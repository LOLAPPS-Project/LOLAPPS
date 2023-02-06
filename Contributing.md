
Anyone can contribute to the project, just be sure to use this template and open up a PR in the corresponding section. 

All template submissions should have at least one reference link if the exploitation methodology isn't obvious. If the application is offered on multiple platforms, choose the platform that's most logical/has the most references that you can find. For example, while Discord exists as a Desktop application - in enterprise exploitation you're more likely to see threat actors communicate via the web application, since downloading Discord looks suspicious.

Keep in mind that this is an open source project. There are thousands of applications that can be used by adversaries, so you'll have to bear with us while
we work through them. Please try to make it easy on us to PoC - there are many products that need premium or enterprise subscriptions, therefore our
capacity to test paid apps will solely be limited on your ability to make it accessible to us or pre-existing access that we might be lucky enough to have.

You'll have a better chance of standing out if you are thorough in your thought process for possible enterprise abuse. 

## Template definitions
Steps: How to carry out the technique\
Description: What you're doing (quick summary of the steps)\
Category: Submit a category from our list. If it doesn't exist, we will make the category if it's a common category.\
Privileges: None, User, User interaction, Administrator, Installation\
Limitations: Caveats to using this method\
MitreID: The official Mitre technique identifier

## Understanding Privs
None: Use this for apps you can self-register to WITHOUT user interaction. Use this even if you need special access to view the application.\
User: Needs a user account that wasn't made by you\
User interaction: An employee or user needs to click something to finish the exploitation process\
Administrator: Special access rights within an application\
Installation: The application might need to be installed

Note: Be concise if multiple privilege sets can accomplish a technique. For instance, in the Zix template, I wrote User interaction/User since
an attacker can carry out Phishing if they aquire a User account in a different way.

```
---
Name: Zix Secure Messaging
Description: Enterprise tool to compose, receive, view, reply to, and forward encrypted messages over the internet. 
Author: 'John Jackson'
Created: 2023-01-09
Usage:
  - Steps: Attempt to locate the zix secure messaging portal for the organization and check to see if you have the ability to register an account. Register an account with a custom email that looks like it could actually belong to an employee. Zip any files you want to exfiltrate from the workstation. Compose a new message, and address it to an employee that doesnt actually exist in the system. You can now retrieve the files on a different device by logging in and viewing the sent mail tab.
    Description: Steps to exfiltrate data using day-to-day enterprise tooling
    Usecase: Exfiltrating data in heavily monitored environments
    Category: Data Exfiltration
    Privileges: None
    Limitations: Need to be able to register an account or gain access to one. Can only exfiltrate a specified amount of data per message.
    MitreID: T1567
  - Steps: Register a zix secure messaging account for the company. Upload a zip-encrypted archive with your payload in it. Compose a new message and send it to an employee that doesnt exist. Login from the victim host machine, download, unzip, and execute the payload. 
    Description: Steps to setup an account and download your malware by a whitelisted solution.
    Usecase: Leveraging external tooling for proxy inspection bypass
    Category: Download
    Privileges: None
    Limitations: Need to be able to register an account or gain access to one. Can only upload a specified archive size per message.
    MitreID: T1105
  - Steps: Register a zix secure messaging account using multiple employee email addresses. Save all of the emails and passwords registered. If an employee clicks the approve button, youll now have their newly registered account to use for whitelisted phishing. 
    Description: Steps to attempt phishing with tools recognized/allowed by the company
    Usecase: Whitelisted phishing since Zix will probably be allowed if the company uses it
    Category: Phishing
    Privileges: User interaction/User
    Limitations: An employee must click the account approval button. In addition, organizations can require an account creation code instead of an approval button.
    MitreID: T1566.003
Resources:
  - Link: https://johnjhacking.com/blog/zix-exfiltration/
  - Link: https://johnjhacking.com/blog/zix-spearphishing/
Acknowledgement:
  - Person: John Jackson
    Handle: '@johnjhacking'
```
