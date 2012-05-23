---
layout: post
title: "Node.js supported encodings"
date: 2012-04-24 09:21
comments: true
categories: 
published: false
---
Ever wondered what encodings node.js supports when reading files using the [fs api](http://nodejs.org/api/fs.html)?
The documentation is quite sparse regarding that topic. Quite sparse is quite true, I could not find anything in the documentation telling me what encodings are supported by the node.js fs api.
As code does not lie taking a look at the code will demystify the encodings. The information is hidden in the Buffer's [toString function](https://github.com/joyent/node/blob/master/lib/buffer.js#L157).

Encodings supported by node.js fs api/Buffer are:

* hex
* utf-8/utf8
* ascii
* binary
* base64
* ucs-2/ucs2

If you wonder what the 'ucs-2' encoding here's the definition given by [wikipedia](http://en.wikipedia.org/wiki/UTF-16)

> The older UCS-2 (2-byte Universal Character Set) is a similar character encoding that was superseded by UTF-16 in version 2.0 of the Unicode standard in July 1996. It produces a fixed-length format by simply using the code point as the 16-bit code unit and produces exactly the same result as UTF-16 for 96.9% of all the code points in the range 0-0xFFFF, including all characters that had been assigned a value at that time.
