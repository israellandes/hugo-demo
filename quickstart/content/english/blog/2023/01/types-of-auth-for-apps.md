---
author: admin
title: "Different Types of Security Login Standards for Applications"
type: post
date: 2023-01-22T21:38:24Z
draft: false
thumbnail: images/23/01/security/HTTP-Auth-example.png
url:
w3codecolor: true
categories:
- Website Programming
tags:
- security
---
{{< images/img src="images/23/01/security/HTTP-Auth-example.png" alt="HTTP Auth Security login example." >}}

This article is about the different types of security standards used for logging into applications

<hr>

# Security Login Standards

The three main standards I will focus this article on are:

1. HTTP Basic Auth - **Least secure**
2. OAuth - **More secure**
3. SAML - **Most secure**

Despite these security standards, a single method is 100% safe. All best practices must be followed to reduce your chances as much as possible in preventing any security breaches to your websites and applications

<hr>

## 1. HTTP Basic Authentication

#### **Pros**

[HTTP Basic Auth](https://docs.nginx.com/nginx/admin-guide/security-controls/configuring-http-basic-authentication/) is open-source and fairly easy to implement on web servers like Apache & Nginx that serve website content in a variety of different formats and languages, the main being HTML and PHP.
I have set up applications in a private repository on Github that utilize this basic login method because of its easy integration.

[**HTTP Basic Auth Walkthrough**](https://www.digitalocean.com/community/tutorials/how-to-set-up-basic-http-authentication-with-nginx-on-ubuntu-14-04)

{{< images/img src="images/23/01/security/HTTP-Auth-example.jpg" alt="HTTP Auth Security login example." >}}

#### **Cons**

[Known HTTP Authentication Explotations:](https://www.hackingarticles.in/multiple-ways-to-exploiting-http-authentication/)

- xHydra
- Hydra
- Ncrack
- Medusa
- Metasploit
- Burp Suite

Basic authentication has several other basic vulnerabilities such as;
1. The username and password are passed in every request. Which is 100% unsafe in HTTP, and a bit safer under HTTPS.
2. Credentials submitted with every request open a risk for an attacker to retrieve a session or authentication token. 

With basic auth, any request is an opportunity to steal the user's password. This is not the best practice by far.

[**Digest Auth**](https://www.nginx.com/resources/wiki/modules/auth_digest/) reduces many of these vulnerabilities in terms of offering a bit more security by only sending an MD5 digest and bits that include the username/password, meaning attackers cannot extract credentials from a captured digest. However, it seems to be more trouble to set up than it's worth in terms of security, [according to this article](https://www.securitydrops.com/http-digest/#complexity) it is likely more secure and easier to choose the following methods.

<hr>

## 2. OAuth - SSO

[Single sign-on](https://www.onelogin.com/learn/how-single-sign-on-works) (SSO) is an authentication method that allows users to securely authenticate with many applications and websites by granting a single set of credentials.

[OAuth](https://oauth.net/) is a public standard way for access delegation, most commonly used as a means for internet users to allow websites or applications to access their information on other websites but without revealing their passwords.

This standard is a bit more effort to add to an application but offers a much higher security grade compared to HTTP Basic Auth.

I plan on completing the below tutorial and adding it to workflows because of its higher layers of security. OAuth also has open-source solutions that should speed up such integrations through the project [Vouch-Proxy](https://github.com/vouch/vouch-proxy).

[**OAuth Vouch-Proxy Walkthrough**](https://www.digitalocean.com/community/tutorials/how-to-set-up-basic-http-authentication-with-nginx-on-ubuntu-14-04)

{{< images/img src="images/23/01/security/OAuth.png" alt="OAuth loginexplained." >}}

<hr>

## 3. SAML - Security Assertion Markup Language


[Security Assertion Markup Language](https://www.onelogin.com/learn/how-single-sign-on-works) (SAML) is an authentication method and similarly to OAuth, its main function in online security is that it grants a user access to multiple web applications using one set of login credentials.

[SAMLs](https://www.onelogin.com/learn/saml#:~:text=What%20is%20SAML%3F,one%20set%20of%20login%20credentials.) main difference between itself and OAuth, is that SAML is designed for a specific user, while OAuth is designed for multiple applications.

This standard is a good amount of effort to add to an application based on some guides I found but offers the highest security grade compared to OAuth & HTTP Basic Auth.

From the guides, I've researched the two main components of SAML involve **Identity Providers** ( the home application base that verifies users ), and **Service Providers** ( the various applications themselves that users access through IDP) to control the verification and granting of application permissions to a user.
Typically, to set up SAML you would choose a 3rd-party IDP provider to host your main verification portal. 

However, I also found the below open-source projects [PHP-SAML](https://github.com/SAML-Toolkits/php-saml) &  [Lightsail SAML](https://github.com/lightSAML/lightSAML-IDP) that help you build your own private IDP server and will be adding it to my workflow because of its high layers of security.

[**SAML Private IDP Walkthrough**](https://medium.com/@adamfanfan7/build-your-own-central-authentication-server-using-saml-2-0-in-aws-9c5a21e01442)

{{< images/img src="images/23/01/security/SAML.png" alt="SAML login example." >}}

# Conclusion

No matter what method you choose to implement your security measures for your users and applications make sure you ask yourself and research the following questions:
1. What are the vulnerabilities of my security solution?
2. What are the best practices for implementing my security measure?
3. What are the known hacks? Or how do you hack my security measure?

Awareness is a must when it comes to security.
