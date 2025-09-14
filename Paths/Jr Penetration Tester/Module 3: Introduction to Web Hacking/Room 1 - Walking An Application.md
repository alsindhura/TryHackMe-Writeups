Link: https://tryhackme.com/room/walkinganapplication (Premium Room)

<img width="1200" height="1200" alt="image" src="https://github.com/user-attachments/assets/620694b1-61d9-4775-8d9a-3a0e4592e8ba" />

Manually review a web application for security issues using only your browsers developer tools. Hacking with just your browser, no tools or scripts.

**Task 1: Walking An Application**

<img width="444" height="310" alt="image" src="https://github.com/user-attachments/assets/5ff61cfb-bdc1-466f-909d-f54d2ad4b9f1" />

In this room you will learn how to manually review a web application for security issues using only the in-built tools in your browser. More often than not, automated security tools and scripts will miss many potential vulnerabilities and useful information.


Here is a short breakdown of the in-built browser tools you will use throughout this room:

- **_View Source_** - Use your browser to view the human-readable source code of a website.

- **_Inspector_** - Learn how to inspect page elements and make changes to view usually blocked content.

- **_Debugger_** - Inspect and control the flow of a page's JavaScript

- **_Network_** - See all the network requests a page makes.

Press the "Start Machine" button to start the virtual machine on this task, then wait 2 minutes, and visit the following URL: https://LAB_WEB_URL.p.thmlabs.com (this URL will update 2 minutes from when you start the machine)

**Answer the questions below**

1. _I confirm that I have deployed the virtual machine and opened the website._

Answer: No answer needed

---

**Task 2: Exploring The Website**

As a penetration tester, your role when reviewing a website or web application is to discover features that could potentially be vulnerable and attempt to exploit them to assess whether or not they are. These features are usually parts of the website that require some interactivity with the user.

Finding interactive portions of the website can be as easy as spotting a login form to manually reviewing the website's JavaScript. An excellent place to start is just with your browser exploring the website and noting down the individual pages/areas/features with a summary for each one.

An example site review for the Acme IT Support website would look something like this:

| Feature               | URL                          | Summary                                                                                         |
|-----------------------|-------------------------------|-------------------------------------------------------------------------------------------------|
| Home Page             | `/`                           | This page contains a summary of what Acme IT Support does with a company photo of their staff. |
| Latest News           | `/news`                       | This page contains a list of recently published news articles with links like `/news/article?id=1`. |
| News Article          | `/news/article?id=1`          | Displays the individual news article. Some articles are restricted to premium customers.        |
| Contact Page          | `/contact`                    | A form for contacting the company with name, email, and message input fields, and a send button. |
| Customers             | `/customers`                  | Redirects to `/customers/login`.                                                                |
| Customer Login        | `/customers/login`            | Login form with username and password fields.                                                   |
| Customer Signup       | `/customers/signup`           | Signup form with username, email, password, and confirmation fields.                            |
| Customer Reset Password | `/customers/reset`          | Password reset form with an email address input field.                                          |
| Customer Dashboard    | `/customers`                  | Shows user's submitted tickets and a "Create Ticket" button.                                    |
| Create Ticket         | `/customers/ticket/new`       | Form with a textbox for IT issues and a file upload option to create a support ticket.          |
| Customer Account      | `/customers/account`          | Allows user to edit their username, email, and password.                                        |
| Customer Logout       | `/customers/logout`           | Logs the user out of the customer area.                                                         |

We will start taking a deeper look into some of the pages we have discovered in the next task.

**Answer the questions below**

1. _Read the above._

Answer: No answer needed

---

**Task 3: Viewing The Page Source**

The page source is the human-readable code returned to our browser/client from the web server each time we make a request.

The returned code is made up of HTML ( HyperText Markup Language), CSS ( Cascading Style Sheets ) and JavaScript, and it's what tells our browser what content to display, how to show it and adds an element of interactivity with JavaScript.

For our purposes, viewing the page source can help us discover more information about the web application.

**How do I view the Page Source?**

- While viewing a website, you can right-click on the page, and you'll see an option on the menu that says View Page Source.

- Most browsers support putting view-source: in front of the URL for example, view-source:https://www.google.com/

- In your browser menu, you'll find an option to view the page source. This option can sometimes be in submenus such as developer tools or more tools.

**Let's view some Page Source!**

Try viewing the page source of the home page of the Acme IT Support website. Unfortunately, explaining everything you can see here is well out of the scope of this room, and you'll need to look into website design/development courses to understand it fully. What we can do, is pick out bits of information that are of importance to us.

At the top of the page, you'll notice some code starting with <!-- and ending with --> these are comments. Comments are messages left by the website developer, usually to explain something in the code to other programmers or even notes/reminders for themselves. These comments don't get displayed on the actual webpage. This comment describes how the homepage is temporary while a new one is in development. View the webpage in the comment to get your first flag.

Links to different pages in HTML are written in anchor tags ( these are HTML elements that start with <a ), and the link that you'll be directed to is stored in the href attribute.

For example, you'll see the contact page link on line 31:

<img width="555" height="137" alt="image" src="https://github.com/user-attachments/assets/287261ff-8c8e-4a22-8c1c-31f1b4652dde" />

If you view further down the page source, there is a hidden link to a page starting with "secr", view this link to get another flag. You obviously wouldn't get a flag in a real-world situation, but you may discover some private area used by the business for storing company/staff/customer information.

External files such as CSS, JavaScript and Images can be included using the HTML code. In this example, you'll notice that these files are all stored in the same directory. If you view this directory in your web browser, there is a configuration error. What should be displayed is either a blank page or a 403 Forbidden page with an error stating you don't have access to the directory. Instead, the directory listing feature has been enabled, which in fact, lists every file in the directory. Sometimes this isn't an issue, and all the files in the directory are safe to be viewed by the public, but in some instances, backup files, source code or other confidential information could be stored here. In this instance, we get a flag in the flag.txt file.

Many websites these days aren't made from scratch and use what's called a framework. A framework is a collection of premade code that easily allows a developer to include common features that a website would require, such as blogs, user management, form processing, and much more, saving the developers hours or days of development.

Viewing the page source can often give us clues into whether a framework is in use and, if so, which framework and even what version. Knowing the framework and version can be a powerful find as there may be public vulnerabilities in the framework, and the website might not be using the most up to date version. At the bottom of the page, you'll find a comment about the framework and version in use and a link to the framework's website. Viewing the framework's website, you'll see that our website is, in fact, out of date. Read the update notice and use the information that you find to discover another
flag.

**Answer the questions below**

1. _Answer the questions below_

Answer: `THM{HTML_COMMENTS_ARE_DANGEROUS}`

**_Explanation:_**

First we visit _MACHINE_IP_ and Press `Ctrl+Shift+I` and we can see the dev tools

<img width="1920" height="996" alt="image" src="https://github.com/user-attachments/assets/d6950dbd-ecfd-45b9-bb02-40c2fba0091c" />

We see a comment like this `This page is temporary while we work on the new homepage @ /new-home-beta`

<img width="1135" height="444" alt="image" src="https://github.com/user-attachments/assets/8a7d9129-28cd-4f42-8c21-d6ccfcf8fdff" />

Now we visit `MACHINE_IP/new-home-beta` and get the flag

<img width="411" height="62" alt="image" src="https://github.com/user-attachments/assets/3c27f091-75b0-48e0-a87e-cff64333d8e6" />


2. _What is the flag from the secret link?_

Answer: `THM{NOT_A_SECRET_ANYMORE}`

**_Explanation:_**

We go through the page source code and see a href called `/secret-page`

<img width="1125" height="506" alt="image" src="https://github.com/user-attachments/assets/78646ed6-fce7-4843-b6bb-28d22b989bf1" />

Now we visit `MACHINE_IP/secret-page` and get the flag

<img width="298" height="53" alt="image" src="https://github.com/user-attachments/assets/31daf806-3c76-4c67-b286-8abdd0831383" />

3. _What is the directory listing flag?_

Answer: `THM{INVALID_DIRECTORY_PERMISSIONS}`

**_Explanation:_**

We visit `MACHINE_IP/assets` and find a file named "flag.txt"

<img width="714" height="313" alt="image" src="https://github.com/user-attachments/assets/05445079-15e2-4a3b-9746-14df3b2ca364" />

Now we open this file to find the flag

<img width="291" height="71" alt="image" src="https://github.com/user-attachments/assets/4837dfd7-3bc6-45b0-8a3c-5149f6601952" />

4. _What is the framework flag?_

Answer: `THM{KEEP_YOUR_SOFTWARE_UPDATED}`

**_Explanation:_**

We see the framework as shown below

<img width="1131" height="477" alt="image" src="https://github.com/user-attachments/assets/e46fe626-95e0-48ac-80ff-e25261949668" />

Now we visit `https://static-labs.tryhackme.cloud/sites/thm-web-framework`

<img width="1920" height="472" alt="image" src="https://github.com/user-attachments/assets/ddf07885-518d-4574-a7fa-a47f08487ec2" />

Now we read through the site and in the section 'Change Log' we find a sentence `We've had an issue where our backup process was creating a file in the web directory called /tmp.zip`

<img width="1920" height="545" alt="image" src="https://github.com/user-attachments/assets/bdf4fc82-e3ad-4984-8dd1-4859228ff0fe" />

Now we type `MACHINE_IP/tmp.zip` and a zip file will be downloaded and after extracting and we can see a flag.txt file with the flag inside

<img width="1877" height="694" alt="email" src="https://github.com/user-attachments/assets/66b6fb69-9704-49d0-b57f-f67f8e8e9def" />

<img width="602" height="499" alt="image" src="https://github.com/user-attachments/assets/28d383ed-4798-4ff5-b676-6fee121e4fa2" />

<img width="281" height="50" alt="image" src="https://github.com/user-attachments/assets/70252e50-a8c6-4c1d-ad59-526a06e44136" />

---

**Task 4: Developer Tools - Inspector**

**Developer Tools**

Every modern browser includes developer tools; this is a tool kit used to aid web developers in debugging web applications and gives you a peek under the hood of a website to see what is going on. As a pentester, we can leverage these tools to provide us with a much better understanding of the web application. We're specifically focusing on three features of the developer tool kit, Inspector, Debugger and Network.

**Opening Developer Tools**

The way to access developer tools is different for every browser. If you're not sure how to access it, click the "View Site" button on the top right of this task to get instructions to how to access the tools for your browser.

**Inspector**

The page source doesn't always represent what's shown on a webpage; this is because CSS, JavaScript and user interaction can change the content and style of the page, which means we need a way to view what's been displayed in the browser window at this exact time. Element inspector assists us with this by providing us with a live representation of what is currently on the website.

As well as viewing this live view, we can also edit and interact with the page elements, which is helpful for web developers to debug issues.

On the Acme IT Support website, click into the news section, where you'll see three news articles.

The first two articles are readable, but the third has been blocked with a floating notice above the content stating you have to be a premium customer to view the article. These floating boxes blocking the page contents are often referred to as paywalls as they put up a metaphorical wall in front of the content you wish to see until you pay.

<img width="810" height="459" alt="image" src="https://github.com/user-attachments/assets/21a40384-7e12-4245-9e30-63f3f29c1868" />

Right-clicking on the premium notice ( paywall ), you should be able to select the Inspect option from the menu, which opens the developer tools either on the bottom or right-hand side depending on your browser or preferences. You'll now see the elements/HTML that make up the website ( similar to the screenshots below ).

<img width="540" height="333" alt="image" src="https://github.com/user-attachments/assets/8328d661-e6ed-4231-b89d-9c6b62ffe5bd" />

Locate the DIV element with the class premium-customer-blocker and click on it. You'll see all the CSS styles in the styles box that apply to this element, such as margin-top: 60px and text-align: center. The style we're interested in is the display: block. If you click on the word block, you can type a value of your own choice. Try typing none, and this will make the box disappear, revealing the content underneath it and a flag. If the element didn't have a display field, you could click below the last style and add in your own. Have a play with the element inspector, and you'll see you can change any of the information on the website, including the content. Remember this is only edited on your browser window, and when you press refresh, everything will be back to normal.

**Answer the questions below**

1. _What is the flag behind the paywall?_

Answer: `THM{NOT_SO_HIDDEN}`

**_Explanation:_**

We visit `http://MACHINE_IP/news` and click on the third news article

<img width="1130" height="391" alt="image" src="https://github.com/user-attachments/assets/6a9d7485-57ce-4c4c-b5e3-30ad5900cdc7" />

And we see something like this

<img width="1114" height="698" alt="image" src="https://github.com/user-attachments/assets/11ee5891-5424-4037-8b41-d36611484442" />

We open dev tools and change the `display` from `block` to `none`

<img width="835" height="448" alt="image" src="https://github.com/user-attachments/assets/1e7b6fe6-f068-4446-86c7-b310a9c563a2" />
<img width="833" height="354" alt="image" src="https://github.com/user-attachments/assets/2fd4340a-45ba-420f-8093-304a3a0ca090" />

Now we can see the flag

<img width="1070" height="590" alt="image" src="https://github.com/user-attachments/assets/16578eed-64da-4ffc-8a4f-89fc5c6f8168" />

---

**TASK 5: Developer Tools - Debugger**

**Developer Tools - Debugger**


This panel in the developer tools is intended for debugging JavaScript, and again is an excellent feature for web developers wanting to work out why something might not be working. But as penetration testers, it gives us the option of digging deep into the JavaScript code. In Firefox and Safari, this feature is called Debugger, but in Google Chrome, it's called Sources.


On the Acme IT Support website, click on the contact page, each time the page is loaded, you might notice a rapid flash of red on the screen. We're going to use the Debugger to work out what this red flash is and if it contains anything interesting. Debugging a red dot wouldn't be something you'd do in the real world as a penetration tester, but it does allow us to use this feature and get used to the Debugger.


In both browsers, on the left-hand side, you see a list of all the resources the current webpage is using. If you click into the assets folder, you'll see a file named flash.min.js. Clicking on this file displays the contents of the JavaScript file.


Many times when viewing javascript files, you'll notice that everything is on one line, which is because it has been minimised, which means all formatting ( tabs, spacing and newlines ) have been removed to make the file smaller. This file is no exception to this, and it has also been obfusticated, which makes it purposely difficult to read, so it can't be copied as easily by other developers.


We can return some of the formattings by using the "Pretty Print" option, which looks like two braces { } to make it a little more readable, although due to the obfustication, it's still difficult to comprehend what is going on with the file. If you scroll to the bottom of the flash.min.js file, you'll see the line: flash['remove']();

<img width="1174" height="525" alt="image" src="https://github.com/user-attachments/assets/6a206177-0d7c-4580-9985-a88c50b51f36" />

This little bit of JavaScript is what is removing the red popup from the page. We can utilise another feature of debugger called breakpoints. These are points in the code that we can force the browser to stop processing the JavaScript and pause the current execution.


If you click the line number that contains the above code, you'll notice it turns blue; you've now inserted a breakpoint on this line. Now try refreshing the page, and you'll notice the red box stays on the page instead of disappearing, and it contains a flag.

**Answer the questions below**

1. _What is the flag in the red box?_

Answer: `THM{CATCH_ME_IF_YOU_CAN}`

**_Explanation:_**

We visit `http://MACHINE_IP/contact` and go to debugger and open `flash.min.js`

<img width="1920" height="930" alt="image" src="https://github.com/user-attachments/assets/b1ab020a-50fa-4765-967a-36ef43d620da" />

Now we click on `{}` at the end (it is called as pretty print)

<img width="1130" height="928" alt="image" src="https://github.com/user-attachments/assets/48f3d575-fde0-4424-950a-3ff99a3205e3" />

Now we scroll down and find `flash['remove']();` on line `110`

<img width="588" height="344" alt="image" src="https://github.com/user-attachments/assets/7f2bc8ae-a5f8-4919-b912-7a830073ebf0" />

Now we click on the line number and we can see, a breakpoint 

<img width="577" height="312" alt="image" src="https://github.com/user-attachments/assets/1648142e-a9ac-4485-987e-ea04bbaf7f5f" />

Now we refresh the page and a red pop up box appears with the flag

<img width="780" height="568" alt="image" src="https://github.com/user-attachments/assets/45e4b2ab-7c51-4114-90de-c9da414dedd5" />

---

**Task 6: Developer Tools - Network**

**Developer Tools - Network**

The network tab on the developer tools can be used to keep track of every external request a webpage makes. If you click on the Network tab and then refresh the page, you'll see all the files the page is requesting. 


Try doing this on the contact page; you can press the trash can icon to delete the list if it gets a bit overpopulated.


With the network tab open, try filling in the contact form and pressing the Send Message button. You'll notice an event in the network tab, and this is the form being submitted in the background using a method called AJAX. AJAX is a method for sending and receiving network data in a web application background without interfering by changing the current web page.


<img width="815" height="466" alt="image" src="https://github.com/user-attachments/assets/0f721509-8ad4-42b0-945d-98855dec5c78" />

Examine the new entry on the network tab that the contact form created and view the page the data was sent to in order to reveal a flag.

**Answer the questions below**

1. _What is the flag shown on the contact-msg network request?_

Answer: `THM{GOT_AJAX_FLAG}`

**_Explanation:_**

We visit `http://MACHINE_IP/contact` and go to Network tab in dev tools

<img width="1920" height="930" alt="image" src="https://github.com/user-attachments/assets/11abe75c-2e58-44ed-819c-839a6a3359ba" />

Now we fill out the form and submit

<img width="784" height="590" alt="image" src="https://github.com/user-attachments/assets/91908d34-b7e1-4d28-95a9-d082daf5260a" />

Now we can see a pop up with the message

<img width="492" height="129" alt="image" src="https://github.com/user-attachments/assets/e6b3ba01-013b-4371-b976-8dbc5940d1ab" />

We can also see there's an entry in the networks tab and we open it

<img width="1131" height="929" alt="image" src="https://github.com/user-attachments/assets/6176c399-ff95-4328-a9e6-48f92bc93328" />

We click on "Response" and see the flag

<img width="1131" height="449" alt="image" src="https://github.com/user-attachments/assets/eee67517-d160-4f01-ae6d-7282b6b1a184" />

---
