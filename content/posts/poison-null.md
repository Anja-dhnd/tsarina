---
title: "Poison Null Byte"
date: 2022-09-22T20:53:14+02:00
draft: false
tags: ["injection","hacking"]
---

# Poison Null Byte Attack

Also known as Null Byte Injection, a null byte (also called null terminator) is used in many languages to detect the end of a string. Systems that do not handle null bytes properly can be exploited by injecting null byte characters (%00, \x00) to get around sanity checks in file names.

Common attacks using this technique are **LFI/RFI Injection** or bypassing file extension checks. In other words, y embedding NULL Bytes/characters into applications that do not handle postfix NULL terminators properly, an attacker can exploit a system using techniques such as *directory traversal*.

## File access restriction by extension

This scenario is about accessing a file in an app that appends an extension:

1. An attacker wants to retrieve the file/etc/passwd but an extension .php is appended automatically such as /etc/passwd.php.

2. The attacker uses the null byte to terminate the string and throw away the .php extension: /etc/passwd%00

Other example:

``
$file = $_GET['file'];  
require_once("/var/www/$file.php");  
``

follows: <http://www.example.com/index.php?file=../../etc/passwd%00>. This NULL byte injection would result in the mandatory appended file extension (.php) to be dropped, and the /etc/passwd file to be loaded.

## File upload restriction by extension

In this scenaria, the app filters the allowed files by extension.

1. An attacker wants to upload a malicious.php, but the only extension allowed is .pdf.
2. The attacker constructs the file name such as malicious.php%00.pdf and uploads the file.
3. The application reads the .pdf extension, validate the upload, and later throws the end of the string due to the null byte.
4. The file malicious.php is then put in the server.

Sources: [DefendTheWeb](https://defendtheweb.net/article/common-php-attacks-poison-null-byte), [Hacker Recipes](https://www.thehacker.recipes/web/inputs/null-byte-injection)
