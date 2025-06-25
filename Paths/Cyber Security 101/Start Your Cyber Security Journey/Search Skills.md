Link : https://tryhackme.com/room/searchskills 

![image](https://github.com/user-attachments/assets/1674c84a-5c7c-45a1-b41a-846a0c45a044)

**Module 1: Introduction**

A quick Google search for “learn cyber security” returned around 600 million hits, while a search for “learn hacking” returned more than double that number! The number might have grown even further when you go through this room.

We are surrounded by information. Do you prefer to surrender in the face of information overload and accept the first few results you get? Or do you like to acquire the necessary search skills to find and access what you are looking for? This room aims to help you with the latter.

Learning Objectives

The goal of this room is to teach:

1. Evaluate information sources
   
2. Use search engines efficiently
   
3. Explore specialized search engines
   
4. Read technical documentation
   
5. Make use of social media

6. Check news outlets
   
**Answer the questions below** 

**Check how many results you get when searching for learn hacking. At the time of writing, we got 1.5 billion results when searching on Google.**

Answer: No answer required

**Module 2: Evaluation of Search Results**

![image](https://github.com/user-attachments/assets/525616d5-31cd-411c-a4c9-1690e66ebf15)

On the Internet, everyone can publish their writings. It can be in the form of blog posts, articles, or social media posts. It can be even in more subtle ways, such as by editing a public wiki page. This ability makes it possible for anyone to voice their unfounded claims. Everyone can express their opinion about best cyber security practices, future programming trends, and how to best prepare for a DevSecOps interview.

It is our job, as readers, to evaluate the information. We will mention a few things to consider when evaluating information:

**Source**: Identify the author or organization publishing the information. Consider whether they are reputable and authoritative on the subject matter. Publishing a blog post does not make one an authority on the subject.

**Evidence and reasoning**: Check whether the claims are backed by credible evidence and logical reasoning. We are seeking hard facts and solid arguments.

**Objectivity and bias**: Evaluate whether the information is presented impartially and rationally, reflecting multiple perspectives. We are not interested in authors pushing shady agendas, whether to promote a product or attack a rival.

**Corroboration and consistency**: Validate the presented information by corroboration from multiple independent sources. Check whether multiple reliable and reputable sources agree on the central claims.


**Answer the questions below**

**What do you call a cryptographic method or product considered bogus or fraudulent?**

Answer: `Snake oil`

![Screenshot from 2025-06-25 17-14-18](https://github.com/user-attachments/assets/fa44f589-3bce-48e4-90de-895284eeaadb)

**What is the name of the command replacing netstat in Linux systems?**

Answer: `ss`
![Screenshot from 2025-06-25 17-17-11](https://github.com/user-attachments/assets/4f0e36ff-f181-4031-a41b-335b63780277)

**Module 3: Search Engines**

Every one of us has used an Internet search engine; however, not everyone has tried to harness the full power of an Internet search engine. Almost every Internet search engine allows you to carry out advanced searches. Consider the following examples:

Google

Bing

DuckDuckGo

Let’s consider the search operators supported by Google.

1. **"exact phrase"**: Double quotes indicate that you are looking for pages with the exact word or phrase.
   
For example, one might search for `"passive reconnaissance"` to get pages with this exact phrase.

2. **site:** : This operator lets you specify the domain name to which you want to limit your search.

For example, we can search for success stories on TryHackMe using `site:tryhackme.com success stories`.

3. **-**: The minus sign allows you to omit search results that contain a particular word or phrase.

For example, you might be interested in learning about the pyramids, but you don’t want to view tourism websites; one approach is to search for `pyramids -tourism` or `-tourism pyramids`.

4. **filetype:** : This search operator is indispensable for finding files instead of web pages. Some of the file types you can search for using Google are Portable Document Format (PDF), Microsoft Word Document (DOC), Microsoft Excel Spreadsheet (XLS), and Microsoft PowerPoint Presentation (PPT).

For example, to find cyber security presentations, try searching for `filetype:ppt cyber security`.

You can check more advanced controls in various search engines in this advanced search operators list; however, the above provides a good starting point. Check your favourite search engine for the supported search operators.

**Answer the questions below** 

**How would you limit your Google search to PDF files containing the terms cyber warfare report?**

Answer: `filetype:pdf cyber warfare report`

**What phrase does the Linux command ss stand for?**

Answer: `socket statistics` 

(Refer image from the last module)

**Module 4: Specialized Search Engines**

You are familiar with Internet search engines; however, how much are you familiar with specialized search engines? By that, we refer to search engines used to find specific types of results.

**Shodan**

Let’s start with Shodan, a search engine for devices connected to the Internet. It allows you to search for specific types and versions of servers, networking equipment, industrial control systems, and IoT devices. You may want to see how many servers are still running Apache 2.4.1 and the distribution across countries. To find the answer, we can search for apache 2.4.1, which will return the list of servers with the string “apache 2.4.1” in their headers.

![image](https://github.com/user-attachments/assets/9290d8a0-eed9-4734-8c42-e44262ace11f)

Consider visiting Shodan Search Query Examples for more examples. Furthermore, you can check Shodan trends for historical insights if you have a subscription.

**Censys**

At first glance, Censys appears similar to Shodan. However, Shodan focuses on Internet-connected devices and systems, such as servers, routers, webcams, and IoT devices. Censys, on the other hand, focuses on Internet-connected hosts, websites, certificates, and other Internet assets.

Some of its use cases include enumerating domains in use, auditing open ports and services, and discovering rogue assets within a network. You might want to check Censys Introductory Use Cases.

![image](https://github.com/user-attachments/assets/0203d82e-d0e0-4ba3-a519-bc9e74fba01a)

**VirusTotal**

VirusTotal is an online website that provides a virus-scanning service for files using multiple antivirus engines. It allows users to upload files or provide URLs to scan them against numerous antivirus engines and website scanners in a single operation. They can even input file hashes to check the results of previously uploaded files.

The screenshot below shows the result of checking the submitted file against 67 antivirus engines. Furthermore, one can check the community's comments for more insights. Occasionally, a file might be flagged as a virus or a Trojan; however, this might not be accurate for various reasons, and that's when community members can provide a more in-depth explanation.

![image](https://github.com/user-attachments/assets/5af31a88-e6e3-4f5e-88bf-bc1a6180eb69)

**Have I Been Pwned**

Have I Been Pwned (HIBP) does one thing; it tells you if an email address has appeared in a leaked data breach. Finding one’s email within leaked data indicates leaked private information and, more importantly, passwords. Many users use the same password across multiple platforms, if one platform is breached, their password on other platforms is also exposed. Indeed, passwords are usually stored in encrypted format; however, many passwords are not that complex and can be recovered using a variety of attacks.

![image](https://github.com/user-attachments/assets/6bb187ba-62ad-42de-9ce2-9225a7c2fb83)

**Answer the questions below**

**What is the top country with lighttpd servers?**

Answer: `United States`

![Screenshot from 2025-06-25 17-49-52](https://github.com/user-attachments/assets/d61f5957-ad94-44f6-a30a-e7774d7cecff)

**What does BitDefenderFalx detect the file with the hash 2de70ca737c1f4602517c555ddd54165432cf231ffc0e21fb2e23b9dd14e7fb4 as?**

Answer: `Android.Riskware.Agent.LHH`
![Screenshot from 2025-06-25 17-58-45](https://github.com/user-attachments/assets/98e28529-7b1b-42d0-b79f-8bf6bbc36732)

**Module 5: Vulnerabilities and Exploits**

**CVE**

We can think of the Common Vulnerabilities and Exposures (CVE) program as a dictionary of vulnerabilities. It provides a standardized identifier for vulnerabilities and security issues in software and hardware products. Each vulnerability is assigned a CVE ID with a standardized format like CVE-2024-29988. This unique identifier (CVE ID) ensures that everyone from security researchers to vendors and IT professionals is referring to the same vulnerability, CVE-2024-29988 in this case.

The MITRE Corporation maintains the CVE system. For more information and to search for existing CVEs, visit the CVE Program website. Alternatively, visit the National Vulnerability Database (NVD) website. The screenshot below shows CVE-2014-0160, also known as Heartbleed.

![image](https://github.com/user-attachments/assets/31f1820e-f58a-43c4-acd5-45d6ef0aa354)

**Exploit Database**

There are many reasons why you would want to exploit a vulnerable application; one would be assessing a company’s security as part of its red team. Needless to say, we should not try to exploit a vulnerable system unless we are given permission, usually via a legally binding agreement.

Now that we have permission to exploit a vulnerable system, we might need to find a working exploit code. One resource is the Exploit Database. The Exploit Database lists exploit codes from various authors; some of these exploit codes are tested and marked as verified.

![image](https://github.com/user-attachments/assets/b6ac7888-0884-4a8f-92f0-c6784946a5e2)

GitHub, a web-based platform for software development, can contain many tools related to CVEs, along with proof-of-concept (PoC) and exploit codes. To demonstrate this idea, check the screenshot below of search results on GitHub that are related to the Heartbleed vulnerability.

![image](https://github.com/user-attachments/assets/99bbc761-1536-4ecf-b6a0-d792ec245027)

**Answer the questions below**

**What utility does CVE-2024-3094 refer to?**

Answer: `xz`

Go to https://www.cve.org/ and type the exploit ID `CVE-2024-3094` and we can see a sentence called "Malicious code was discovered in the upstream tarballs of xz"

![Screenshot from 2025-06-25 18-09-45](https://github.com/user-attachments/assets/2485d7c0-73b4-4058-b3e9-125beb6a65cb)

![Screenshot from 2025-06-25 18-12-32](https://github.com/user-attachments/assets/c58d4606-ca68-49c6-8b4e-de2b6f9eaf08)

**Module 6: Technical Documentation**

One vital skill to acquire is to look up official documentation. We will cover a few examples of official documentation pages.

**Linux Manual Pages**

Long before the Internet was everywhere, how would you get help using a command in a Linux or Unix-like system? The answer would be checking the manual page, man page for short. On Linux and every Unix-like system, each command is expected to have a man page. In fact, man pages also exist for system calls, library functions, and even configuration files.

Let’s say we want to check the manual page for the command ip. We issue the command man ip. The screenshot below shows the page we received. You might want to start the AttackBox and run man ip on the terminal. Press q to quit.

![image](https://github.com/user-attachments/assets/0751b6af-1e35-4442-8d8b-cbd67a3e1fdf)

If you prefer to read the man page of ip in your web browser, just type man ip in your favourite search engine. This page might be at the top of the results.

**Microsoft Windows**

Microsoft provides an official Technical Documentation page for its products. The screenshot below shows the search results for the command ipconfig.

![image](https://github.com/user-attachments/assets/cc101ad9-9ca8-4863-886d-9d067f0a1585)

**Product Documentation**

Every popular product is expected to have well-organized documentation. This documentation provides an official and reliable source of information about the product features and functions. 

Examples include Snort Official Documentation, Apache HTTP Server Documentation, PHP Documentation, and Node.js Documentation.

It is always rewarding to check the official documentation as it is the most up-to-date and offers the most complete product information.

**Answer the questions below**

**What does the Linux command cat stand for?**

Answer: `concatenate`

![Screenshot from 2025-06-25 18-19-20](https://github.com/user-attachments/assets/8a60c8d7-14c5-4743-a76a-205336cf7531)

**What is the netstat parameter in MS Windows that displays the executable associated with each active connection and listening port?**

Answer: `-b`

Visit https://learn.microsoft.com/en-gb/ and type `netstat`

![Screenshot from 2025-06-25 18-23-47](https://github.com/user-attachments/assets/f6b71481-e0b1-4593-99bc-3acfddce7966)

And now we will be redirected to the page https://learn.microsoft.com/en-gb/search/?terms=netstat click on the first link of this page

![Screenshot from 2025-06-25 18-25-11](https://github.com/user-attachments/assets/578f789f-947d-430d-b447-52a8104312a2)

And now we will be redirected to https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netstat

Here we find something called `Parameters` and we also find `-b` has the description similar to our question

![Screenshot from 2025-06-25 18-26-31](https://github.com/user-attachments/assets/a2e22876-1381-4d80-8f36-ee1ef05d1bde)

**Module 7: Social Media**

![image](https://github.com/user-attachments/assets/2c989c05-fc8f-439e-88b5-0f239f8d31df)

There are billions of users registered on social media platforms such as Facebook, Twitter, and LinkedIn. We expect you to be familiar with popular platforms. However, if you are aware of any platform you are not familiar with, we recommend that you check it out and learn about it. Ideally, one would want to explore a platform without creating an account; however, this severely limits your experience. Instead, one recommendation is to use a temporary email address to discover these platforms without linking them to your real email addresses; once done, you can terminate the accounts and associated email addresses. One reason for not using your primary account is that you don’t want your contacts to start connecting with you there when you are only temporarily exploring a platform.

The power of social media is that it allows you to connect with companies and people you are interested in. Furthermore, social media offers a wealth of information for cyber security professionals, whether they are searching for people or technical information. Why is searching for people important, you ask?

When protecting a company, you should ensure that the people you protect are not oversharing on social media. For instance, their social media might give away the answer to their secret questions, such as, “Which school did you go to as a child?”. Such information might allow adversaries to reset their passwords and take over their accounts effortlessly.

Furthermore, as a cyber security professional, you want to stay updated with new cyber security trends, technologies, and products. Following the proper channels and groups can provide a suitable environment for growing your technical expertise.

Besides staying updated via social media channels and groups, we should mention news outlets. Hundreds of news websites would offer valuable cyber-security-related news. Try different ones and stick with the ones you like most.

**Answer the questions below**

**You are hired to evaluate the security of a particular company. What is a popular social media website you would use to learn about the technical background of one of their employees?**

Answer: `LinkedIn`

**Continuing with the previous scenario, you are trying to find the answer to the secret question, “Which school did you go to as a child?”. What social media website would you consider checking to find the answer to such secret questions?**

Answer: `facebook`

** Module 8: Conclusion**

This room focused on the most common sources of information for cyber security professionals. There are plenty more. As the information landscape keeps changing, it is impossible to cover all the sources. However, by subscribing to relevant cyber security groups, one can stay ahead and be aware whenever new interesting sources arise.


**Answer the questions below**

**Ensure you have noted the various search engines and resources mentioned in this room as they will be convenient in any cyber security path you follow.**

Answer: No answer needed
