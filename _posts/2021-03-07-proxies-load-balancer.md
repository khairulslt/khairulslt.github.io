---
title: On Proxies & Load Balancers
date: 2021-03-07 00:27:31
---

Benefits of Proxies (Proxies protect clients)
1) proxies act as a shield, as a firewall that keeps all the bad stuff from the internet out of the intranet
2) better management, multiple clients can talk to the same proxy. Proxy helps manage all the requests at one place and then pass it on to the outside world
3) security, prevents phishing attacks
4) performance via caching, say multiple clients are requesting for a static page from a website... once this particular request has been fetched from the server. you can store that static content on the proxy. Rather than going back through the internet and onto that website again, you can just fetch the static content from the proxy, saving bandwidth and improving performance
5) encryption/decryption, when your client makes a request to a website (web server) through a proxy, the proxy hides your IP whether by changing it or decrypting it so the web server doesnt know where you are in the world. It can also encrypt your data so it is unreadable in transit. It also can block access to certain web pages based on IP address.

Benefits of Reverse Proxies (Reverse Proxies protect servers)


Reverse Proxy Vs Load balancer
Reverse proxy can be a load balancer as well
but load balancer cannot be a reverse proxy