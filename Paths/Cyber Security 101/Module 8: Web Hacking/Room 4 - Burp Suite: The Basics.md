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




