---
title: On Proxies & Load Balancers
date: 2021-03-07 00:27:31
---

<h2>Proxy (Protects Clients)</h2>
<ol>
<li>
    Proxies act as a shield, as a firewall that keeps all the bad stuff from the internet out of the intranet
</li>
<li>
    Better management, multiple clients can talk to the same proxy. Proxy helps manage all the requests at one place and then pass it on to the outside world
</li>
<li>
    Security, prevents phishing attacks
</li>
<li>
    Performance via caching, say multiple clients are requesting for a static page from a website... once this particular request has been fetched from the server. you can store that static content on the proxy. Rather than going back through the internet and onto that website again, you can just fetch the static content from the proxy, saving bandwidth and improving performance
</li>
<li>
    Encryption/decryption, when your client makes a request to a website (web server) through a proxy, the proxy hides your IP whether by changing it or decrypting it so the web server doesnt know where you are in the world. It can also encrypt your data so it is unreadable in transit. It also can block access to certain web pages based on IP address.
</li>
</ol>

<h2>Reverse Proxy (Protects Servers)</h2> 
<p>
    Whereas deploying a load balancer makes sense only when you have multiple servers, it often makes sense to deploy a reverse proxy even with just one web server or application server. You can think of the reverse proxy as a website’s “public face.” Its address is the one advertised for the website, and it sits at the edge of the site’s network to accept requests from web browsers and mobile apps for the content hosted at the website. The benefits are two-fold:
</p>
<ul>
<li>
    Increased security – No information about your backend servers is visible outside your internal network, so malicious clients cannot access them directly to exploit any vulnerabilities. Many reverse proxy servers include features that help protect backend servers from <a href="https://nginx.com/resources/glossary/what-is-distributed-denial-of-service/" target="_blank">distributed denial-of-service</a> (DDoS) attacks, for example by rejecting traffic from particular client IP addresses (blacklisting), or limiting the number of connections accepted from each client.
</li>
<li>
    Increased scalability and flexibility – Because clients see only the reverse proxy’s IP address, you are free to change the configuration of your backend infrastructure. This is particularly useful In a load-balanced environment, where you can scale the number of servers up and down to match fluctuations in traffic volume.
</li>
</ul>
<p>
    Another reason to deploy a reverse proxy is for <a href="https://nginx.com/resources/glossary/web-acceleration/" target="_blank">web acceleration</a> – reducing the time it takes to generate a response and return it to the client. Techniques for web acceleration include the following:
</p>
<ul>
<li>
    Compression
    – Compressing server responses before returning them to the client (for instance, with "<code>gzip</code>") reduces the amount of bandwidth they require, which speeds their transit over the network.
</li>
<li>
    <a href="https://www.nginx.com/resources/admin-guide/nginx-ssl-termination/" target="_blank">SSL termination</a>
    – Encrypting the traffic between clients and servers protects it as it crosses a public network like the Internet. But decryption and encryption can be computationally expensive. By decrypting incoming requests and encrypting server responses, the reverse proxy frees up resources on backend servers which they can then devote to their main purpose, serving content.
</li>
<li>
    <a href="https://www.nginx.com/products/content-caching-nginx-plus/" target="_blank">Caching</a>
    – Before returning the backend server’s response to the client, the reverse proxy stores a copy of it locally. When the client (or any client) makes the same request, the reverse proxy can provide the response itself from the cache instead of forwarding the request to the backend server. This both decreases response time to the client and reduces the load on the backend server.
</li>
</ul>
<p> Taken from the <a href="https://www.nginx.com/resources/glossary/reverse-proxy-vs-load-balancer/" target="_blank">Nginx</a> website</p>