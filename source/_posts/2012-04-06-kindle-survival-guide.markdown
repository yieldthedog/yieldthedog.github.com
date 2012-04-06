---
layout: post
title: "Kindle Survival Guide"
date: 2012-04-06 10:47
comments: true
categories: kindle, tools, reading
published: true
---

I own a Kindle for about 1 year and a half and I must say it has served me quite well. In this time I have read about 20-30 books - not all from cover to cover, but some twice-, have read literally 100th of articles, used it for browsing the web, sent a tweet and used it as my main reading device.

So what is it, that makes an ebook reader superior to a normal book?

<!-- more -->
{% img full-width https://lh4.googleusercontent.com/-MnoWQED2tp8/T3IFGz0VXOI/AAAAAAAAALg/WJFwBQAqk8U/s861/IMG_9883.JPG %}

###Advantages

- ***Size and weight*** is a main factor. I can carry it with me all the time in my back bag and I won't even notice it's weight
- ***Readiness of books***: When you buy a book over the internet, it takes a while until you have it in your hands and are able to start reading. With ebooks it's different. Buy it, download it, read it. Dead simple and crazy fast.
- ***Your library at your disposal***: With 3 gigs of memory, I don't care, how many books I carry with me. If I need to read a passage, that I have marked or dog eared in the past, I pull out the kindle and read it.

###Disadvantages

- ***Screen size***: If the width of the screen was a bit larger - about 1cm -, a lot of stuff would be easier to read.
- ***Reading code***: Reading code was especially in the beginning kind of weird/awkward. The small width often breaks lines, what makes it very hard to read it properly. One ebook I own tried to circumvent this fact, by putting all code in images, which you can zoom in. Still not a great experience. But it seems that authors and publishers acknowledge this fact more recently, and try to avoid breaking lines on a Kindle.
 

## Buying books

I don't like to buy books from Amazon. Even though they made their process very easy, they lack one important thing. I do not own the books I buy. They are DRMed and cannot be read or ported to another device unless you jailbreak your device, what I am not willing to do. This is really bad, because it deadlocks me in a situation, in which I will only buy Kindles for my whole life.

So what to do with this situation? Download books from rapidshare, megaupload, ....? No! Why not, you ask. Because there are useful alternatives that are at least as good as amazon, with which you support the author and the publisher.

As I'm a coder, I'm mainly interested in technical books. One publisher of technical books, that stands out is ***[PragProg](http://pragprog.com)*** - not because I emphasize their text, but because they offer a quite superior service. Here are the main features:

- All ebooks are DRM free available in various formats
- You can configure your PragProg account to automatically send your purchases and future updates to your free kindle email address. This can sometimes get annoying, when you have purchased a book in beta, which receives updates quite often.
- PragProg can automatically send your ebooks to your Dropbox
- They publish a free magazine

Some of the PragProg titles lack chapter markers, which is quite annoying, but all in all they offer a great service. Kudos to Dave and Andy!

Next one is [O'Reilly](http://shop.oreilly.com). Just like PragProg they offer their whole library in various formats.

[Manning](http://manning.com) had great problems converting their pbooks to ebooks. For a long time they only offered PDFs, that are not very comfortable to read on a Kindle (don't even try), and are now slowly reducing the distance to the others.

[Apress](http://apress.com) - I must admit that I don't buy much books from Apress for no special reason. Probably because I'm not subscribed to their newsletter.

{% pullquote %}
All of these publishers have one advantage over Amazon in common. {"They offer discounts and deals."} Subscribe to their newsletter, visit their home page and you will be amazed, how much you can save. I have read many books, just because of discounts and I have stopped reading books, because it just did not hurt to put them away, when they did not cost that much. Another advantage over Amazon is, that you can purchase books that are no published yet - PragProg calls them [beta](http://pragprog.com/categories/new), O'Reilly calls them [rough cuts](http://oreily.com/roughcuts). This is kind of nice when the book is dealing with a fast evolving topic, where the book will be out of date as soon as it is published. On the other hand those books are not published for a certain reason: They are not finished. At PragProg you can even follow the progress of a book that's currently written (Click on progress of the [Practical Vim](http://pragprog.com/book/dnvim/practical-vim) book and take a look at this great [RaphaelJS](http://raphaeljs.com) chart).
{% endpullquote %}

## Tools that make your life easier

###Instapaper
[Instapaper](http://instapaper.com) is one of the best companions of your kindle. It provides a _read later_ bookmarklet, that saves an article to a list. Later you can either export the list manually or you can let Instapaper automatically send an email to your free kindle account, when a certain amount of new articles is reached. Nowadays I even use it to send out [tweets](https://twitter.com/#!thomaspeklak/status/183086027668336640) for great articles and save them to my [Evernote](http://evernote.com) article backlog.

###Calibre
[Calibre](http://calibre-ebook.com) is a great tool to manage your ebooks, send them to your device via USB or email. What I especially like is the ability to convert formats. They offer a great support. I once filed a feature request and on the next day it was closed. Way to go!

###You@free.kindle.com
And last but not least don't forget that you own a user@free.kindle.com address, which you can use (as mentioned above) to send books to it and have Amazon automatically deliver them to your device the next time you connect. Works great with PragProg and Instapaper.

### Pandoc
Pandoc can be useful if you have an exotic format such as markdown that you want to convert to epub and via Calibre or [KindleGen](http://www.amazon.com/gp/feature.html?ie=UTF8&docId=1000234621) to mobi. A direct conversion to mobi is not supported. I used Pandoc to produce my epub/mobi versions of the excellent [The Little Redis Book](http://openmymind.net/2012/1/23/The-Little-Redis-Book/) and [The Little MongoDB Book](http://openmymind.net/2011/3/28/The-Little-MongoDB-Book/) books. Pandoc is not needed any more for the two "Little Books" since they are available as epub.

## Bugs
Once in a while I was plagued with the following bug. It manifests itself in the fact, that the Kindle leaks battery as hell and instead of lasting one to two months, the charge is wasted after a week. This can happen, when the internal search indexer fails to index a document and tries again and again. If you experience the symptoms, simply go to your home screen, enter random characters and hit enter to start a search. If the indexer hangs, you will see that a document being processed.

To solve this, delete the document from your Kindle and upload it again. In my case that worked 100%.


##Conclusion

The Kindle and I had a kind of rough start, because the ecosystem was not that great one and a half year ago. But it served me well. In the meantime publishers have noticed, that they do not have to solely rely on Amazon or another big company. The tools around ebook readers have grown and matured. If my kindle would break tomorrow, I would not hesitate to replace it with another kindle or ebook reader. The advantages over a pbook are too big.

