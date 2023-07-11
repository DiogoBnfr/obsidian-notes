# Web Resource Addressing and Access
## Domain Name System and its Processes
The Domain Name System (DNS) is the system responsible for addressing and recognizing web pages, as well as locating them on their servers and bridging the gap between the data of the web page and the requests made by the browser.

All this process is done through the IP system, which is responsible for creating unique addresses for web pages. DNS servers eliminate the need for humans to memorize IP addresses such as 192.168.1.1 (in IPv4) or more complex alphanumeric IP addresses like 2400:cb00:2048:1::c629:d7a2 (in IPv6) by using their translation methods to more human-friendly addresses.

**Example:** Google.com

### DNS Recursive Resolver
The DNS recursive resolver is the computer responsible for responding to a client's request and is dedicated to tracking the DNS record of the entered address. This is done through a series of requests until it reaches the authoritative DNS nameserver for the requested record (or times out or returns an error if no record is found). DNS recursive resolvers do not always need to make multiple requests to track the necessary records to respond to a client; caching is a data persistence process that helps shorten the path of necessary requests by providing the requested resource record earlier in the DNS lookup.

![https://cf-assets.www.cloudflare.com/slt3lc6tev37/3NOmAzkfPG8FTA8zLc7Li8/8efda230b212c0de2d3bbcb408507b1e/dns_record_request_sequence_recursive_resolver.png](https://cf-assets.www.cloudflare.com/slt3lc6tev37/3NOmAzkfPG8FTA8zLc7Li8/8efda230b212c0de2d3bbcb408507b1e/dns_record_request_sequence_recursive_resolver.png)

### Authoritative DNS Server
An authoritative DNS server is the one that actually holds the DNS resource records. It is the endpoint of the DNS lookup chain, which will ultimately respond with the requested resource record, allowing the web browser to make the request to reach the necessary IP address to access a website or other internet resources. An authoritative nameserver can handle queries with its own data without needing to consult another source, as it is the ultimate source of truth for certain DNS records.

![https://cf-assets.www.cloudflare.com/slt3lc6tev37/6Cxvsc4NOvmU4pPkKbkDmP/a7588a4c8a3c187e9175a40fa1b3d548/dns_record_request_sequence_authoritative_nameserver.png](https://cf-assets.www.cloudflare.com/slt3lc6tev37/6Cxvsc4NOvmU4pPkKbkDmP/a7588a4c8a3c187e9175a40fa1b3d548/dns_record_request_sequence_authoritative_nameserver.png)

**Note:** It is worth mentioning that in cases where the query is for a subdomain, such as blog.cloudflare.com, an additional nameserver will be added to the sequence after the authoritative nameserver. This additional nameserver is responsible for storing the CNAME record of the subdomain.

![https://cf-assets.www.cloudflare.com/slt3lc6tev37/1O1o3jhs0ztWsD00k8RLIJ/f33c1793a7e21cb92678c1f35ef1b245/dns_record_request_sequence_cname_subdomain.png](https://cf-assets.www.cloudflare.com/slt3lc6tev37/1O1o3jhs0ztWsD00k8RLIJ/f33c1793a7e21cb92678c1f35ef1b245/dns_record_request_sequence_cname_subdomain.png)

## DNS Servers
There are four DNS servers involved in retrieving data for a request. They are:
1. **DNS Resolver** - It is responsible for fetching the directly requested data from the browser when a user enters an address in the search bar, as in the example.
2. **Root Server** - It is the first step in DNS resolution, responsible for translating human-readable addresses into IPv4 and/or IPv6 format addresses.
3. **TLD Nameserver** - Also known as Top-Level Domain Server, it is responsible for hosting the last part of a hostname, such as all websites ending in .com, .net, .org, etc.
4. **Authoritative DNS Server** - The authoritative nameserver is the final stop in the DNS query. If it has access to the requested record, the authoritative nameserver will return the IP address of the requested hostname back to the DNS resolver that made the initial request.

### Steps of DNS Lookup
1. The user enters a URL in their search bar, such as "Website.com". This query goes from the local network to the internet, which redirects it to a DNS resolver.
2. The resolver queries a root DNS server.
3. The root server responds to the resolver with the address of a Top-Level Domain (TLD) DNS server that stores information about its domains. Again, websites ending in .com, .net, .org, etc.
4. The resolver then makes a request to the .com TLD.
5. Next, the TLD server responds with the IP address of the domain's nameserver, Website.com.
6. The recursive resolver sends a query to the domain's nameserver.
7. The IP address of Website.com is then returned to the resolver from the nameserver.
8. The DNS resolver, finally, responds to the web browser with the IP address of the initially requested domain.

Only after this "translation" process from the URL to the IP address, the browser can make the request for the web page.
1. The browser sends an HTTP request to the IP address.
2. The server at that IP returns the web page that should be rendered in the browser.

![https://cf-assets.www.cloudflare.com/slt3lc6tev37/1NzaAqpEFGjqTZPAS02oNv/bf7b3f305d9c35bde5c5b93a519ba6d5/what_is_a_dns_server_dns_lookup.png](https://cf-assets.www.cloudflare.com/slt3lc6tev37/1NzaAqpEFGjqTZPAS02oNv/bf7b3f305d9c35bde5c5b93a519ba6d5/what_is_a_dns_server_dns_lookup.png)

### DNS CNAME Record
The Canonical Name (CNAME) record is used in place of an A record when a domain or subdomain is an alias for another domain. All CNAME records must point to a domain, never to an IP address.

For example, suppose blog.example.com has a CNAME record with a value of "example.com" (without the "blog" part). This means that when a DNS server accesses the DNS records for blog.example.com, it actually triggers another DNS lookup for example.com, returning the IP address of example.com through its A record. In this case, we would say that example.com is the canonical name (or true name) of blog.example.com.

Often, when websites have subdomains like blog.example.com or shop.example.com, these subdomains will have CNAME records that point to a root domain (example.com). This way, if the IP address of the host changes, only the A record of the root domain needs to be updated, and all CNAME records will follow any changes made to the root.

**Example of a CNAME record:**
```
blog.example.com.    IN    CNAME    example.com.
```

### DNS Caching
DNS caching is used to improve the performance of DNS lookups and web queries. Caching occurs in a location closer to the client (user) so that subsequent DNS requests become more reliable, as they do not need to go through all the steps described in the Steps of DNS Lookup. In addition to reducing the loading times of cached addresses, caching also reduces bandwidth/CPU consumption. Cached DNS data can be stored in various locations for a finite period of time defined by the Time To Live (TTL), which is the time a packet can be stored in a network before being discarded.

#### ACDNS - Browser
Modern web browsers are designed to cache DNS records by default for a defined period of time. The goal here is obvious: the closer the DNS caching occurs to the web browser, the fewer processing steps need to be performed to check the cache and make the correct requests for an IP address. When a DNS record request is made, the browser cache is the first place checked in the search for the requested record.

**Additional Features of the Recursive Resolver:**
1. If it does not have the A records but has the NS records of the authoritative nameservers, the resolver will query those nameservers directly, bypassing the various steps of a DNS query. This shortcut avoids queries to the root servers and the .com nameservers (in our example.com query) and helps expedite DNS resolution.
2. If it does not have the NS records, the resolver will send a query to the TLD servers (.com, in our case), bypassing the root server.
3. In the unlikely event of not finding any records pointing to the TLD servers, the resolver will consult the root servers. This event usually occurs after a DNS cache cleanup.

#### ACDNS - Operating System (OS)
The DNS resolver at the operating system level is the second and final local stop before a DNS query leaves your machine. The process within your operating system designed to handle this query is usually called a "stub resolver" or DNS client. When it receives a request from an application, a stub resolver first checks its own cache to see if it has the record. Otherwise, it sends a DNS query (with a recursive flag set) outside the local network to a recursive DNS resolver within the internet service provider (ISP).

As with all previous steps, when it receives a DNS query, the recursive resolver within the ISP also checks if the requested host-to-IP translation is already stored within its local caching layer.

**Reminder: ACDNS = Authoritative DNS Cache.**

## Uniform Resource Identifiers and their Structures

## Uniform Resource Identifier (URI)
A Uniform Resource Identifier (URI) is a sequence of characters used to identify a logical or physical resource, typically on the internet. The URI describes the mechanisms for accessing a resource, the computers on which the resources are hosted, and the names of the resources on each computer.

**Examples of Protocols:** http, ftp, file, news, mailto, telnet.

**Examples of URIs:**
- ftp://ftp.is.co.za/rfc/rfc1808.txt
- http://www.ietf.org/rfc/rfc2396.txt
- ldap://[2001:db8::7]/c=GB?objectClass?one
- mailto:John.Doe@example.com
- news:comp.infosystems.www.servers.unix
- tel:+1-816-555-1212
- telnet://192.0.2.16:80/
- urn:oasis:names:specification:docbook:dtd:xml:4.1.2

### Uniform Resource Name (URN)
A URN is an internet resource with a static name that remains valid even if its data is moved to another location. Instead of needing to know the specific address of a resource to access it, as in URLs, in URNs you only need to know the name of the resource. A URN does not indicate which protocol should be used to locate and access a resource. It identifies a resource on the web through a unique and persistent name, but it does not necessarily inform where to find it. The purpose of a URN is to allow separation between identification (unique name) and location (e.g., URL addresses that can provide the identified resource). A URN will identify a resource throughout its lifecycle and will never change.

**Examples of URNs:**
- urn:isbn:0572248854
To identify a book by its ISBN number.

- urn:uuid:6e8bc430-9c3a-11d9-9669-0800200c9a66
As a globally unique identifier.

- urn:publishing:book
As an XML that identifies a document as a type of book.

### Uniform Resource Locator (URL)
A URL is the address of a resource on the internet. The URL informs the protocol that should be used to access the physical or logical resources contained in a network.

The URL schema is open and extremely simple for browsers. With this, browsers use various protocols to access different types of resources on the network.

**Examples of URLs:**
- [https://www.microsoft.com/](https://www.microsoft.com/)
- [https://www.linux.org/](https://www.linux.org/)
- [https://www.hostinger.com/](https://www.hostinger.com/)

#### URL Structure and Syntax
Simply put, the structure of a Uniform Resource Locator (URL) is divided into 6 parts.
1. **Protocol:** It informs which protocol should be used to locate and access the resources at the given address. **Example:** HTTP, HTTPS, mailto, telnet, news, ftp, file.
2. **Subdomain:** A subdomain consists of any words or phrases that come before the first dot in a URL. **Example:** www.support.blog.
3. **Domain Name:** A domain name is what users type in the browser's address bar to access a website. **Example:** Google, Facebook, YouTube.
4. **Domain Extension:** Also known as the top-level domain (TLD), it is the bit that follows the name of a website. **Example:** .com, .net, .org.
5. **Resource Path:** A path to the resource provides additional information to a web server, allowing it to take users to a specific location. A series of resource paths can point to a specific page, post, or file. It behaves like a folder structure within the website. **Example:** /tutorial/how-to-make-a-website/youtube/channel/.
6. **Parameters:** Parameters are query strings or URL variables. They are the part of a URL after a question mark. Parameters contain key-value pairs separated by an equal sign (=). Additionally, a URL can have multiple variables, in which case the ampersand symbol (&) will separate each one. **Example:** ?q=siteAfacebook.com%2Fcreateaccount

#### Classification of URLs
- **Canonical URLs -** Website owners can use canonical URLs if they have duplicate content. Setting a URL as canonical is a way to let search engines know which internet address to crawl and index.
- **Callback URLs -** They refer to an initial destination when users complete a process in an external system.
- **Custom URLs -** Also known as custom short URLs, they are easy-to-remember web addresses. Typically, a custom URL is a redirection from a longer URL. Website owners can use a URL shortening tool like Bitly, Short.io, and TinyURL to create a custom URL.

#### Classification of TLDs
Here are the most commonly used types of TLD extensions:
- **Generic TLD (gTLD)** - This category includes most popular extensions, including .com, .org, .net.
- **Country Code TLD (ccTLD)** - As the name suggests, this TLD indicates a country, territory, or geographical area. The ccTLD consists of two letters based on the international country codes, such as .br, .uk, .in, and .sg.
- **Sponsored TLD (sTLD)** - This type of extension is sponsored and used for specific organizations. For example, Tralliance Registry Management Company, LLC sponsors .travel, and DotAsia Organization Ltd. sponsors .asia.
- **New gTLD (nTLD)** - It is a new generation of domain extensions. Basically, any TLD launched after January 12, 2012, is a new gTLD, including .online, .store, and .tech.

#### Common Parameters and Their Functions
- **Localization -** Having a country code in the query string translates a web page to the language of the associated country.
- **Search -** The search parameter provides search results from an internal search system of a website.
- **Filtering -** To separate distinct fields, such as topic, color, price range, and region, website owners can use the filtering parameter.
- **Pagination -** This parameter is especially useful for e-commerce sites, allowing website owners to organize content.
- **Tracking -** It often contains codes from the Urchin Tracking Module to track ad traffic and marketing campaigns.

# Recommended Readings
- [The internet, explained](https://www.vox.com/2014/6/16/18076282/the-internet)
- [How does the Internet work? - Learn web development | MDN](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Web_mechanics/How_does_the_Internet_work)
- https://www.cloudflare.com/en-gb/learning/ddos/glossary/hypertext-transfer-protocol-http/
- [Role of Rendering Engines in Browsers | BrowserStack](https://www.browserstack.com/guide/browser-rendering-engine)
- [Populating the page: how browsers work - Web performance | MDN](https://developer.mozilla.org/en-US/docs/Web/Performance/How_browsers_work)

# Bibliography
- [O que é URL: significado e como ela pode ajudar o seu negócio!](https://rockcontent.com/br/blog/url/)
- [What is DNS? | How DNS works | Cloudflare](https://www.cloudflare.com/en-gb/learning/dns/what-is-dns/)
- [O que são URI, URL e URN? - Tech Enter](https://techenter.com.br/o-que-sao-uri-url-e-urn/)
- [URI](https://pt.wikipedia.org/wiki/URI)
- [URL](https://en.wikipedia.org/wiki/URL)
- (https://www.cloudflare.com/pt-br/learning/dns/glossary/what-is-a-domain-name/)
- [O Que é URL: Exemplos, Estrutura e Muito Mais](https://www.hostinger.com.br/tutoriais/url)
- [O que é um registro DNS CNAME? | Cloudflare](https://www.cloudflare.com/pt-br/learning/dns/dns-records/dns-cname-record/)