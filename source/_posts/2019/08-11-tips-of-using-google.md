---
title: 進階使用 Google 搜尋
date: 2019-08-11 21:49:24
tags:
- google
- tips
- seo
---
## TLDR;
在互聯網開發上，如果要快速的幫助自己搜尋到有用的資料， 大部分的人第一個想到的就是透過瀏覽器，尤其是 Google， 不過簡單的用Google查詢關鍵字誰都會，但是在進階一點的使用方法，可能就不會了， 然而這些進階的方法其實能幫助我們更準確地找到我們想要的資料，以下就是可能會使用到的進階方法的範例。
<!-- more -->
範例一，以現在熱門的區塊鏈跟比特幣的議題，當你用 Google 搜尋的時候，往往文章的內容都是成對出現的，但是，如果我們現在要搜索的文章，要求是標題裡面必須出現區塊練這個名詞，但是必須沒有比特幣這個詞，那要怎麼搜索呢?
> intitle:blockchain -bitcoin


範例二，另外有些更進階的功能，當你做行業研究的時候也是可以用的，以亞馬遜為例子，他公司有很多的業務，而且他很多業務都會取一個二級域名，比如說它的雲服務是叫做aws.amazon.com，但如如果我們想要了解亞馬遜有哪些服務的話，可以查一下亞馬遜有哪些不以www開頭的站點，亞馬遜的主要是www.amazon.com
> site:amazon.com -inurl:www

範例三，亞馬遜有哪些不以.com作結尾的網站
> site:amazon.\* -site:amazon.com

範例四，搜索特斯拉網站上所有的PDF文黨
> site:tesla.com fitetype:pdf


所以如果把搜尋引擎的技巧學起來的話，這樣找到正確的信息的效率就會高很多，
以下是整理過後的 Google 引擎進階搜尋技巧
## Basic Examples
| This Search           | Finds Pages Containing...                                                           |
| --------------------- | ----------------------------------------------------------------------------------- |
| biking Italy          | the words biking and Italy                                                          |
| recycle steel OR iron | information on recycling steel or recycling iron                                    |
| "I have a dream"      | the exact phrase I have a dream                                                     |
| salsa –dance          | the word salsa but _NOT_ the word dance                                               |
| Louis "I" France      | information about Louis the First (I), weeding out other kings of France            |
| castle ~glossary      | glossaries about castles, as well as dictonaries, lists of terms, terminology, etc. |
| fortune-telling       | all forms of the term, whether spelled as a single word, a phrase, or hyphenated    |
| define:imbroglio      | definitions of the word imbroglio from the Web                                      |

## Calculator
| Operators              | Meaning          | Type Into Search Box (& Results)              |
| ---------------------- | ---------------- | --------------------------------------------- |
| + – * /                | basic arithmetic | 12 + 34 - 56 * 7 / 8                          |
| % of                   | percentage of    | 45% of 39                                     |
| ^ or **                | raise to a power | 2^5 or 2**5                                   |
| old units in new units | convert units    | 300 Euros in USD, 130 lbs in kg, or 31 in hex |

### Restrict Search
| Operators                                          | Meaning                                                    | Type Into Search Box (& Results)                                                                             |
| -------------------------------------------------- | ---------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| city1<br>city2                                     | Book flights.                                              | sfo bos <br> (Book flights from San Francisco (SFO) to Boston (BOS).)                                        |
| site:                                              | Search only one website or domain.                         | Halloween site:www.census.gov<br> (Search for information on Halloween gathered by the US Census Bureau.)    |
| [#]..[#]                                           | Search within a range of numbers.                          | Dave Barry pirate 2002..2006 <br>(Search for Dave Barry articles mentioning pirates written in these years.) |
| filetype:<br> (or ext:)                            | Find documents of the specified type.                      | Form 1098-T IRS filetype:pdf <br>(Find the US tax form 1098-T in PDF format.)                                |
| link:                                              | Find linked pages, i.e., show pages that point to the URL. | link:warriorlibrarian.com <br>(Find pages that link to Warrior Librarian's website.)                         |

## Specialized Information Queries
| Operators                 | Meaning                                                            | Type Into Search Box (& Results)                                                                                                                   |
| ------------------------- | ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| book<br> (or books)       | Search full-text of books.                                         | book Ender's Game<br> (Show book-related information.  Note: No colon needed after book.)                                                          |
| define, what is, what are | Show a definition for a word or phrase.                            | define monopsony, what is podcast<br> (Show a definition for the words monopsony and podcast.  Note: No colon after define, what is, or what are.) |
| define:                   | Provide definitions for words, phrases, and acronyms from the Web. | define:kerning<br> (Find definitions for kerning from the Web.)                                                                                    |
| movie:                    | Find reviews and showtimes.                                        | movie: traffic<br> (Search for information about this movie, including reviews, showtimes, etc.)                                                   |
| stocks:                   | Given ticker symbols, show stock information                       | stocks: goog<br> (Find Google's current stock price.)                                                                                              |
| weather                   | Given a location (US zip code or city), show the weather           | weather Seattle WA, weather 81612<br> (Show the current weather and forecast.  Note: No colon after weather.)                                      |

### Alternative Query Types
| Operators          | Meaning                                                | Type Into Search Box (& Results) cache:www.irs.gov                                    |
| ------------------ | ------------------------------------------------------ | ------------------------------------------------------------------------------------- |
| cache:             | Display Google's cached version of a web page.         | (Show Google's cached version of the US Internal Revenue Service home page.)          |
| info:<br> (or id:) | Find info about a page.                                | info:www.theonion.com<br> (Find information about The Onion website.)                 |
| related:           | List web pages that are similar or related to the URL. | related:www.healthfinder.gov<br> (Find websites related to the Healthfinder website.) |

### Restrict Search to Sites where Query Words Appear
| Operators    | Meaning                                                          | Type Into Search Box (& Results)                                                                                                                                                            |
| ------------ | ---------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| allinanchor: | All query words must appear in anchor text of links to the page. | allinanchor:useful parenting sites<br> (Search for pages that are called useful parenting sites by others.)                                                                                 |
| inanchor:    | Terms must appear in anchor text of links to the page.           | restaurants Portland inanchor:kid-friendly<br> (Search for pages on Portland restaurants for which links to the page say they are "kid friendly.")                                          |
| allintext:   | All query words must appear in the text of the page.             | allintext:ingredients cilantro chicken lime (Search for recipes with these three ingredients.)                                                                                              |
| intext:      | The terms must appear in the text of the page.                   | Dan Shugar intext:Powerlight<br> (Find pages mentioning Dan Shugar where his company, Powerlight, is included in the text of the page, i.e., less likely to be from the corporate website.) |
| allintitle:  | All query words must appear in the title of the page.            | allintitle: Google Advanced Operators<br> (Search for pages with titles containing "Google," "Advanced,", and "Operators".)                                                                 |
| intitle:     | The terms must appear in the title of the page.                  | movies comedy intitle:top ten<br> (Search for pages with the words movie and comedy that include top ten in the title of the page.)                                                         |
| allinurl:    | All query words must appear in the URL.                          | allinurl:pez faq<br> (Search for pages containing the words pez & faq in the URL.)                                                                                                          |
| inurl:       | The terms must appear in the URL of the page.                    | pharmaceutical inurl:investor<br> (Search for pages in which the URL contains the word investor.)                                                                                           |

### Restrict Search to Google Groups
| Operators  | Meaning                                                      | Type Into Search Box (& Results)                                                                      |
| ---------- | ------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------- |
| author:    | Find Groups messages from the specified author.              | flying author:Hamish author:Reid<br> (Search for Hamish Reid's articles on flying.)                   |
| group:     | Find Groups messages from the specified newsgroup.           | ivan doig group:rec.arts.books<br> (Search for postings about Ivan Doig in the group rec.arts.books.) |
| insubject: | Find Groups messages containing crazy quilts in the subject. | insubject:"crazy quilts"<br> (Find articles containing crazy quilts in the subject line.)             |

### Restrict Search to Google News
| Operators | Meaning                                                            | Type Into Search Box (& Results)                                                         |
| --------- | ------------------------------------------------------------------ | ---------------------------------------------------------------------------------------- |
| location: | Find News articles from sources located in the specified location. | queen location:uk<br> (Find British news articles on the Queen.)                         |
| source:   | Find News articles from specified sources.                         | peace source:ha\_aretz<br> (Show articles on peace from the Israeli newspaper Ha'aretz.) |
