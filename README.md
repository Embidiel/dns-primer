# DNS Primer


## Ano?
Ang ginagawa ng isang **DNS** or **Domain Name System** ay cino-convert niya yung isang **hostname** (ex : facebook.com) papunta sa isang **IP Address** (192.168.0.0)

Kapag ine-expose mo yung computer mo sa internet, nagkakaroon siya ng assigned IP Address or Internet Protocol Address. Pwede tong maging **IPv4 (192.168.0.0)** or **IPv6 (2001:0db8:85a3:0000:0000:8a2e:0370:7334)**

Pero tayong mga tao, ano ba yung mas naalala natin? Numbers or names? Names diba? Kaya gumagamit tayo ng hostname para ma-access ang isang website sa internet.

Kapag nag e-enter ka ng website, for example facebook.com sa browser mo. Hindi alam ng browser mo kung saang server naka locate si facebook.com. **Kaya si browser kumo-connect siya sa isang DNS**. **Tapos si DNS mina-map niya yung hostname sa isang IP Address para ma access si facebook.com**

So si **DNS isa siyang large collection of servers & databases** na nagwo-work sa isang **DNS Protocol**.

![enter image description here](https://res.cloudinary.com/practicaldev/image/fetch/s--094_8-aq--/c_limit,f_auto,fl_progressive,q_auto,w_880/https://talk.hyvor.com/blog/wp-content/uploads/2020/01/a7f51433-7b1b-4f00-84f6-313c622aa749.png)



## DNS Protocol

So paano ba gumagana or tumatakbo ang isang DNS?
Yung image sa taas parang ang dali lang diba, 2 steps lang. Pero in reality maraming steps ang nagaganap para mahanap yung IP Address nung hostname.

**4 Parts / Servers of a DNS.**

1.  **DNS Recursor** : Librarian
2.  **Root Nameserver**  : Corridor with Bookshelves
3.  **Top-Level Domain (TLD) Nameserver** : Bookshelf na may category
4.  **Authoritative Nameserver** : Book
 
## DNS Recursor / Resolver
Kapag nag re-request tayo ng site for example facebook.com, pagka enter natin nito sa browser, dumadaan tong request na to sa isang DNS Recursor. **Ang isang DNS Recursor ay provided na ng mga ISP natin tulad ng PLDT o Globe.**

Pero si DNS Resolver, di rin niya alam kung ano yung IP Address nung given na hostname. Kaya ang gagawin niya magse-send siya ng request papunta sa ibang server, specifically the Root Name Server

## Root Name Server
So meron lang 13 na root name servers across the world. Gagawin ni DNS Resolver magrerecursive request papunta sa 13 root name servers na to hanggang mahanap yung TLD Server na pasok sa requested na hostname. Ang kaya lang gawin ng isang Root Name Server ay ibigay yung address ng isang Top Level Domain Server na may hawak sa mga .com websites papunta ulit sa DNS Resolver.

## Top Level Domain Server
**Eto yung nag me-maintain ng data sa lahat ng top level domains**. Example .com. .org . io, etc. So pag napasok na dito yung request mo na facebook.com. Ibibigay niya yung address ng isang Authoritative Nameserver na may hawak nito.

## Authoritative Nameserver
Last step, finally hahaha. So for example facebook.com, ang job dito ng isang Authoritative Nameserver ay hanapin yung IP Address nito sa server niya. Magpe-perform dito si Authoritative Nameserver ng isang DNS Lookup or search for **A Name and C Name Records**. Pag may nakitang record, boom ayun na ang IP Address ni facebook.com

## TLDR
-   Tinype mo facebook.com sa browser mo.
-   Yung browser mo magre-request ng IP Address ni facebook.com papunta sa isang DNS Resolver.
-    Yung DNS Resolver mag se-send ng request step by step para makita yung address ng mga to.
	    -   Root Nameserver
	    -   TLD Nameserver
-   Last step yung Authoritative Nameserver na may hawak ng domain, ibabalik niya yung IP Address ng requested na hostname pabalik sa DNS Recursor, tapos si DNS Recursor ipapasa niya yung IP Address sa browser.

![enter image description here](https://res.cloudinary.com/practicaldev/image/fetch/s--P0AZENio--/c_limit,f_auto,fl_progressive,q_auto,w_880/https://www.cloudflare.com/img/learning/dns/dns-server-types/authoritative-nameserver.png)

## DNS Caching
Isa tong process para di na maground trip ulit yung browser mo sa pagkuha ng IP Address ng isang hostname. Pwede rin maganap yung caching sa isa sa mga DNS Servers o OS nung user.

**Example flow:**

-   Nagrequest ka ng facebook.com sa browser.
-   Yung browser che-check niya kung may cache nung DNS data.
    -   If found, it terminates the DNS resolving and sends the request directly to the IP address.
    -   If not, it asks for it from the DNS Recursor.
-   The DNS Recursor checks its cache for the DNS data of the requested domain.
    -   If found, it terminates the DNS resolving and sends the IP address back to the browser without further requests.
    -   If not, continues the DNS resolving process...
-   ......

So rare na mangyayari yung scenario na mapupunta sa Authoritative server yung request unless bago yung domain.

## DNS Records

## Types of DNS Records

## Reference
