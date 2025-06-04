---
title: "Web"
nav_order: 2
has_chidren: true
---
# Web Exploitation in CTF
## What is Web Exploitation
Like the name implies, Web Exploitation is the practice of discovering vulnerabilities on a website, and then utilizing the vulnerabilities to do what we want, in our case is finding the flag. 
## Fundamental principles
Throughout this chapter, there are a number of different guiding principles that you should keep at the forefront of your thought process when defending or attacking web applications.  
**Trusting user input**  
The root of many attacks is assuming input is safe. Web apps must treat all user-controlled data, query parameters, headers, cookies, form data, JSON, as hostile.
**Mixing code with data**  
Vulnerabilities occur when user input is embedded directly into code (e.g., SQL, HTML, JavaScript, shell commands) without separation or escaping.
**Client-side trust**  
Developers often assume the browser enforces logic securely. But anything client-side (JavaScript, form fields, cookies, local Storage) can be modified by attackers.
**Overexposure of internal logic or secrets**  
Comments, verbose error messages, stack traces, and leftover files can expose routes, credentials, or implementation details that attackers use to map and manipulate the app.
**Improper trust boundaries between services**  
In modern web apps (APIs, microservices, OAuth), assumptions about internal trust, IP allowlists, or token verification often create attack paths.
**Improper handling of identity and state**  
Many flaws arise from poor session tracking, weak or misused JWTs, insecure cookies, or assuming roles based on client-side flags (e.g., `isAdmin=true`).
## Overview
In this chapter, we will focus on the foundation of what websites are and 


