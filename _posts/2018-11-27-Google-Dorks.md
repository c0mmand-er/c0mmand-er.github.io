---
layout: post
title: MAXIMIZE SEARCH RESULTS.
description: "GOOGLE DORKS"
modified: 2018-11-27
tags: [search, hacking]
image:
  feature: dorks.png
---

Hello everyone, in this article we are going to discuss how you can maximize your search results using google dorks. Google dorks is mainly referred to pull information from Google using advanced search terms that help users to search the index of a specific website, specific file type and some interesting information. Most of use of google dorks is by hackers to gather sensitive information about specific website or someone. Google Dorks can uncover some incredible information such as email addresses and lists, login credentials, sensitive files, website vulnerabilities, and even financial information (e.g. payment card data). However, you still able to use google dorks for any kind of research you are making.

### HOW IT WORKS

Dorking can be done using various search engines such as Bing, Yahoo, and DuckDuckGo, not just Google. search engines are programmed to accept more advanced operators that refine those search terms. An operator is a phrase that has particular meaning for the search engine. Operators include things like “inurl”, “intext”, “site”, and so on. Each operator is followed by a colon which is followed by the relevant term or terms.

These operators allow a search to target more specific information, such as certain strings of text in the body of a page in website or files hosted on a given url. Also, a google dork can locate hidden login pages. error messages that give away too much information and files that a website administrator might not realize are publicly accessible.

### PRACTICAL

A simple example of a dork that does rely on an operator might be:
![](/images/google1.png)
As you can see, we searched about a “login” word that exists in specific url (in this example nu.edu.eg). Google dorks returned login pages that you may find them interesting.

Let’s Chain some Operators :)
![](/images/google2.png)
![](/images/google3.png)
As you can see, there is a sensitive information discloser that attacker can use.

Let’s try to login :)
![](/images/google4.png)
Here we go. We gained a full access control for the school admin :)

### COMMON GOOGLE DORKS OPERATORS

<b> site </b> – limits the scope of a query to a single website.

<b> intitle </b> – this allows to search for pages with specific text in their HTML title. So intitle: “login page” will help you scour the web for login pages.

<b> allintitle </b> – similar to the previous operator, but only returns results for pages that meet all of the keyword criteria.

<b> inurl </b> – allows to search for pages based on the text contained in the URL (i.e. “login.php”).

<b> allinurl </b> – similar to the previous operator, but only returns matches for URLs that meet all the matching criteria.

<b> filetype </b> – helps narrow down search results to specific types of files such as PHP, PDF, or TXT file types.

<b> ext </b> – very similar to filetype, but this looks for files based on their file extension.

<b> intext </b> – this operator searches the entire content of a given page for keywords supplied by the hacker.

<b> allintext </b> – similar to the previous operator, but requires a page to match all of the given keywords.
