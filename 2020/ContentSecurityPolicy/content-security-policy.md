---
layout: default
title: Content Security Policy
parent: 2020
nav_order: 20
---

# Content Security Policy
{: .no_toc }
Presented on 8th September 2020 by [Taeim](https://github.com/kwontaeim)

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}


## What is Cross Site Scripting (XSS)?

- XSS enables an attacker to inject client-side script into non-malicious web pages viewed by other users.
- It’s (still) in the OWASP top 10.
- In 2016 there was a 61% likeihood of a brower-based vulnerability being found in a web application.
- Of those brower based vulnerablities, 86% were found to be XSS related.
- That’s just over 52% of all web application vulnerablities.
  (*The OWASP Top 10 :  a standard awareness document for developers and web application security. It represents a broad consensus about the most critical security risks to web applications.
  https://www.edgescan.com/assets/docs/reports/2016-edgescan-stats-report.pdf)
![image](https://user-images.githubusercontent.com/21251967/160268296-e2332150-0105-4238-b9b0-64f5ebfdd3c7.png)

## What can be done with XSS?

- Make modification to the DOM - replace a form action to point to your own script to capture credentials.
- Load in additional scripts, resources, styles, images etc.
- (such as a crypto miner to make some $$$).
- Access HTML5 APIs: webcam, microphone, geolocation
- Keylogging
- Phishing
- Steal cookies (and therefore steal session cookies)

## How do these "mitigations" work?
- WAFs, XSS filters
- Block requests containing dangerous tags / attributes
- HTML Sanitizers
- Remove dangerous tags / attributes from HTML
- Content Security Policy
- Distinguish legitimate and injected JS code
- Whitelist legitimate origins
- Whitelist code hash
- Require a secret nonce

## What is a CSP?
- HTTP response header to help reduce XSS risks.
- It’s an extra Layer of security.
- Declares what resources are allowed to load.
- Blocking those pasky crypto-mining scripts that have been popping up.

## What can we protect? (Source Whitelist Directives)
- `Default-src`
- `Script-src ‘unsafe-inline’`
    - Allows use of inline source elements such as style attribute, onclick, or script tag bodies ( don’t use unsafe-inline)
- `Style-src ‘self’`
    - Allow loading from same scheme, host and port
- `Img-src `
    - Allows any url except data: blob: filesystem: schemes
- `form-action`
- `object-src ‘none’`
   - Dont load resources from any sources
- `Upgrade-insecure-requests`
- `media-src`: Define from where the protected resource can load video and audio
- `frame-src`: Define from where the protected resource can embed frames
- `font-src`: Define from where the protected resource can load fonts
- `connect-src`: Define which URIs the protected resource can load using script interfaces
- `script-nonce`: Define script execution by requiring the presence of the specified nonce on script elements
- `plugin-types`: Define the set of plugins that can be invoked by the protected resource by limiting the types of resources that can be embedded
- `form-action`: Define which URIs can be used as the action of HTML form elements

And so much more -> content-security-policy.com

## Examples

#### Example 1
Wants all content to come from the site's own origin (this excludes subdomains.)   
`Content-Security-Policy: default-src 'self'`

#### Example 2
Wants to allow content from a trusted domain and all its subdomains (it doesn't have to be the same domain that the CSP is set on.)   
`Content-Security-Policy: default-src 'self' *.trusted.com`

#### Example 3
wants to allow users of a web application to include images from any origin in their own content, but to restrict audio or video media to trusted providers, and all scripts only to a specific server that hosts trusted code.    
`Content-Security-Policy: default-src 'self'; img-src *; media-src media1.com media2.com; script-src userscripts.example.com`

#### Example 4
A web site administrator of a web mail site wants to allow HTML in email, as well as images loaded from anywhere, but not JavaScript or other potentially dangerous content.    
`Content-Security-Policy: default-src 'self' *.mailsite.com; img-src *`


## Links & futher reading
https://www.w3.org/TR/CSP3   
https://csp.withgoogle.com/docs/index.html   
https://scotthelme.co.uk/csp-cheat-sheet   
https://observatory.mozilla.org     
https://infosec.mozilla.org/guidelines/web_security#content-security-policy
https://csp-evaluator.withgoogle.com      
https://hacks.mozilla.org/2016/02/implementing-content-security-policy     

