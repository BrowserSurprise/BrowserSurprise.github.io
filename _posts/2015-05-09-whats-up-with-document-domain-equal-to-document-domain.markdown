---
layout:     post
title:      "Communicating across sub-domains/ports in iframes"
subtitle:   "Why setting document.domain = document.domain make it work?"
date:       2015-05-09 04:05:00
author:     "Amit Ambardekar"
header-img: "img/post-bg-06.jpg"
---

<p>This port is going to be short and I won't be contributing much bbut this is the quote.</p>

<blockquote cite="http://stackoverflow.com/questions/1481251/what-does-document-domain-document-domain-do">
When trying to do cross-subdomain/port comet, the iframe needs to have the same document.domain value as the parent frame. Unfortunately, the browser stores the domain name AND port internally for the original document.domain value. But the getter and setter in javascript knows nothing about the port. So the problem is this: if the top frame document.domain is ('example.com', 80), and the bottom frame is ('comet.example.com', 80), how do you get the bottom frame to be ('example.com', 80) as well?
<br />
You can't, as changing the hostname portion will necessarily cause the port to be set to null, so the best you can do is ('example.com', null) in the bottom frame. So the top frame also needs to be set to that value, and setting document.domain=document.domain does just that. It changes the internal representation in the browser from ('example.com', 80) to ('example.com', null) and then everything matches up and cross-port/subdomain frame communication works.
</blockquote>

<p>
  Source: <a href="http://stackoverflow.com/questions/1481251/what-does-document-domain-document-domain-do">http://stackoverflow.com/questions/1481251/what-does-document-domain-document-domain-do</a>
</p>