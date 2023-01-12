
Anyone can contribute to the project, just be sure to use this template and open up a PR in the corresponding section. 

All template submissions should have at least one reference link if the exploitation methodology isn't obvious. If the application is offered on multiple platforms, choose the platform that's most logical/has the most references that you can find. For example, while Discord exists as a Desktop application - in enterprise exploitation you're more likely to see threat actors communicate via the web application, since downloading Discord looks suspicious.

Keep in mind that this is an open source project. There are thousands of applications that can be used by adversaries, so you'll have to bear with us while
we work through them. Please try to make it easy on us to PoC - there are many products that need premium or enterprise subscriptions, therefore our
capacity to test paid apps will solely be limited on your ability to make it accessible to us or pre-existing access that we might be lucky enough to have.

You'll have a better chance of standing out if you are thorough in your thought process for possible enterprise abuse. 

```
Name: Zix Secure Messaging
Description: Enterprise tool to compose, receive, view, reply to, and forward encrypted messages over the internet. 
Author: 'John Jackson'
Created: 2023-01-09
Usage:
  - Category: Data Exfiltration
    Steps to replicate: Attempt to locate the zix secure messaging portal for the organization and check to see if you have the ability to register an account. Register an account with a custom email that looks like it could actually belong to an employee. Zip any files you want to exfiltrate from the workstation. Compose a new message, and address it to an employee that doesnt actually exist in the system. You can now retrieve the files on a different device by logging in and viewing the sent mail tab.
    Usecase: Exfiltrating data in heavily monitored environments
    Privileges: User
    Limitations: Need to be able to register an account or gain access to one. Can only exfiltrate a specified amount of data per message.
    MitreID: T1567
  - Category: Download
    Steps to replicate: Register a zix secure messaging account for the company. Upload a zip-encrypted archive with your payload in it. Compose a new message and send it to an employee that doesnt exist. Login from the victim host machine, download, unzip, and execute the payload. 
    Usecase: xxxxxx
    Category: Credentials
    Privileges: User
    MitreID: T1105
Resources:
  - Link: https://johnjhacking.com/blog/zix-exfiltration/
Acknowledgement:
  - Person: John Jackson
    Handle: '@johnjhacking'
```
