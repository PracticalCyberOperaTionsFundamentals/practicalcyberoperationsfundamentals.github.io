---
title: Exploring Browser Interaction
parent: What is a Website?
nav_order: 2
---
# Browser interaction
Browsers are complex tools that, at its core, performs a simple task, making requests to web servers. These requests almost always are made using HTTP/HTTPS. The example below demonstrates the Firefox developer tools available to us to analyze the request made to a simple website. You can open the Firefox developer tools by right clicking and selecting "inspect(Q)". We will analyze the the requests and response in the following sections, introducing different technologies as we do so.
![Firefox DevTools showing an HTTP request]({{ site.baseurl }}/content/assets/images/simple_site.png)
# Inspector
The first of the tabs you will see in the Firefox developer tools is the inspector tab. This tool allows you to explore the HTML, CSS and the overall layout of the websites user interface. 
![inspector]({{ site.baseurl }}/content/assets/images/inspector1.png)
## HTML
HTML stands for Hypertext Markup Language, and is a Markup language originally designed by Tim Burners-Lee and currently is the standard for content to be displayed in a web browser. A Markup language describes the structure of text, and in HTML's case can be very powerful. It uses tags to define elements like headings, paragraphs, links, images, and forms. Looking at the example above, we can see exactly how this web page is structured, and even see a hidden value ```is_admin``` that is sent along with the form for the password. Judging by this value name, we can assume that this value is useful for determining the access the user has. It is important to note that even within the browser, a user can simply edit this value and upon refreshing the page, the browser will send the new value to the server. In this case is a clear security risk and shows that user submitted form fields should never be trusted for critical functionality without numerous protections in place. We go more into this in the page blank.
# Console & Debugger
The next 2 tabs are the console and the debugger. In the console we can run JavaScript code, and in the debugger we can see JavaScript code the server runs on our browser. 
## JavaScript
JavaScript is a programming language used to create interactive and dynamic content on websites. It runs in the browser and can respond to user actions, manipulate the HTML and CSS of a page, and communicate with servers. JavaScript is essential for things like form validation, animations, and real-time updates without refreshing the page.
## Interacting with the browser using the console
Below we can see an example of a simple debugging statement that can be printed to the console using JavaScript.
![browser-console]({{ site.baseurl }}/content/assets/images/browser_console.png)  
While this is fairly standard for most programming languages, using the native console, you can interact with the browser in some interesting ways. Below we make an alert appear, which this may look familiar if you have ever encountered a website that has ever returned an alert in this manner as a result of invalid input or other errors.
![console_alert]({{ site.baseurl }}/content/assets/images/console_alert.png)  
Below is an example of interacting with the form variables to change the client-side field.
![console_auth_bypass]({{ site.baseurl }}/content/assets/images/console_auth_bypass.png)  

# Network

## HTTP/HTTPS
HTTP (Hypertext Transfer Protocol) is a protocol used to communicate and transfer data over the internet. It is a stateless, protocol built on top of either TCP/IP or QUIC/IP depending on the version, and it follows a request-response model where the client sends a request to the server, and the server responds with content like HTML, images, or data.

HTTPS (HTTP Secure) adds a layer of encryption using TLS (Transport Layer Security). More on this later.

### HTTP Methods
When a web browser or other client communicates with a server, it uses specific HTTP methods to indicate what kind of action it wants to perform. These methods form the foundation of how data is requested, submitted, or modified on the web. Using the browser developer tools, we can actually see and edit the types of requests and the data within that we make to the website by opening the context menu (right clicking) of the request and selecting "Edit and Resend". We will make extensive use of this feature and Burps enhanced tool, Repeater, throughout the rest of this unit. 
![Http_Methods]({{site.baseurl}}/content/assets/images/HTTP_Methods.png)

### Headers
HTTP headers are key-value pairs that are sent in both HTTP requests and responses. They provide metadata about the communication between the client and the server, such as what type of content is being sent, how the browser should behave, and how authentication is handled.

They are important for:
- Controlling how the browser and server interact
- Managing sessions, cookies, and authentication
- Defining how data is formatted and processed
- Enabling features like caching, compression, or redirects
- Setting a Content Security Policy (CSP)

## REST and SOAP APIS

## JSON

# Style Editor

## CSS

# Storage

## Cookies

