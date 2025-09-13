---
title: Exploring Browser Interaction
parent: Web Fundamentals
nav_order: 1
permalink: /web/website/browser/
---
# Browser interaction
Browsers are complex tools that, at its core, performs a simple task, making requests to web servers. These requests almost always are made using HTTP/HTTPS. The example below demonstrates the Firefox developer tools available to us to analyze the request made to a simple website. You can open the Firefox developer tools by right clicking and selecting "inspect(Q)". We will analyze the the requests and response in the following sections, introducing different technologies as we do so.
![example_site](/content/assets/images/example_site.png)
# Inspector
The first of the tabs you will see in the Firefox developer tools is the inspector tab. This tool allows you to explore the HTML, CSS and the overall layout of the websites user interface. 
## HTML
HTML stands for Hypertext Markup Language, and is a Markup language originally designed by Tim Burners-Lee and currently is the standard for content to be displayed in a web browser. A Markup language describes the structure of text, and in HTML's case can be very powerful. It uses tags to define elements like headings, paragraphs, links, images, and forms. Looking at the example below, we can see exactly how this web page is structured, and even see a hidden value ```is_admin``` that is sent along with the form for the password
![HTML_example](/content/assets/images/inspector1.png)
 Judging by this value name, we can assume that this value is useful for determining the access the user has. It is important to note that even within the browser, a user can simply edit this value and upon refreshing the page, the browser will send the new value to the server. In this case is a clear security risk and shows that user submitted form fields should never be trusted for critical functionality without numerous protections in place. We go more into this in the page blank.
# Console & Debugger
The next 2 tabs are the console and the debugger. In the console we can run JavaScript code, and in the debugger we can see JavaScript code the server runs on our browser. 
## JavaScript
JavaScript is a programming language used to create interactive and dynamic content on websites. It runs in the browser and can respond to user actions, manipulate the HTML and CSS of a page, and communicate with servers. JavaScript is essential for things like form validation, animations, and real-time updates without refreshing the page.
## Interacting with the browser using the console
Below we can see an example of a simple debugging statement that can be printed to the console using JavaScript.
![browser-console](/content/assets/images/browser_console.png)  
While this is fairly standard for most programming languages, using the native console, you can interact with the browser in some interesting ways. Below we make an alert appear, which this may look familiar if you have ever encountered a website that has ever returned an alert in this manner as a result of invalid input or other errors.
![console_alert](/content/assets/images/console_alert.png)  
Below is an example of interacting with the form variables to change the client-side field.
![console_auth_bypass](/content/assets/images/console_auth_bypass.png)  

# Network
The network tab is useful for analyzing the traffic between your browser and the sites it is making requests and receiving responses from. There is a number of important technologies to be familiar with when analyzing this data. 
## HTTP/HTTPS
HTTP (Hypertext Transfer Protocol) is a protocol used to communicate and transfer data over the internet. It is a stateless, protocol built on top of either TCP/IP or QUIC/IP depending on the version, and it follows a request-response model where the client sends a request to the server, and the server responds with content like HTML, images, or data.

HTTPS (HTTP Secure) adds a layer of encryption using TLS (Transport Layer Security). More on this later.

### HTTP Methods
When a web browser or other client communicates with a server, it uses specific HTTP methods to indicate what kind of action it wants to perform. These methods form the foundation of how data is requested, submitted, or modified on the web. Using the browser developer tools, we can actually see and edit the types of requests and the data within that we make to the website by opening the context menu (right clicking) of the request and selecting "Edit and Resend". We will make extensive use of this feature and Burps enhanced tool, Repeater, throughout the rest of this unit. 
![Http_Methods](/content/assets/images/HTTP_Methods.png)

### Headers
HTTP headers are key-value pairs that are sent in both HTTP requests and responses. They provide metadata about the communication between the client and the server, such as what type of content is being sent, how the browser should behave, and how authentication is handled.

They are important for:
- Controlling how the browser and server interact
- Managing sessions, cookies, and authentication
- Defining how data is formatted and processed
- Enabling features like caching, compression, or redirects
- Setting a Content Security Policy (CSP)

## JSON
During your analysis of web traffic, you will inevitably encounter JSON. JSON stands for JavaScript Object notation and is used to transfer data between applications. Below is a simple example of some JSON data.
```
"users":[
{"username":"Isaac", "password":"Asimov"},
{"username":"Admin", "password":"Admin"}
]
```
We see that the data is represented in name:value pairs, or objects, contained within an array, with pairs and objects separated by commas. The structure is both simple to read and to understand. 
JSON is seen commonly in Web Applications as it is a simple and compact text based format, ideal for transferring information over the internet between independent software. 
# Style Editor

## CSS
In the styles section of your browsers developer tools, you can see the CSS code that helps render the web page. CSS, Cascading Style Sheets, is a style sheet language or a language intended to define the presentation of a structured document, like HTML. This allows the same content to be presented in a variety of ways. Below is an example of CSS that seems pretty intuitive.  
```
body {
  background-color: black;
}

h1 {
  color: #39ff14;
  text-align: center;
}

p {
  color: green; 
  text-align: center;
  font-family: verdana;
  font-size: 20px;
}

p {
  color: #39ff14; 
  text-align: center;
  font-family: verdana;
  font-size: 20px;
}
```
Any HTML with the tags shown before the brackets will be styled according to the definitions. You may have noticed that there are two styles for the p tag, and when this is the case, the latest rule with the same specificity (not discussed in this book) will get chosen. This is part of the cascading nature of style sheets that makes it so useful, as browsers will follow a set process to determine what style gets applied during any conflicts. This allows large teams to work on and maintain sites with ease. 
# Storage

## Cookies
![Cookie_intro](/content/assets/images/cookie_intro.png)
In the storage section of your browser’s developer tools, you can see cookies that websites have saved on your computer. Cookies are small pieces of data sent from a website and stored in your browser. They allow a site to “remember” information between visits, such as whether you are logged in, what items are in your shopping cart, or your site preferences.
Each cookie has a name and a value, and may also include details like the website it belongs to, when it expires, and security options. Cookies are sent back and forth between your browser and the server automatically, so websites can maintain state across multiple page loads.
This system is what makes modern web applications usable: you don’t have to re-enter your password every time you click a link, and online stores can keep track of your cart as you browse. However, cookies are also a breeding ground for a wide variety of vulnerabilities if they are not properly secured, such as session hijacking or cross-site scripting attacks. We go more into detail on the topic of Cookies throughout this chapter.
