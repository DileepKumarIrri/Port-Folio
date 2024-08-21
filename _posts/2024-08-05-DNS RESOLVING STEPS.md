---
title: "DNS RESOLVING STEPS"
date: 2024-08-05
categories:
---

## DNS RESOLVING STEPS

<!-- ### Advice -->

### 1. Entering the Domain Name

When you enter `www.gvpce.ac.in` into your web browser, the browser needs to resolve this domain name into an IP address to establish a connection.

### 2. Checking the Browser Cache

The browser first checks its cache to see if it has recently resolved this domain name and stored the corresponding IP address. If it finds an entry, it will use the cached IP address, skipping further steps.

### 3. Checking the Operating System Cache

If the browser cache doesn't have the information, the browser queries the operating system's DNS cache. Modern operating systems cache DNS lookups to improve performance.

### 4. Querying the Local DNS Resolver

If the IP address is not found in the OS cache, the query is sent to the local DNS resolver. This is typically provided by your Internet Service Provider (ISP) or a third-party DNS resolver like Google DNS (8.8.8.8) or Cloudflare (1.1.1.1).

### 5. Checking the Resolver Cache

The local DNS resolver checks its cache to see if it has a recent copy of the IP address for `www.gvpce.ac.in`.

### 6. Iterative Querying

If the local DNS resolver does not have the information cached, it starts an iterative querying process to resolve the domain name:

### a. Root Name Server

The local resolver first queries a root name server. The root name servers are the highest level in the DNS hierarchy. The root server does not know the exact IP address for `www.gvpce.ac.in`, but it knows where to find authoritative name servers for top-level domains (TLDs).

### b. TLD Name Server

The root server responds with the IP address of the TLD name server responsible for `.in` domains. The local resolver then queries this TLD name server.

### c. Authoritative Name Server for the Domain

The TLD name server responds with the IP address of the authoritative name server for `gvpce.ac.in`. The local resolver now queries this authoritative name server.

### 7. Querying the Authoritative Name Server

The authoritative name server for `gvpce.ac.in` holds the DNS records for this domain. It responds to the local resolver with the IP address associated with `www.gvpce.ac.in`.

### 8. Returning the IP Address

The local resolver returns the IP address to the original requesting client (your browser).

### 9. Connecting to the IP Address

The browser now has the IP address and can establish a connection to the web server at that IP address to retrieve the web page content.

### Example Walkthrough

Let's apply these steps to `www.gvpce.ac.in`:

1. **Enter `www.gvpce.ac.in` in Browser**:
    - The browser starts the DNS resolution process.
2. **Browser Cache Check**:
    - Browser checks if it has `www.gvpce.ac.in` cached. If not, proceed.
3. **OS Cache Check**:
    - OS cache is checked for `www.gvpce.ac.in`. If not found, proceed.
4. **Local DNS Resolver Query**:
    - Query is sent to the local DNS resolver.
5. **Local Resolver Cache Check**:
    - Local resolver checks its cache. If not found, proceed.
6. **Iterative Querying**:
a. **Root Name Server Query**:
    - Local resolver queries a root name server, which directs it to the `.in` TLD name server.
    b. **TLD Name Server Query**:
    - TLD name server for `.in` responds with the authoritative name server for `gvpce.ac.in`.
    c. **Authoritative Name Server Query**:
    - Authoritative name server for `gvpce.ac.in` responds with the IP address for `www.gvpce.ac.in`.
7. **Local Resolver Response**:
    - Local resolver returns the IP address to the browser.
8. **Browser Connects**:
    - Browser uses the IP address to connect to the web server and load the webpage.

### DNS Records Involved

During this process, several DNS records may be involved:

- **A Record**: Maps a domain name to its corresponding IPv4 address.
- **AAAA Record**: Maps a domain name to its corresponding IPv6 address.
- **NS Record**: Indicates the authoritative name servers for a domain.
- **CNAME Record**: Maps an alias name to a true or canonical domain name.
