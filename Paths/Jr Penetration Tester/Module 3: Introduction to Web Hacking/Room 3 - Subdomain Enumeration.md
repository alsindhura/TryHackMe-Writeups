Link: https://tryhackme.com/room/subdomainenumeration (Premium Room)

<img width="512" height="512" alt="image" src="https://github.com/user-attachments/assets/91407937-12bd-40d4-98ce-af29941bd1ed" />

Learn the various ways of discovering subdomains to expand your attack surface of a target.

**Task 1: Brief**

Subdomain enumeration is the process of finding valid subdomains for a domain, but why do we do this? We do this to expand our attack surface to try and discover more potential points of vulnerability.

We will explore three different subdomain enumeration methods: Brute Force, OSINT (Open-Source Intelligence) and Virtual Host.

Start the machine and then move onto the next task.

**Answer the questions below**

1. _What is a subdomain enumeration method beginning with B?_

Answer: `Brute Force,`

2. _What is a subdomain enumeration method beginning with O?_

Answer: ` OSINT`

3. _What is a subdomain enumeration method beginning with V?_

Answer: `Virtual Host.`

---

**Task 2: OSINT - SSL/TLS Certificates**

When an SSL/TLS (Secure Sockets Layer/Transport Layer Security) certificate is created for a domain by a CA (Certificate Authority), CA's take part in what's called "Certificate Transparency (CT) logs". These are publicly accessible logs of every SSL/TLS certificate created for a domain name. The purpose of Certificate Transparency logs is to stop malicious and accidentally made certificates from being used. We can use this service to our advantage to discover subdomains belonging to a domain, sites like https://crt.sh offer a searchable database of certificates that shows current and historical results.

Go to crt.sh and search for the domain name tryhackme.com, find the entry that was logged at 2020-12-26 and enter the domain below to answer the question.

**Answer the questions below**

1. _What domain was logged on crt.sh at 2020-12-26?_

Answer: `store.tryhackme.com`

**_Explanation:_**

we visit https://crt.sh/ and search for tryhackme.com

<img width="670" height="431" alt="image" src="https://github.com/user-attachments/assets/f8586827-ea0a-4a8c-8152-5dc637959a87" />

Now we search for the domain with the date `2020-12-26` and get our answer

<img width="1024" height="163" alt="image" src="https://github.com/user-attachments/assets/52f1b763-e848-4d60-8b2a-77d1ba25d50e" />


---

**Task 3: OSINT - Search Engines**

Search engines contain trillions of links to more than a billion websites, which can be an excellent resource for finding new subdomains. Using advanced search methods on websites like Google, such as the `site: filter`, can narrow the search results. For example, `site:*.domain.com -site:www.domain.com` would only contain results leading to the domain name domain.com but exclude any links to www.domain.com; therefore, it shows us only subdomain names belonging to domain.com.

Go to [Google](https://tryhackme.com/room/google.com) and use the search term `site:*.tryhackme.com -site:www.tryhackme.com`, which should reveal a subdomain for tryhackme.com; use that subdomain to answer the question below.

**Answer the questions below**

1. _What is the TryHackMe subdomain beginning with S discovered using the above Google search?_

Answer: `store.tryhackme.com`

**_Explanation:_**

We go to google and search `site:*.tryhackme.com -site:www.tryhackme.com` and see the answer

<img width="904" height="575" alt="image(3)" src="https://github.com/user-attachments/assets/cd25c36b-45c3-41fe-900d-0af6aa7df7af" />

---

**Task 4: DNS Bruteforce**

Bruteforce DNS (Domain Name System) enumeration is the method of trying tens, hundreds, thousands or even millions of different possible subdomains from a pre-defined list of commonly used subdomains. Because this method requires many requests, we automate it with tools to make the process quicker. In this instance, we are using a tool called dnsrecon to perform this. Click the "View Site" button to open the static site, press the "Run DNSrecon Request" button to start the simulation, and then answer the question below.

**Answer the questions below**

1. _What is the first subdomain found with the dnsrecon tool?_

Answer: `api.acmeitsupport.thm`

**_Explanation:_**

We click on "View Site" button and see something like this

<img width="1025" height="620" alt="image" src="https://github.com/user-attachments/assets/f088f06a-cd39-4184-8355-c0736c60be49" />

Now we click on the "Run DNSrecon Request" and we see two records and our answer is the first one

<img width="1019" height="614" alt="image" src="https://github.com/user-attachments/assets/4803e0c7-f11e-41e9-98b9-65a065089367" />

---

**Task 5: OSINT - Sublist3r**

To speed up the process of OSINT subdomain discovery, we can automate the above methods with the help of tools like [Sublist3r](https://www.kali.org/tools/sublist3r/), click the "View Site" button to open up the static site and run the sublist3r simulation to discover a new subdomain that will help answer the question below.

**Answer the questions below**

1. _What is the first subdomain discovered by sublist3r?_

Answer: `web55.acmeitsupport.thm`

**_Explanation:_**

We click on "View Site" button and see something like this

<img width="1021" height="624" alt="image" src="https://github.com/user-attachments/assets/f55f1baa-c127-4733-a4aa-add10d9990b2" />

Now we click on the "Run Sublist3r Request" and we see two records and our answer is the first one

<img width="1018" height="586" alt="image" src="https://github.com/user-attachments/assets/371d41fc-2b67-4417-a76f-c91e21f3cbe1" />

---

**Task 6: Virtual Hosts**

Some subdomains aren't always hosted in publically accessible DNS results, such as development versions of a web application or administration portals. Instead, the DNS record could be kept on a private DNS server or recorded on the developer's machines in their /etc/hosts file (or c:\windows\system32\drivers\etc\hosts file for Windows users), which maps domain names to IP addresses. 

Because web servers can host multiple websites from one server when a website is requested from a client, the server knows which website the client wants from the Host header. We can utilize this host header by making changes to it and monitoring the response to see if we've discovered a new website.

Like with DNS Bruteforce, we can automate this process by using a wordlist of commonly used subdomains.

Start the AttackBox and then try the following command against the Acme IT Support machine to discover a new subdomain.

```
user@machine$ ffuf -w /usr/share/wordlists/SecLists/Discovery/DNS/namelist.txt -H "Host: FUZZ.acmeitsupport.thm" -u http://10.201.71.25
```

The above command uses the -w switch to specify the wordlist we are going to use. The -H switch adds/edits a header (in this instance, the Host header), we have the FUZZ keyword in the space where a subdomain would normally go, and this is where we will try all the options from the wordlist.

Because the above command will always produce a valid result, we need to filter the output. We can do this by using the page size result with the -fs switch. Edit the below command replacing {size} with the most occurring size value from the previous result and try it on the AttackBox.

```
user@machine$ ffuf -w /usr/share/wordlists/SecLists/Discovery/DNS/namelist.txt -H "Host: FUZZ.acmeitsupport.thm" -u http://10.201.71.25 -fs {size}
```


This command has a similar syntax to the first apart from the -fs switch, which tells ffuf to ignore any results that are of the specified size.

The above command should have revealed two positive results that we haven't come across before.

**Answer the questions below**

1. _What is the first subdomain discovered?_

Answer: `delta`

**_Explanation:_**

We use the command `ffuf -w /usr/share/wordlists/seclists/Discovery/DNS/namelist.txt -H "Host: FUZZ.acmeitsupport.thm" -u http://10.201.71.25`

<img width="1535" height="995" alt="image" src="https://github.com/user-attachments/assets/b15b1c12-5616-4966-9e68-abd2c7595ffe" />

And we can see many requests have the size: 2395 now we can ignore this size by using the command 

`ffuf -w /usr/share/wordlists/seclists/Discovery/DNS/namelist.txt -H "Host: FUZZ.acmeitsupport.thm" -u http://10.201.71.25 -fs 2395`

And we can see the first sub-domain as `api` but our answer needs 5 letters so we see our second-domain as `delta` and that is our answer

<img width="1664" height="728" alt="image" src="https://github.com/user-attachments/assets/5f4362fe-6a10-4ab5-a276-f6830f57d78f" />


2. _What is the second subdomain discovered?_

Answer: `yellow`

**_Explanation:_**

So we need to choose third-domain (second-domain from api)

<img width="1920" height="757" alt="image" src="https://github.com/user-attachments/assets/488e73ba-1b6d-47d1-ad8e-4f2461930c84" />

---
