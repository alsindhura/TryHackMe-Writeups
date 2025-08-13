Link : https://tryhackme.com/room/burpsuitebasics (Premium Room)

<img width="800" height="800" alt="image" src="https://github.com/user-attachments/assets/622b4419-f804-4fb0-b67b-fa875638d56e" />

An introduction to using Burp Suite for web application pentesting.

**Module 1: Introduction**

Welcome to Burp Suite Basics!

This particular room aims to understand the basics of the Burp Suite web application security testing framework. Our focus will revolve around the following key aspects:

- A thorough introduction to Burp Suite.

- A comprehensive overview of the various tools available within the framework.

- Detailed guidance on the process of installing Burp Suite on your system.

- Navigating and configuring Burp Suite.

We will also introduce the core of the Burp Suite framework, which is the Burp Proxy. It is important to note that this room primarily serves as a foundational resource for acquiring knowledge about Burp Suite. Subsequent rooms in the Burp module will adopt a more practical approach. Thus, this room will contain a greater emphasis on theoretical content. If you have not yet utilised Burp Suite, it is recommended to carefully read the provided information and actively engage with the tool. Experimentation is essential for grasping the fundamentals of this framework. Combining the information presented here with hands-on exploration will establish a strong foundation for utilising the framework. This will significantly assist you in future rooms.

**Answer the questions below**

1. _Let us start!_

Answer: No answer needed

------------------------------------------------------------------------------------------------------------------------------------------------


**Module 2: What is Burp Suite**

In essence, Burp Suite is a Java-based framework designed to serve as a comprehensive solution for conducting web application penetration testing. It has become the industry standard tool for hands-on security assessments of web and mobile applications, including those that rely on application programming interfaces (APIs).

Simply put, Burp Suite captures and enables manipulation of all the HTTP/HTTPS traffic between a browser and a web server. This fundamental capability forms the backbone of the framework. By intercepting requests, users have the flexibility to route them to various components within the Burp Suite framework, which we will explore in upcoming sections. The ability to intercept, view, and modify web requests before they reach the target server or even manipulate responses before they are received by our browser makes Burp Suite an invaluable tool for manual web application testing.

Burp Suite is available in different editions. For our purposes, we will focus on the Burp Suite Community Edition, which is freely accessible for non-commercial use within legal boundaries. However, it's worth noting that Burp Suite also offers Professional and Enterprise editions, which come with advanced features and require licensing:

Burp Suite Professional is an unrestricted version of Burp Suite Community. It comes with features such as:

- An automated vulnerability scanner.

- A fuzzer/brute-forcer that isn't rate limited.

- Saving projects for future use and report generation.

- A built-in API to allow integration with other tools.

- Unrestricted access to add new extensions for greater functionality.

- Access to the Burp Suite Collaborator (effectively providing a unique request catcher self-hosted or running on a Portswigger-owned server).


In short, Burp Suite Professional is a highly potent tool, making it a preferred choice for professionals in the field.

Burp Suite Enterprise, in contrast to the community and professional editions, is primarily utilized for continuous scanning. It features an automated scanner that periodically scans web applications for vulnerabilities, similar to how tools like Nessus perform automated infrastructure scanning. Unlike the other editions, which allow manual attacks from a local machine, Burp Suite Enterprise resides on a server and constantly scans the target web applications for potential vulnerabilities.

<img width="1920" height="998" alt="image" src="https://github.com/user-attachments/assets/b759d7ff-b6fe-429e-8300-6e9a845dd17e" />

Due to requiring a license for the Professional and Enterprise editions, we will focus on the core feature set provided by the Burp Suite Community Edition.

Note: The provided demonstrations utilize Burp Suite for Windows. However, the functionality remains consistent with the version installed on the AttackBox.

**Answer the questions below**

1. _Which edition of Burp Suite runs on a server and provides constant scanning for target web apps?_

Answer: `Burp Suite Enterprise`

2. _Burp Suite is frequently used when attacking web applications and ______ applications._

Answer: `Mobile`

-----------------------------------------------------------------------------------------------------------------------------------------------

**Module 3: Features of Burp Community**

Although Burp Suite Community offers a more limited feature set compared to the Professional edition, it still provides an impressive array of tools that are highly valuable for web application testing. Let's explore some of the key features:

- **_Proxy_**: The Burp Proxy is the most renowned aspect of Burp Suite. It enables interception and modification of requests and responses while interacting with web applications.

- **_Repeater_**: Another well-known feature. [Repeater](https://tryhackme.com/room/burpsuiterepeater) allows for capturing, modifying, and resending the same request multiple times. This functionality is particularly useful when crafting payloads through trial and error (e.g., in SQLi - Structured Query Language Injection) or testing the functionality of an endpoint for vulnerabilities.

- **_Intruder_**: Despite rate limitations in Burp Suite Community, [Intruder](https://tryhackme.com/room/burpsuiteintruder) allows for spraying endpoints with requests. It is commonly utilized for brute-force attacks or fuzzing endpoints.

- **_Decoder_**: [Decoder](https://tryhackme.com/room/burpsuiteom) offers a valuable service for data transformation. It can decode captured information or encode payloads before sending them to the target. While alternative services exist for this purpose, leveraging Decoder within Burp Suite can be highly efficient.

- **_Comparer_**: As the name suggests, [Comparer](https://tryhackme.com/room/burpsuiteom) enables the comparison of two pieces of data at either the word or byte level. While not exclusive to Burp Suite, the ability to send potentially large data segments directly to a comparison tool with a single keyboard shortcut significantly accelerates the process.

- **_Sequencer_**: [Sequencer](https://tryhackme.com/room/burpsuiteom) is typically employed when assessing the randomness of tokens, such as session cookie values or other supposedly randomly generated data. If the algorithm used for generating these values lacks secure randomness, it can expose avenues for devastating attacks.

Beyond the built-in features, the Java codebase of Burp Suite facilitates the development of extensions to enhance the framework's functionality. These extensions can be written in Java, Python (using the Java Jython interpreter), or Ruby (using the Java JRuby interpreter). The Burp Suite Extender module allows for quick and easy loading of extensions into the framework, while the marketplace, known as the BApp Store, enables downloading of third-party modules. While certain extensions may require a professional license for integration, there are still a considerable number of extensions available for Burp Community. For instance, the Logger++ module can extend the built-in logging functionality of Burp Suite.

**Answer the questions below**

1. _Which Burp Suite feature allows us to intercept requests between ourselves and the target?_

Answer: `Proxy`

2. _Which Burp tool would we use to brute-force a login form?_

Answer: `Intruder`

-------------------------------------------------------------------------------------------------------------------------------------------------------------------


**Module 4: Installation**

Burp Suite is one of those tools that is very useful to have around, whether for web or mobile application assessments, pentesting, bug bounty hunting, or even debugging features in web app development. Here's a guide on installing Burp Suite on different platforms:

Note: If you use the AttackBox, Burp Suite is already installed, so you can skip this step.
Downloads

To download the latest version of Burp Suite for other systems, you may click this button to go to their download page.

Kali Linux: Burp Suite comes pre-installed with Kali Linux. In case it is missing on your Kali installation, you can easily install it from the Kali apt repositories.

Linux, macOS, and Windows: For other operating systems, PortSwigger provides dedicated installers for Burp Suite Community and Burp Suite Professional on the Burp Suite downloads page. Choose your operating system from the dropdown menu and select Burp Suite Community Edition. Then, click the Download button to initiate the download.

<img width="1208" height="556" alt="image" src="https://github.com/user-attachments/assets/28a8e399-7093-42fa-b1e1-37d44d77a1f4" />

Installation

Install Burp Suite using the appropriate method for your operating system. On Windows, run the executable file, while on Linux, execute the script from the terminal (with or without sudo). If you choose not to use sudo during installation on Linux, Burp Suite will be installed in your home directory at ~/BurpSuiteCommunity/BurpSuiteCommunity and will not be added to your PATH.

The installation wizard provides clear instructions, and it is generally safe to accept the default settings. However, it is always recommended to review the installer carefully.

With Burp Suite successfully installed, you can now launch the application. In the next task, we will explore the initial setup and configuration.

**Answer the questions below**

1. _If you have chosen not to use the AttackBox, ensure that you have a copy of Burp Suite installed before proceeding._

Answer: No answer needed

----------------------------------------------------------------------------------------------------------------------------------------------

**Module 5: The Dashboard**

You may use the pre-installed Burp Suite Community Edition in our AttackBox. To launch the AttackBox, click the Start AttackBox button at the top of this page.

Once you launch Burp Suite and accept the terms and conditions, you will be prompted to select a project type. In Burp Suite Community, the options are limited, and you can simply click Next to proceed.

The next window allows you to choose the configuration for Burp Suite. It is generally recommended to keep the default settings, which are suitable for most situations. Click Start Burp to open the main Burp Suite interface.

Upon opening Burp Suite for the first time, you might encounter a screen with training options. It is highly recommended to go through these training materials when you have the time.

If you don't see the training screen (or in subsequent sessions), you will be presented with the Burp Dashboard, which may seem overwhelming at first. However, it will soon become familiar.

The Burp Dashboard is divided into four quadrants, as labelled in counter-clockwise order starting from the top left:

<img width="1132" height="584" alt="image" src="https://github.com/user-attachments/assets/441a95e0-c678-483a-8709-6bf12fb0d89c" />


- **Tasks**: The Tasks menu allows you to define background tasks that Burp Suite will perform while you use the application. In Burp Suite Community, the default “Live Passive Crawl” task, which automatically logs the pages visited, is sufficient for our purposes in this module. Burp Suite Professional offers additional features like on-demand scans.

- **Event log**: The Event log provides information about the actions performed by Burp Suite, such as starting the proxy, as well as details about connections made through Burp.

- **Issue Activity**: This section is specific to Burp Suite Professional. It displays the vulnerabilities identified by the automated scanner, ranked by severity and filterable based on the certainty of the vulnerability.

- **Advisory**: The Advisory section provides more detailed information about the identified vulnerabilities, including references and suggested remediations. This information can be exported into a report. In Burp Suite Community, this section may not show any vulnerabilities.

Throughout the various tabs and windows of Burp Suite, you will notice question mark icons (<img width="30" height="26" alt="image" src="https://github.com/user-attachments/assets/e5e867d5-d7c8-4b99-9e58-41d3503b3a41" />)

Clicking on these icons opens a new window with helpful information specific to that section. These help icons are invaluable when you need assistance or clarification on a particular feature, so make sure to utilise them effectively.

<img width="1032" height="882" alt="image" src="https://github.com/user-attachments/assets/6a0a9fdc-fc9f-4731-876d-2942e3a5887e" />

By exploring the different tabs and functionalities of Burp Suite, you will gradually become familiar with its capabilities.

**Answer the questions below**

1. _What menu provides information about the actions performed by Burp Suite, such as starting the proxy, and details about connections made through Burp?_

Answer: `Event log`

----------------------------------------------------------------------------------------------------------------------------------------------

**Module 6: Navigation**

In Burp Suite, the default navigation is primarily done through the top menu bars, which allow you to switch between modules and access various sub-tabs within each module. The sub-tabs appear in a second menu bar directly below the main menu bar.

Here's how the navigation works:

1. **_Module Selection_**: The top row of the menu bar displays the available modules in Burp Suite. You can click on each module to switch between them. For example, the Burp Proxy module is selected in the image below.

    <img width="1102" height="50" alt="image" src="https://github.com/user-attachments/assets/6f76aa25-2e85-442a-941a-a38e396a8bdf" />

2. **_Sub-Tabs:_** If a selected module has multiple sub-tabs, they can be accessed through the second menu bar that appears directly below the main menu bar. These sub-tabs often contain module-specific settings and options. For example, in the image above, the Proxy Intercept sub-tab is selected within the Burp Proxy module.

3. _**Detaching Tabs:**_ If you prefer to view multiple tabs separately, you can detach them into separate windows. To do this, go to the Window option in the application menu above the Module Selection bar. From there, choose the "Detach" option, and the selected tab will open in a separate window. The detached tabs can be reattached using the same method.

<img width="169" height="326" alt="image" src="https://github.com/user-attachments/assets/3555e3d6-d2bf-431d-9109-2d0f75a03286" />

Burp Suite also provides keyboard shortcuts for quick navigation to key tabs. By default, the following shortcuts are available:

| Shortcut             | Tab          |
|----------------------|--------------|
| `Ctrl + Shift + D`   | Dashboard    |
| `Ctrl + Shift + T`   | Target tab   |
| `Ctrl + Shift + P`   | Proxy tab    |
| `Ctrl + Shift + I`   | Intruder tab |
| `Ctrl + Shift + R`   | Repeater tab |


**Answer the questions below**

1. _Which tab Ctrl + Shift + P will switch us to?_

Answer: `Proxy tab`

----------------------------------------------------------------------------------------------------------------------------------------------

**Module 7: Options**

Before diving into the Burp Proxy, let's explore the available options for configuring Burp Suite. There are two types of settings: Global settings (also known as User settings) and Project settings.

- **_Global Settings_**: These settings affect the entire Burp Suite installation and are applied every time you start the application. They provide a baseline configuration for your Burp Suite environment.

- **_Project Settings_**: These settings are specific to the current project and apply only during the session. However, please note that Burp Suite Community Edition does not support saving projects, so any project-specific options will be lost when you close Burp.

To access the settings, click on the Settings button in the top navigation bar. This will open a separate settings window.

<img width="1109" height="61" alt="image" src="https://github.com/user-attachments/assets/85f74244-db71-4737-96b0-89cf813fb6a0" />

Below is the image showing the separate settings window.

<img width="1346" height="755" alt="image" src="https://github.com/user-attachments/assets/1b0140f9-f1cb-4b0c-b2f8-fd12ffefc438" />

In the Settings window, you will find a menu on the left-hand side. This menu allows you to switch between different types of settings, including:

1. **_Search_**: Enables searching for specific settings using keywords.

2. **_Type filter_**: Filters the settings for User and Project options.

   - User settings: Shows settings that affect the entire Burp Suite installation.

   - Project settings: Displays settings specific to the current project.

3. **_Categories_**: Allows selecting settings by category.

<img width="1253" height="747" alt="image" src="https://github.com/user-attachments/assets/0ed10c98-2ef2-4641-998a-1a8613b6ab8f" />

It's worth noting that many tools within Burp Suite provide shortcuts to specific categories of settings. For example, the Proxy module includes a Proxy settings button that opens the settings window directly to the relevant proxy section.

<img width="487" height="54" alt="image" src="https://github.com/user-attachments/assets/c9914f7e-1afb-46c9-a01f-6934625315b8" />

The search feature on the settings page is a valuable addition, allowing you to quickly search for settings using keywords.

Take some time to familiarise yourself with the range of configurable options in Burp Suite. Once you are comfortable, you can proceed with the exercises related to configuring Burp Suite settings.

**Answer the questions below**

1. _In which category can you find a reference to a "Cookie jar"?_

Answer: `Sessions`

**_Explanation:_**

We click on Settings Gear on the right side and now we search for `Cookie jar` and we see the left pane showing "Sessions"

<img width="1375" height="674" alt="image" src="https://github.com/user-attachments/assets/e9c42930-304c-4d22-bfaa-7f434bbb0971" />


2. _In which base category can you find the "Updates" sub-category, which controls the Burp Suite update behaviour?_

Answer: `Suite`

**_Explanation:_**

We search for `Updates` and we see it is part of "Suite"

<img width="1378" height="324" alt="image" src="https://github.com/user-attachments/assets/99af75b0-4930-490b-b216-a5f42a3ae384" />

3. _What is the name of the sub-category which allows you to change the keybindings for shortcuts in Burp Suite?_

Answer: `Hotkeys`

**_Explanation:_**

We go to the menu `User Interface` -> `HotKeys` and we can see it is capable of changing the shortcuts

<img width="1383" height="794" alt="image" src="https://github.com/user-attachments/assets/22dfc8cf-fcf0-4f6c-a6ac-98c3ab4281fd" />


4. _If we have uploaded Client-Side TLS certificates, can we override these on a per-project basis (yea/nay)?_

Answer: `yea`

**_Explanation:_**

We search "Client TLS" and we can see there's a toggle to override TLS options for this project. So the answer is "yea" 

<img width="1386" height="517" alt="image" src="https://github.com/user-attachments/assets/e1f97389-ffab-4f7a-9099-cf866edc38de" />

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Module 8: Introduction to the Burp Proxy**

The Burp Proxy is a fundamental and crucial tool within Burp Suite. It enables the capture of requests and responses between the user and the target web server. This intercepted traffic can be manipulated, sent to other tools for further processing, or explicitly allowed to continue to its destination.
Key Points to Understand About the Burp Proxy

- **_Intercepting Requests_**: When requests are made through the Burp Proxy, they are intercepted and held back from reaching the target server. The requests appear in the Proxy tab, allowing for further actions such as forwarding, dropping, editing, or sending them to other Burp modules. To disable the intercept and allow requests to pass through the proxy without interruption, click the Intercept is on button.

<img width="823" height="437" alt="image" src="https://github.com/user-attachments/assets/4ca28505-31db-4e27-9f61-8cb637fac316" />

- **_Taking Control**_: The ability to intercept requests empowers testers to gain complete control over web traffic, making it invaluable for testing web applications. 

- **_Capture and Logging:_** Burp Suite captures and logs requests made through the proxy by default, even when the interception is turned off. This logging functionality can be helpful for later analysis and review of prior requests.

- _**WebSocket Support:**_ Burp Suite also captures and logs WebSocket communication, providing additional assistance when analysing web applications.

- _**Logs and History:**_ The captured requests can be viewed in the HTTP history and WebSockets history sub-tabs, allowing for retrospective analysis and sending the requests to other Burp modules as needed.

<img width="1111" height="309" alt="image" src="https://github.com/user-attachments/assets/25b9f685-da2a-438f-a6ff-43241e2da6fc" />

Proxy-specific options can be accessed by clicking the Proxy settings button. These options provide extensive control over the Proxy’s behaviour and functionality. Familiarise yourself with these options to optimize your Burp Proxy usage.

**Some Notable Features in the Proxy Settings**

- **_Response Interception_**: By default, the proxy does not intercept server responses unless explicitly requested on a per-request basis. The "Intercept responses based on the following rules" checkbox, along with the defined rules, allows for a more flexible response interception.

<img width="859" height="287" alt="image" src="https://github.com/user-attachments/assets/1dd2b8e8-50f0-412b-89c9-1dc26bdf2200" />

- **_Match and Replace_** : The "Match and Replace" section in the Proxy settings enables the use of regular expressions (regex) to modify incoming and outgoing requests. This feature allows for dynamic changes, such as modifying the user agent or manipulating cookies.

Take the time to explore and experiment with the Proxy options, as this will enhance your understanding and proficiency with the tool.

**Answer the questions below**

1. _Click me to proceed to the next task._

Answer: No answer needed

--------------------------------------------------------------------------------------------------------------------------------------------

**Module 9: Connecting through the Proxy (FoxyProxy)**

To use the Burp Suite Proxy, we need to configure our local web browser to redirect traffic through Burp Suite. In this task, we will focus on configuring the proxy using the FoxyProxy extension in Firefox.

Please note that the instructions provided are specific to Firefox. If you are using a different browser, you may need to find alternative methods or use the TryHackMe AttackBox.

Here are the steps to configure the Burp Suite Proxy with FoxyProxy:

1. Install FoxyProxy: Download and install the [FoxyProxy Basic extension](https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-basic/).

    Note: FoxyProxy is already installed on the AttackBox.

2. Access FoxyProxy Options: Once installed, a button will appear at the top right of the Firefox browser. Click on the FoxyProxy button to access the FoxyProxy options pop-up.

<img width="364" height="181" alt="image" src="https://github.com/user-attachments/assets/2c327745-28e9-4c57-b811-8934995dce91" />

3. Create Burp Proxy Configuration: In the FoxyProxy options pop-up, click the Options button. This will open a new browser tab with the FoxyProxy configurations. Click the Add button to create a new proxy configuration.

<img width="903" height="515" alt="image" src="https://github.com/user-attachments/assets/502faae1-c2aa-4d92-b1b7-9e700e9b526a" />


4. Add Proxy Details: On the "Add Proxy" page, fill in the following values:

- Title: Burp (or any preferred name)

- Proxy IP: 127.0.0.1

- Port: 8080

<img width="869" height="537" alt="image" src="https://github.com/user-attachments/assets/b238801a-d5cd-4763-829b-54f3ae863fcc" />

5. Save Configuration: Click Save to save the Burp Proxy configuration.

6. Activate Proxy Configuration: Click on the FoxyProxy icon at the top-right of the Firefox browser and select the Burp configuration. This will redirect your browser traffic through 127.0.0.1:8080. Note that Burp Suite must be running for your browser to make requests when this configuration is activated.

<img width="369" height="181" alt="image" src="https://github.com/user-attachments/assets/538e0f01-498d-4c39-8e67-d11eb7984617" />

7. Enable Proxy Intercept in Burp Suite: Switch to Burp Suite and ensure that Intercept is turned on in the Proxy tab.

<img width="558" height="114" alt="image" src="https://github.com/user-attachments/assets/7a435adf-9b7e-48c6-af07-9f62cea9424a" />


8. Test the Proxy: Open Firefox and try accessing a website, such as the homepage for http://MACHINE_IP/. Your browser will hang, and the proxy will populate with the HTTP request. Congratulations, you have successfully intercepted your first request!

Remember the following:

- When the proxy configuration is active, and the intercept is switched on in Burp Suite, your browser will hang whenever you make a request.

- Be cautious not to leave the intercept switched on unintentionally, as it can prevent your browser from making any requests.

- Right-clicking on a request in Burp Suite allows you to perform various actions, such as forwarding, dropping, sending to other tools, or selecting options from the right-click menu.

Take note of these details as you begin using the Burp Suite Proxy.

Note: Consider closing the other tabs in the AttackBox browser before enabling interception, as you will receive some WebSocket requests instead of request from the target VM.

**Answer the questions below**

1. _Click me to proceed to the next task._

Answer: No answer needed

--------------------------------------------------------------------------------------------------------------------------------------------


**Module 10: Site Map and Issue Definitions**

The Target tab in Burp Suite provides more than just control over the scope of our testing. It consists of three sub-tabs:

- **_Site map_**: This sub-tab allows us to map out the web applications we are targeting in a tree structure. Every page that we visit while the proxy is active will be displayed on the site map. This feature enables us to automatically generate a site map by simply browsing the web application. In Burp Suite Professional, we can also use the site map to perform automated crawling of the target, exploring links between pages and mapping out as much of the site as possible. Even with Burp Suite Community, we can still utilize the site map to accumulate data during our initial enumeration steps. It is particularly useful for mapping out APIs, as any API endpoints accessed by the web application will be captured in the site map.

- **_Issue definitions_**: Although Burp Community does not include the full vulnerability scanning functionality available in Burp Suite Professional, we still have access to a list of all the vulnerabilities that the scanner looks for. The Issue definitions section provides an extensive list of web vulnerabilities, complete with descriptions and references. This resource can be valuable for referencing vulnerabilities in reports or assisting in describing a particular vulnerability that may have been identified during manual testing.

- **_Scope settings_**: This setting allows us to control the target scope in Burp Suite. It enables us to include or exclude specific domains/IPs to define the scope of our testing. By managing the scope, we can focus on the web applications we are specifically targeting and avoid capturing unnecessary traffic.

<img width="1911" height="125" alt="image" src="https://github.com/user-attachments/assets/04b7af6c-b185-4745-aa06-6a99882df13a" />

Overall, the Target tab offers features beyond scoping, allowing us to map out web applications, fine-tune our target scope, and access a comprehensive list of web vulnerabilities for reference purposes.

**Challenge**

Take a look around the site on http://MACHINE IP/ — we will be using this a lot throughout the module. Visit every other page that is linked on the homepage, then check your sitemap — one endpoint should stand out as being very unusual! 

Visit this in your browser (or use the "Response" section of the site map entry for that endpoint)

**Answer the questions below**

1. _What is the flag you receive after visiting the unusual endpoint?_

Answer: `THM{NmNlZTliNGE1MWU1ZTQzMzgzNmFiNWVk}`

**_Explanation:_**

On BurpSuite we open the broswer and enter our victim IP

<img width="844" height="179" alt="image" src="https://github.com/user-attachments/assets/199af86f-142c-4329-9076-9319917bc1ac" />

We browse through all the pages and on site map we see something like `/5yjR2GLcoGoij2ZK` 

<img width="1917" height="992" alt="image" src="https://github.com/user-attachments/assets/5767d2c4-090c-406e-b823-658355679bdf" />

We copy the URL and then paste it on the browser and find the flag

<img width="847" height="222" alt="image" src="https://github.com/user-attachments/assets/bc1b3ee0-a92a-43df-b24b-e39dfe29a06a" />
<img width="459" height="152" alt="image" src="https://github.com/user-attachments/assets/bda98a6d-bdb9-4854-bf70-190ae6248324" />

--------------------------------------------------------------------------------------------------------------------------------------------

**Module 11: The Burp Suite Browser**

If the previous tasks seemed overly complex, rest assured, this topic will be a lot simpler.

In addition to modifying our regular web browser to work with the proxy, Burp Suite also includes a built-in Chromium browser that is pre-configured to use the proxy without any of the modifications we just had to do.

To start the Burp Browser, click the Open Browser button in the proxy tab. A Chromium window will pop up, and any requests made in this browser will go through the proxy.

<img width="593" height="116" alt="image" src="https://github.com/user-attachments/assets/980618cf-109d-4c31-8afb-664b1271f9c9" />

Note: There are many settings related to the Burp Browser in the project options and user options settings. Make sure to explore and customise them as needed.

However, if you are running Burp Suite on Linux as the root user (as is the case with the AttackBox), you may encounter an error preventing the Burp Browser from starting due to the inability to create a sandbox environment.

There are two simple solutions to this:

- Smart option: Create a new user and run Burp Suite under a low-privilege account to allow the Burp Browser to run without issues.

- Easy option: Go to Settings -> Tools -> Burp's browser and check the Allow Burp's browser to run without a sandbox option. Enabling this option will allow the browser to start without a sandbox. However, please be aware that this option is disabled by default for security reasons. If you choose to enable it, exercise caution, as compromising the browser could grant an attacker access to your entire machine. In the training environment of the AttackBox, this is unlikely to be a significant issue, but use it responsibly.

**Answer the questions below**

1. _Click me to proceed to the next task._

Answer: No answer needed

--------------------------------------------------------------------------------------------------------------------------------------------

**Module 12: Scoping and Targeting**

Finally, we come to one of the most important aspects of using the Burp Proxy: Scoping.

Capturing and logging all of the traffic can quickly become overwhelming and inconvenient, especially when we only want to focus on specific web applications. This is where scoping comes in.

By setting a scope for the project, we can define what gets proxied and logged in Burp Suite. We can restrict Burp Suite to target only the specific web application(s) we want to test. The easiest way to do this is by switching to the Target tab, right-clicking on our target from the list on the left, and selecting Add To Scope. Burp will then prompt us to choose whether we want to stop logging anything that is not in scope, and in most cases, we want to select yes.

To check our scope, we can switch to the Scope settings sub-tab within the Target tab.

The Scope settings window allows us to control our target scope by including or excluding domains/IPs. This section is powerful and worth spending time getting familiar with.

However, even if we disabled logging for out-of-scope traffic, the proxy will still intercept everything. To prevent this, we need to go to the Proxy settings sub-tab and select And URL Is in target scope from the "Intercept Client Requests" section.

<img width="1265" height="811" alt="image" src="https://github.com/user-attachments/assets/f9909568-4f98-487f-8f94-f42a86a736d3" />

Enabling this option ensures that the proxy completely ignores any traffic that is not within the defined scope, resulting in a cleaner traffic view in Burp Suite.

**Answer the questions below**

1. _Add http://MACHINE IP to your scope and change the proxy settings to only intercept traffic to in-scope targets._

Answer: No answer needed

--------------------------------------------------------------------------------------------------------------------------------------------

**Module 13: Proxying HTTPS**

Note: The AttackBox is already configured to solve the problem posed in this task. If you use the AttackBox and don't wish to read through the information here, you can skip to the next task.

When intercepting HTTP traffic, we may encounter an issue when navigating to sites with TLS enabled. For example, when accessing a site like https://google.com/, we may receive an error indicating that the PortSwigger Certificate Authority (CA) is not authorised to secure the connection. This happens because the browser does not trust the certificate presented by Burp Suite.

<img width="895" height="502" alt="image" src="https://github.com/user-attachments/assets/4abb548f-1e0e-463e-ba25-a8fa4d129ae2" />

To overcome this issue, we can manually add the PortSwigger CA certificate to our browser's list of trusted certificate authorities. Here's how to do it:

- Download the CA Certificate: With the Burp Proxy activated, navigate to http://burp/cert. This will download a file called cacert.der. Save this file somewhere on your machine.


- Access Firefox Certificate Settings: Type about:preferences into your Firefox URL bar and press Enter. This will take you to the Firefox settings page. Search the page for "certificates" and click on the View Certificates button.

<img width="706" height="351" alt="image" src="https://github.com/user-attachments/assets/4e209d3d-ab28-4a2f-a441-cb5d4a5729cd" />

- Import the CA Certificate: In the Certificate Manager window, click on the Import button. Select the cacert.der file that you downloaded in the previous step.

- Set Trust for the CA Certificate: In the subsequent window that appears, check the box that says "Trust this CA to identify websites" and click OK.

<img width="678" height="303" alt="image" src="https://github.com/user-attachments/assets/e64771a5-8da3-4fcb-8291-f40a8175d965" />

By completing these steps, we have added the PortSwigger CA certificate to our list of trusted certificate authorities. Now, we should be able to visit any TLS-enabled site without encountering the certificate error.

By following these instructions, you can ensure that your browser trusts the PortSwigger CA certificate and securely communicates with TLS-enabled websites through the Burp Suite Proxy.

**Answer the questions below**

1. _If you are not using the AttackBox, configure Firefox (or your browser of choice) to accept the PortSwigger CA certificate for TLS communication through the Burp Proxy._

Answer: No answer needed

--------------------------------------------------------------------------------------------------------------------------------------------

**Module 14: Example Attack**

Having looked at how to set up and configure our proxy, let's go through a simplified real-world example.

We will start by taking a look at the support form at http://MACHINE IP/ticket/:

<img width="623" height="388" alt="image" src="https://github.com/user-attachments/assets/a86b150d-1617-4a52-ab4c-53d298ee9405" />

In a real-world web app pentest, we would test this for a variety of things, one of which would be Cross-Site Scripting (or XSS). If you have not yet encountered XSS, it can be thought of as injecting a client-side script (usually in Javascript) into a webpage in such a way that it executes. There are various kinds of XSS – the type that we are using here is referred to as "Reflected" XSS, as it only affects the person making the web request.

**Walkthrough**

Try typing: `<script>alert("Succ3ssful XSS")</script>`, into the "Contact Email" field. You should find that there is a client-side filter in place which prevents you from adding any special characters that aren't allowed in email addresses:

Fortunately for us, client-side filters are absurdly easy to bypass. There are a variety of ways we could disable the script or just prevent it from loading in the first place.

Let's focus on simply bypassing the filter for now.

First, make sure that your Burp Proxy is active and that intercept is on.

Now, enter some legitimate data into the support form. For example: "pentester@example.thm" as an email address, and "Test Attack" as a query.

Submit the form — the request should be intercepted by the proxy.

With the request captured in the proxy, we can now change the email field to be our very simple payload from above: `<script>alert("Succ3ssful XSS")</script>`. After pasting in the payload, we need to select it, then URL encode it with the Ctrl + U shortcut to make it safe to send. 

Finally, press the "Forward" button to send the request.

You should find an alert box from the site indicating a successful XSS attack!

<img width="838" height="646" alt="image" src="https://github.com/user-attachments/assets/48fed828-6b40-46fa-8f41-6e4c69577373" />

<img width="1920" height="1039" alt="image" src="https://github.com/user-attachments/assets/40308332-2242-41a5-a817-e9b817710f1b" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7169b019-6c2f-4ac4-a08d-1f3ee2db04ea" />


<img width="847" height="293" alt="image" src="https://github.com/user-attachments/assets/69d7ae26-3312-4ebd-816f-163efed5456f" />

**Answer the questions below**

1. _Click me to proceed to the next task._

Answer: No answer needed

--------------------------------------------------------------------------------------------------------------------------------------------

**Module 15: Conclusion**

Congratulations on completing the Burp Basics room! You now have a solid understanding of the Burp Suite interface, configuration options, and the Burp Proxy. These skills will be essential as you continue your journey in web and mobile application penetration testing.

To further enhance your skills, I encourage you to practice and experiment with Burp Suite. Explore its features, try different configurations, and familiarise yourself with its various tools. The more you use Burp Suite, the more proficient you will become in identifying and exploiting vulnerabilities in web applications.

In the next room of the module, we will dive deeper into [Burp Suite Repeater](https://tryhackme.com/room/burpsuiterepeater), another powerful tool for manual testing and manipulation of web application requests. Stay curious and keep learning!

Stay curious and keep learning!

**Answer the questions below**

1. _I understand the fundamentals of using Burp Suite!_

Answer: No answer needed

--------------------------------------------------------------------------------------------------------------------------------------------

