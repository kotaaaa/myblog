---
title: Nginx Basic overview
date: "2022-01-20T18:46:37.121Z"
description: Nginx, Reverse proxy
---

# What is Nginx?

Nginx [engine x] is an HTTP and reverse proxy server, a mail proxy server, and a generic TCP/UDP proxy server. Nginx is usually used as reverse proxy to serve web/api server.

[Reference](https://nginx.org/en/)

<img width="700" alt="nginx.png" src="./nginx.png">
<img width="700" alt="logo.png" src="./logo.png">

# Anyway, What is reverse proxy?

[Source](https://www.f5.com/services/resources/glossary/reverse-proxy)

> In networking and web traffic, a proxy is a device or server that acts on behalf of other devices. It sits between two entities and performs a service. Proxies are hardware or software solutions that sit between the client and the server in order to manage requests and sometimes responses.
> Typically, a reverse proxy server sits in front of web servers and forwards client (e.g. web browser) requests to those web servers.
> The requested resources are then returned to the client, appearing as if they originated from the proxy server itself. This provides an additional level of abstraction and control to ensure the smooth flow of network traffic between clients and servers. A reverse proxy also provides the ability to direct requests based on a wide variety of parameters such as user device, location, network conditions, application health and even the time of day.

<img width="700" alt="reverseproxy.png" src="./reverse-proxy.png">

# What for Nginx(reverse proxy) is used?

- Load Balancing (switching upstream host)
- For security reason (ACL IP address blocking)
- Speeding up through caching (return js, css, html files, show busy pages)
- Integration of different apps, frameworks, and platforms (we can switch many kinds of apps by nginx conf)

# Nginx Directive

Two types of directive

1. Variable type
   Ex) proxy_pass, root, …

2. Scope type
   Ex) http, server, events, upstream

<img width="700" alt="1.png" src="./1.png">
<img width="700" alt="2.png" src="./2.png">
<img width="700" alt="3.png" src="./3.png">
<img width="700" alt="4.png" src="./4.png">

# Scope type directive

| Context  | Settings written in context                                                                              |
| -------- | -------------------------------------------------------------------------------------------------------- |
| http     | http server setting Log format, log rolling settings, health check script file                           |
| server   | Sets configuration for virtual server https:sample.com(:81) http:sample.com(:80)                         |
| location | Where to send on the request Ex) location /api/items { proxy_pass http://item-api; }                     |
| events   | Parameters for processing wach requests Numbers of workers accept_mutex_delay(how much it accepts delay) |

# Variable type directive

| Directive        | Explanation                                                                     |     |
| ---------------- | ------------------------------------------------------------------------------- | --- |
| proxy_pass       | Proxied destination server                                                      |
| proxy_set_header | Add the specified field to a request header, then passed to the proxied server. |
| add_header       | Add the specified field to a response header                                    |
| location         | Reverse proxy setting for each URI                                              |
| server_name      | Host name used in virtual server                                                |
| root             | Source file directory to be opened to external                                  |
