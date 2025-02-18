## REQUIREMENTS
- Full proof-of-concept reference. We are rejecting any template that doesn't clearly state what can be abused and how. For instance, in DLL hijacking, saying "run ProcMan and filter for NOT FOUND path ends with .dll" isn't it. Your reference MUST demonstrate the abuse you're documenting. References that are step-based only with no proof of execution/download/action, w.e., will be rejected.
- Limit references to two, with at least one being a full proof of concept, as described above.
- No extra new lines after the template, and check each template line for trailing spaces.
- Use the order of the template exactly as shown. The below template has three techniques, thus three step blocks are implemented. Add or remove as needed but don't change the order of Usecase, Category, etc.
- If you're making a new category of abuse, also make a PR to the Categories.md file
- NEW REQUIREMENT 2/18/2025: Use seperate PRs per technique please. 

## Template definitions
Steps: How to carry out the technique\
Description: What you're doing (quick summary of the steps)\
Category: Submit a category from our list. If it doesn't exist, we will make the category if it's a common category.\
Privileges: None, User, User interaction, Administrator, Installation\
Limitations: Caveats to using this method\
MitreID: The official Mitre technique identifier

## Understanding Privs
None: Use this for apps you can self-register to WITHOUT user interaction. For instance, if you want to use Discord as a C2 or to host files, that's something you can carry out without obtaining credentials of a user that's not yours.\
User: Needs a local or cloud-based user account that wasn't made by you.\
User interaction: An employee or user needs to be convinced to do "something" to finish the exploitation process.\
Administrator: Needs administrative rights to carry out.\

Note: Be concise if multiple privilege sets can accomplish a technique. For instance, in the Zix template, I wrote User interaction/User since an attacker can carry out Phishing if they aquire a User account in a different way. Another example would be DLL hijacking, which can be considered User interaction/User, since you could technically social engineer a user into clicking a file that pulls the malicious DLL and drops it into the correct directory.

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
