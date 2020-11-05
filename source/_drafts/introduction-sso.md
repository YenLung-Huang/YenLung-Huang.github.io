---
title: introduction-sso
tags:
---
浅谈SAML, OAuth, OpenID和SSO, JWT和Session
前言
通常为了弄清楚一个概念，我们需要掌握十个概念。在判断 JWT(JsonWebToken) 是否能代替 session 管理之前，我们要了解什么是 token，以及 access token 和 refresh token 的区别。

了解什么是 OAuth，什么是 SSO，SSO 下不同策略 OAuth 和 SAML 的不同，以及 OAuth 与 OpenID 的不同，更重要的是区分 authorisation 和 authentication。

最后我们引出 JSON WEB TOKEN，聊聊 JWT 在 Session 管理方面的优势和劣势，同时尝试解决这些劣势，看看成本和代价有多少。


正文
本文关于 OAuth 授权 和 API 调用实例都来自 Google API。

关于Token
Token 即使是在计算机领域中也有不同的定义，这里我们说的 token，是指 访问资源 的凭据。例如当你调用 Google API 时，需要带上有效 token 来表明你请求的 合法性。这个 Token 是 Google 给你的，这代表 Google 给你的 授权 使得你有能力访问 API 背后的 资源。

请求 API 时携带 token 的方式也有很多种，通过 HTTP Header 或者 url 参数或者 google 提供的类库都可以：

HTTP Header
GET /drive/v2/files HTTP/1.1

Authorization: Bearer <token>
Host: www.googleapis.com/
URL参数
GET https://www.googleapis.com/drive/v2/files?token=<token>
Python函数库
from googleapiclient.discovery import build
drive = build('drive', 'v2', credentials=credentials)
更具体的说，上面用于调用 API 的 token，我们称为细分为 access token。通常 access token 是有 有效期限 的，如果 过期 就需要 重新获取。那么如何重新获取？先看看第一次获取 token 的流程是怎样的:

首先需要向 Google API 注册一个应用程序，注册完毕之后就会拿到 认证信息（credentials）包括 ID 和 secret。不是所有的程序类型都有 secret。

接下来就要向 Google 请求 access token。这里先忽略一些细节，例如请求参数（当然需要上面申请到的 secret）。重要的是，如果你想访问的是 用户资源，这里就会提醒用户进行 授权。

如果 用户授权 完毕。Google 就会返回 access token。又或者是返回 授权代码（authorization code），再通过代码取得 access token。

token 获取到之后，就能够带上 token 访问 API 了。

流程如下图所示：


注意：在第三步通过 authorization code 兑换 access token 的过程中，Google 并不会仅仅返回 access token，还会返回额外的信息，这其中和之后更新相关的就是 refresh token。

一旦 access token 过期，你就可以通过 refresh token 再次请求 access token。

以上只是大致的流程，并且故意省略了一些额外的概念。比如更新 access token 当然也可以不需要 refresh token，这要根据你的 请求方式 和访问的 资源类型 而定。

这里又会引起另外的两个问题：

如果 refesh token 也过期了怎么办？这时就需要用户 重新登陆授权。

为什么要区分 refresh token 和 access token？如果合并成一个 token 然后把 过期时间 调整的 更长，并且每次 失效 之后用户 重新登陆授权 就好了？这个问题会和后面谈的相关概念有关，后面会给予解释说明。

OAuth 2.0
从获取 token 到使用 token 访问接口。这其实是标准的 OAuth2.0 机制下访问 API 的流程。这里介绍一下 OAuth 里外相关的概念，更深入的理解 token 的作用。

SSO (Single sign-on)
通常公司内部会有非常多的平台供大家使用，比如人力资源，代码管理，日志监控，预算申请等等。如果每一个平台都实现自己的用户体系的话无疑是巨大的浪费，所以公司内部会有一套 公用的用户体系，用户只要登陆之后，就能够 访问所有的系统。这就是 单点登录。

SSO 是一类 解决方案 的统称，而在具体的实施方面，我们有两种策略可供选择：

SAML 2.0

OAuth 2.0

接下来我们区别这 两种授权方式 有什么不同。但是在描述 不同的策略 之前，我们先叙述几个 共有的特性，并且相当重要的概念。

Authentication VS Authorisation
Authentication: 身份鉴别，以下简称 认证；

Authorisation: 资源访问 授权。

认证 的作用在于 认可 你能够访问系统，用于 鉴别访问者 是否是 合法用户；而 授权 用于决定你有访问 哪些资源的权限。

大多数人不会区分这两者的区别，因为站在用户的立场上。而作为系统的设计者来说，这两者是有差别的，这是不同的两个工作职责。我们可以只需要 认证功能，而不需要 授权功能，甚至不需要自己实现 认证功能。而借助 Google 的认证系统，即用户可以用 Google 的账号进行登陆。

Authorization Server/Identity Provider(IdP)
把负责 认证的服务 称为 AuthorizationServer 或者 IdentityProvider，以下简称 IDP。

Service Provider(SP)/Resource Server
把负责 提供资源（API 调用）的服务称为 ResourceServer 或者 ServiceProvider，以下简称 SP。

SAML 2.0
下图是 SAML2.0 的流程图，看图说话：


还 未登陆 的用户 打开浏览器 访问你的网站（SP），网站 提供服务 但是并 不负责用户认证。

于是 SP 向 IDP 发送了一个 SAML 认证请求，同时 SP 将 用户浏览器 重定向到 IDP。

IDP 在验证完来自 SP 的 请求无误 之后，在浏览器中呈现 登陆表单 让用户填写 用户名 和 密码 进行登陆。

一旦用户登陆成功， IDP 会生成一个包含 用户信息（用户名 或者 密码）的 SAML token（SAML token 又称为 SAML Assertion，本质上是 XML 节点）。IDP 向 SP 返回 token，并且将 用户重定向 到 SP (token 的返回是在 重定向步骤 中实现的，下面会详细说明)。

SP 对拿到的 token 进行验证，并从中解析出 用户信息，例如 用户是谁 以及 用户的权限 有哪些。此时就能够根据这些信息允许用户访问我们网站的内容。

当用户在 IDP 登陆成功之后，IDP 需要将用户 再次重定向 到 SP 站点，这一步通常有两个办法：

HTTP 重定向：这并不推荐，因为 重定向 的 URL 长度 有限制，无法携带更长的信息，比如 SAML Token。

HTTP POST 请求：这个是更常规的做法，当用户登陆完毕之后渲染出一个表单，用户点击后向 SP 提交 POST 请求。又或者可以使用 JavaScript 向 SP 发出一个 POST 请求。

如果你的应用是基于 Web，那么以上的方案没有任何问题。但如果你开发的是一个 iOS 或者 Android 的手机应用，那么问题就来了：

用户在 iPhone 上打开应用，此时用户需要通过 IDP 进行认证。

应用跳转至 Safari 浏览器，在登陆认证完毕之后，需要通过 HTTP POST 的形式将 token 返回至 手机应用。

虽然 POST 的 url 可以 拉起应用，但是 手机应用 无法解析 POST 的内容，我们也就无法读取 SAML Token。

当然还是有办法的，比如在 IDP 授权阶段 不跳转至系统的 Safari 浏览器，在 内嵌 的 Webview 中解决，在想方设法从 Webview 中提取 token，或者利用 代理服务器。

无论如何，SAML 2.0 并 不适用 于当下 跨平台 的场景，这也许与它产生的年代也有关系，它诞生于 2005 年，在那个时刻 HTTP POST 确实是最好的选择方案。

OAuth 2.0
我们先简单了解 SSO 下的 OAuth2.0 的流程。


用户通过 客户端（可以是 浏览器 也可以是 手机应用）想要访问 SP 上的资源，但是 SP 告诉用户需要进行 认证，将用户 重定向 至 IDP。

IDP 向 用户 询问 SP 是否可以访问 用户信息。如果用户同意，IDP 向 客户端 返回 authorization code。

客户端拿到 authorization code 向 IDP 交换 access token，并拿着 access token 向 SP 请求资源。

SP 接受到请求之后，拿着附带的 token 向 IDP 验证 用户的身份。确认身份无误后，SP 向 客户端 发放相关资源。

那么 OAuth 是如何避免 SAML 流程下 无法解析 POST 内容的信息的呢？

一方面是用户从 IDP 返回 客户端 的方式，也是通过 URL 重定向，这里的 URL 允许 自定义 schema，所以即使在 手机 上也能 拉起应用；

另一方面因为 IDP 向 客户端 传递的是 authorization code，而不是 XML 信息，所以 code 可以很轻易的附着在 重定向 URL 上进行传递。

但以上的 SSO 流程体现不出 OAuth 的本意。OAuth 的本意是 一个应用 允许 另一个应用 在 用户授权 的情况下 访问自己的数据。

OAuth 的设计本意更倾向于 授权而非认证（当然授权用户信息就间接实现了认证），虽然 Google 的 OAuth 2.0 API 同时支持 授权 和 认证。所以你在使用 Facebook 或者 Gmail 账号登陆第三方站点时，会出现 授权对话框，告诉你 第三方站点 可以访问你的哪些信息，需要征得你的同意。


在上面 SSO 的 OAuth 流程中涉及三方角色: SP, IDP 以及 Client。但在实际工作中 Client 可以是不存在的，例如你编写了一个 后端程序 定时的通过 Google API 从 Youtube 拉取最新的节目数据，那么你的 后端程序 需要得到 Youtube 的 OAuth 授权 即可。

OAuth VS OpenId
如果你有留心的话，你会在某些站点看到允许以 OpenID 的方式登陆，其实也就是以 Facebook 账号或者 Google 账号登陆站点：


OpenID 和 OAuth 很像。但本质上来说它们是截然不同的两个东西：

OpenID: 只用于 身份认证（Authentication），允许你以 同一个账户 在 多个网站登陆。它仅仅是为你的 合法身份 背书，当你以 Facebook 账号登陆某个站点之后，该站点 无权访问 你的在 Facebook 上的 数据。

OAuth: 用于 授权（Authorisation），允许 被授权方 访问 授权方 的 用户数据。

Refresh Token
现在可以回答上面的问题了，为什么我们需要 refresh token？

这样的处理是为了 职责的分离：

refresh token: 负责 身份认证；

access token: 负责 请求资源。

虽然 refresh token 和 access token 都由 IDP 发出，但是 access token 还要和 SP 进行 数据交换，如果 公用的话 这样就会有 身份泄露 的可能。并且 IDP 和 SP 可能是 完全不同 的 服务提供 的。而在上文，我们之所以没有这样的顾虑是因为 IDP 和 SP 都是 Google。

JWT
初步认识
本质上来说 JWT 也是 token，正如我们在上文提到的，它是 访问资源 的 凭证。

Google 的一些 API 诸如 Prediction API 或者 Google Cloud Storage，是不需要 访问 用户的 个人数据 的。因而不需要经过 用户的授权 这一步骤，应用程序可以直接访问。就像上面 OAuth 中没有 Client 没有参与的流程类似。这就要借助 JWT 完成访问了, 具体流程如下：


首先需要在 Google API 上创建一个服务账号（service account）。

获取 服务账号 的 认证信息（credential），包括 邮箱地址，client ID，以及一对 公钥/私钥。

使用 Client ID 和 私钥 创一个 签名 的 JWT，然后将这个 JWT 发送给 Google 交换 access token。

Google 返回 access token。

程序通过 access token 访问 API。

甚至你可以不需要向 Google 索要 access token，而是携带 JWT 作为 HTTP header 里的 bearer token 直接访问 API 也是可以的。这才是 JWT 的最大魅力。

理性认识
JWT 顾名思义，它是 JSON 结构的 token，由三部分组成：

header

payload

signature

header
header 用于描述 元信息，例如产生 signature 的算法：

{
    "typ": "JWT",
    "alg": "HS256"
}
其中 alg 关键字就指定了使用哪一种 哈希算法 来创建 signature。

payload
payload 用于携带你希望 向服务端传递 的信息。你既可以往里添加 官方字段，例如：iss(Issuer), sub(Subject), exp(Expirationtime)，也可以塞入 自定义的字段，比如 userId:

{
    "userId": "b08f86af-35da-48f2-8fab-cef3904660bd"
}
signature
signature 译为 签名，创建签名要分以下几个步骤：

从 接口服务端 拿到 密钥，假设为 secret。

对 header 进行 base64 编码，假设结果为 headerStr。

将 payload 进行 base64 编码，假设结果为 payloadStr。

将 headerStr 和 payloadStr 用 . 字符 拼装起来成为字符 data。

以 data 和 secret 作为参数，使用 哈希算法 计算出 签名。

如果上述描述还不直观，用 伪代码 表示就是：

// Signature algorithm
data = base64urlEncode( header ) + “.” + base64urlEncode( payload )
signature = Hash( data, secret );
假设我们的原始 JSON 结构是这样的：

// Header
{
    "typ": "JWT",
    "alg": "HS256"
}

// Payload
{
    "userId": "b08f86af-35da-48f2-8fab-cef3904660bd"
}
如果 密钥 是字符串 secret 的话，那么最终 JWT 的结果就是这样的：

eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VySWQiOiJiMDhmODZhZi0zNWRhLTQ4ZjItOGZhYi1jZWYzOTA0NjYwYmQifQ.-xN_h82PHVTCMA9vdoHrcZxH-x5mb11y1537t3rGzcM
可以在 jwt.io 上 验证 这个结果。

JWT究竟带来了什么
确保数据完整性
JWT 的目的不是为了 隐藏 或者 保密数据，而是为了确保 数据 确实来自被 授权的人 创建的，以防止 中途篡改。

回想一下，当你拿到 JWT 时候，你完全可以在没有 secret 的情况下解码出 header 和 payload，因为 header 和 payload 只是经过了 base64 编码（encode）而已，编码的目的在于 利于数据结构的传输。

虽然创建 signature 的过程近似于 加密 (encrypt)，但本质其实是一种 签名 (sign) 的行为，用于保证 数据的完整性，实际上也并且并 没有加密任何数据。

用于接口调用
接下来在 API 调用中就可以附上 JWT（通常是在 HTTP Header 中）。又因为 SP 会与程序 共享 一个 secret，所以 程序 可以通过 header 提供的相同的 hash 算法来 验证签名 是否正确，从而判断应用是否有权力调用 API。

有状态的对话Session
因为 HTTP 是 无状态 的，所以 客户端 和 服务端 需要解决的问题是，如何让它们之间的对话变得有状态。例如只有是 登陆状态 的 用户 才有权限调用某些接口，那么在 用户登陆 之后，需要记住该用户是 已经登陆 的状态。常见的方法是使用 session 机制。

常见的 session 模型是这样工作的：


用户在浏览器 登陆 之后，服务端为用户生成 唯一 的 session id，存储在 服务端 的 存储服务（例如 MySQL, Redis）中。

该 session id 也同时 返回给浏览器，以 SESSION_ID 为 KEY 存储在浏览器的 cookie 中。

如果用户再次访问该网站，cookie 里的 SESSION_ID 会随着 请求 一同发往 服务端。

服务端通过判断 SESSION_ID 是否已经在 Redis 中判断用户是否处于 登陆状态。

相信你已经察觉了，理论上来说，JWT 机制可以取代 session 机制。用户不需要提前进行登陆，后端也不需要 Redis 记录用户的登陆信息。客户端的本地保存一份合法的 JWT，当用户需要调用接口时，附带上该合法的 JWT，每一次调用接口，后端都使用请求中附带的 JWT 做一次 合法性的验证。这样也间接达到了 认证用户 的目的。

然而 JWT 真的能取代 session 机制吗？这么做有哪些好处和坏处？这些问题将留在下一篇再讨论。
references:

[https://juejin.im/post/6844903634094784520](https://juejin.im/post/6844903634094784520)
