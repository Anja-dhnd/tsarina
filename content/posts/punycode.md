---
title: "Punnycode"
date: 2022-08-30T14:48:20+02:00
draft: false
categories: ["Social Engineering"]
tags: ["phishing", "punycode", "social engineering"]
---

# What is Punycode?

According to Wikipedia,

> Punycode is a representation of Unicode with the limited ASCII character subset used for Internet hostnames. Using Punycode, host names containing Unicode characters are transcoded to a subset of ASCII consisting of letters, digits, and hyphens, which is called the letter–digit–hyphen (LDH) subset. For example, München (German name for Munich) is encoded as Mnchen-3ya.

In other words, anything we write on computers has a unique binary binary number associated with it. **ASCII**, a character encoding standard, uses 7 bits to code up to 127 characters, enough to code the Alphabet in upper and lower case, numbers 0-9 and some additional special characters. Despite being a standard, ASCII doesn't support languages such as Hebrew or Russian.

To counter this problem, **Unicode** has been created. It uses 32 bits to code up to 2,147,483,647 characters! Unicode gives us enough options to support any language and even emojis.

## What about Punycode then?

Punycode is a way of converting words that cannot be written in ASCII, into a Unicode ASCII encoding. Why would you want to do this? The global Domain Name System (DNS), the naming system for any resource connected to the internet, is limited to ASCII characters. With punycode, you can include non-ASCII characters within a domain name by creating “bootstring” encoding of Unicode as part of a complicated encoding process.

## Punycode attacks

Unicode characters can look the same to the naked eye but actually, have a different web address. Some letters in the Roman alphabet, used by the majority of modern languages, are the same shape as letters in Greek, Cyrillic, and other alphabets, so it’s easy for an attacker to launch a domain name that replaces some ASCII characters with Unicode characters. For example, you could swap a normal T for a Greek Tau: τ, the user would see the almost identical T symbol but the punycode behind this, read by the computer, is actually xn--5xa. Depending on how the browser renders this information in the address bar, these sneaky little characters are difficult for us humans to identify.
This technique is called a homograph attack, the URLs will look legitimate, and the content on the page might appear the same on the face of it but its actually a different website set up to steal the victim’s sensitive data or to infect the user’s device. These attacks use common techniques like phishing, forced downloads, and scams.

## Why are Punycode attacks a bigger problem on mobile?

Research into Punycode attacks on mobile identified a number of new malicious domains (listed below). Not only are these sites hosting phishing attacks on domains that are visually deceptive to users, but they are optimized for mobile, meaning hackers are aware of the difficulties faced by mobile users in identifying deceptive URLs. By targeting mobile users, these attacks are resulting in more successful phishing campaigns.
Phishing attacks are generally more difficult to detect on mobile for a number of reasons, this becomes near impossible when punycode is introduced and displayed properly.

- Smaller screen size leaves less space to evaluate the legitimacy of a website
- OS design typically hides the already tiny address bar as the user scrolls down to make room for the page content
- Distracted users tend to rush through various pages and notifications
- There is no mouse-over or preview functionality, which prevents the user from seeing or evaluating the link destination before clicking

## Ways to avoid punycode attack

1. Be cautious if the site presses you to do something quickly. This is a classic strategy by hackers to rush their potential victims so that they are less likely to notice anything suspicious.
2. If you are being offered a deal, go to the original company site and check if it’s available there as well, if not it’s most likely a scam doing its best to mimic the established brand and trick visitors into handing over their details.
3. If some of the letters in the address bar look weird, or the website design looks different, rewrite it or visit the original company URL in a new tab to compare. The letters in the address bar looking strange is a key indicator that punycode is being used to trick you into thinking you are visiting a well-established brand site when in fact you are being taken to a malicious site.
4. Force your browser to display Punycode names, this option is available in Firefox.
5. Click on the padlock to view and inspect the HTTPS certificate.
6. Use a mobile security solution, Jamf for example uses MI:RIAM’s machine learning and artificial intelligence to monitor all data traffic and to detect and block phishing links such as these.
