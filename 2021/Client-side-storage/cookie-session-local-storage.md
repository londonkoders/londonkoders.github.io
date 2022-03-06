---
layout: default
title: Cookie, Session and Local storage
parent: 2021
nav_order: 1
---

# Cookie, Session and Local storage
{: .no_toc }
Presented on 24th January 2021 by [Taeim](https://github.com/kwontaeim)

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}


## What is Client Side Storage?
Client-side storage works on similar principles, but has different uses. It consists of JavaScript APIs that allow you to store data on the client (i.e. on the user's machine) and then retrieve it when needed. This has many distinct uses, such as:

1. Personalizing site preferences (e.g. showing a user's choice of custom widgets, color scheme, or font size).
2. Persisting previous site activity (e.g. storing the contents of a shopping cart from a previous session, remembering if a user was previously logged in).
3. Saving data and assets locally so a site will be quicker (and potentially less expensive) to download, or be usable without a network connection.
4. Saving web application generated documents locally for use offline.

## What is Cookies (old school)?
Websites have used cookies to store information to personalize user experience on websites. They're the earliest form of client-side storage commonly used on the web.

They are still used commonly to store data related to user personalization and state, e.g. session IDs and access tokens. For more information on cookies see our Using HTTP cookies article.

### Cookies

A cookie (web cookie, browser cookie) is a small piece of data(4KB) that the user's server sends to the user's web browser. The browser may store it and send it back with the next request to the same server. Typically, it’s used to tell if two requests came from the same browser — keeping a user logged-in, for example. It remembers stateful information for the stateless HTTP protocol.

Cookies have three main use-cases:

- Session management — Logins, shopping carts, game scores, or anything else the server should remember
- Personalization — User preferences, themes, and other settings
- Tracking — Recording and analyzing user behavior
- Specific cookies known as HTTP cookies are used to identify specific users and improve your web browsing experience.
- Data stored in a cookie is created by the server upon your connection. This data is labeled with an ID unique to you and your computer.
- When the cookie is exchanged between your computer and the network server, the server reads the ID and knows what information to specifically serve to you.
- A cookie with the HttpOnly attribute is inaccessible to the JavaScript Document.cookie API;



## What is Web Storage (New school)?
The Web Storage API (local/session storage) provides a very simple syntax for storing and retrieving smaller, data items consisting of a name and a corresponding value. 

This is useful when you just need to store some simple data, like the user's name, whether they are logged in, what color to use for the background of the screen, etc.

### Local storage
Local Storage does the same thing, but persists even when the browser is closed and reopened.

- Stores data with no expiration date, and gets cleared only through JavaScript, or clearing the Browser cache / Locally Stored Data.
- Storage limit is the maximum amongst the three.
- The local storage uses the localStorage object to store data for your entire website on a permanent basis. That means the stored local data will be available on the next day, the next week, or the next year unless you remove it.

### Session storage
Session storage maintains a separate storage area for each given origin that's available for the duration of the page session (as long as the browser is open, including page reloads and restores).

- Stores data only for a session, meaning that the data is stored until the browser (or tab) is closed.
- Data is never transferred to the server.
- Storage limit is larger than a cookie (at most 5MB).
- The session storage uses the sessionStorage object to store data on a temporary basis, for a single browser window or tab. The data disappears when session ends i.e. when the user closes that browser window or tab.

## Cookies vs Session vs Local storage

### Capacities
The capacity for cookies is 4 Kb for most browsers while local storage and session storage can hold 10 Mb and 5 Mb respectively.

### Browser Support
Cookies are supported in older browsers which support HTML 4 other than session / local storage are supported in HTML 5

### Accessibility
Cookies and local storage are available for any window inside the browser. Session storage is only available in the single tab that you have open

### Expiration
Session storage is removed as soon as the user closes the tab. whereas local storage is around forever until the user ends up deleting it or the code for the website is programmed to delete it after a certain action. As for cookies, the expiration date is declared when it is sent to the client and it is the developer who sets the expiration which is always declared on a cookie.

### Storage Location
For storage location, local storage and session storage are both on the browser. cookies while they are stored in the browser they are sent to this server every time a user requests something from the server.

Cookies are also really helpful for doing certain authentication-related tasks and they get sent to the server from the browser in the HTTP headers, unlike local storage or session storage which are just accessed by the application as client-side data storage.

## Private Browsing / Incognito modes
Most modern browsers support a privacy option called 'Incognito', 'Private Browsing' or something similar that doesn't store data like history and cookies. 
This is fundamentally incompatible with Web Storage for obvious reasons.

## Client Storage Purpose
- Make the website work as users'd expect
- Improve the speed/security of the site
- Allow users to share pages with social networks
- Continuously improve our website for users

More details -> https://javascript.info/data-storage
