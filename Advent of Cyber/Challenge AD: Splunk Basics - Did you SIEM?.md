Link: https://tryhackme.com/room/splunkforloganalysis-aoc2025-x8fj2k4rqp

**Task 1: Introduction**

Read the content and start the machine

**Task 2: Log Analysis with Splunk**

**Answer the questions below**

1. _**What is the attacker IP found attacking and compromising the web server?**_

Answer: **`198.51.100.55`**

**Explanation**

We navigate to Splunk and we select "Search & Reporting"

<img width="1894" height="584" alt="Screenshot 2025-12-04 113016" src="https://github.com/user-attachments/assets/12597a04-562c-4f92-a3a3-ff80238cab1f" />

And in the search box, we type the following command and select **"All Time"** instead of "Last 24 hours"

**`sourcetype=web_traffic user_agent!=*Mozilla* user_agent!=*Chrome* user_agent!=*Safari* user_agent!=*Firefox* | stats count by client_ip | sort -count | head 5`**

<img width="1915" height="567" alt="Screenshot 2025-12-04 113141" src="https://github.com/user-attachments/assets/31dc18f8-6a91-4c37-bdbb-0e26fd2fa9b7" />

<img width="1919" height="492" alt="Screenshot 2025-12-04 113345" src="https://github.com/user-attachments/assets/6d0fd604-3828-4b14-9fcc-fa1a97fb6be7" />

And we can see the IP address

_________________________________________________________

2. **_Which day was the peak traffic in the logs? (Format: YYYY-MM-DD)_**

Answer: **`2025-10-12`**

**Explanation:**

Again in the search bar, we enter the following command and make sure the time period is set to **"All time"**

**`index=main sourcetype=web_traffic | timechart span=1d count | sort by count | reverse`**

<img width="1900" height="772" alt="Screenshot 2025-12-04 113821" src="https://github.com/user-attachments/assets/3449da10-6547-432e-b99f-ceece2d255c6" />

Now we will click on Visualization tab 

<img width="1916" height="687" alt="Screenshot 2025-12-04 113855" src="https://github.com/user-attachments/assets/35f225a9-d038-43cc-a083-f3265ee11597" />

We can see that 12th Oct 2025 has the peak traffic

<img width="1898" height="660" alt="Screenshot 2025-12-04 113915" src="https://github.com/user-attachments/assets/af7365d4-ec6e-47a5-95e1-ff1ea961d908" />

_________________________________________________________

3. **_What is the count of Havij user_agent events found in the logs?_**

Answer: **`993`**

**Explanation**

We will use the same command as in the previous question and then select Events tab

<img width="1889" height="760" alt="Screenshot 2025-12-04 114232" src="https://github.com/user-attachments/assets/f226a481-1f44-431d-ac3d-8590ffbc202d" />

And on the left side menu, we select **`user_agent`** and see the count for Havij

<img width="1100" height="773" alt="Screenshot 2025-12-04 114331" src="https://github.com/user-attachments/assets/d6e3cd79-1e41-4b29-905c-5b4a44cfdc85" />

_______________________________________________________

4. **_How many path traversal attempts to access sensitive files on the server were observed?_**

Answer: **`658`**

**Explanation:**

We use the following command 

**`sourcetype=web_traffic client_ip="198.51.100.55" AND path="*..\/..\/*" OR path="*redirect*" | stats count by path`**

<img width="1897" height="821" alt="Screenshot 2025-12-04 115254" src="https://github.com/user-attachments/assets/d44cb9c0-5136-4383-8335-206f5da7e480" />

We navigate to the Statistics tab and see that **`/download?file=../../etc/passwd`** has the count 658

<img width="1919" height="431" alt="Screenshot 2025-12-04 115402" src="https://github.com/user-attachments/assets/ae0ee579-77b5-45db-a1bb-9a2f80da2171" />

_______________________________________________________

5. **_Examine the firewall logs. How many bytes were transferred to the C2 server IP from the compromised web server?_**

Answer: **`126167`**

**Explanation:**

We use the following command 

**`sourcetype=firewall_logs src_ip="10.10.1.5" AND dest_ip="198.51.100.55" AND action="ALLOWED" | stats sum(bytes_transferred) by src_ip`**

<img width="1896" height="857" alt="Screenshot 2025-12-04 120027" src="https://github.com/user-attachments/assets/d691335f-48e2-4eb4-9010-fe9dc044e64d" />

Now we will select Statistics tab and see the count

<img width="1894" height="383" alt="Screenshot 2025-12-04 120133" src="https://github.com/user-attachments/assets/245adbfa-d3d0-40c4-b794-de515db43930" />

__________________________________________________________

6. _**If you enjoyed today's room, check out the Incident Handling With Splunk room to learn more about analyzing logs with Splunk.**_

Answer: No answer needed

__________________________________________________________
