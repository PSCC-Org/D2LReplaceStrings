D2L Replace Strings
=================

**Replace Strings** are variables you add to the HTMl editor in the Learning Environment. When a page is accessed, these variables are populated with specific information about the course or user accessing the page. Replace strings make it possible to both create customized content and save time when developing course materials. This page contains information presented by Audrey Williams and Brandon Ballentine at D2L's Fusion 2013 conference.

##Available Strings

Here's a list of the most useful strings. Check D2L's documentation for a full list of available strings. 
 	  
For the Current	Org Unit

* {OrgUnitId}
* {OrgUnitName}
* {OrgUnitCode}
* {OrgUnitPath}
 	  
For the Current	User

* {UserId}
* {UserName}
* {OrgDefinedId}
* {FirstName}
* {LastName}
* {Email}
* {ExternalEmail}
* {InternalEmail}

##Examples

###Course Welcome

`````html
<p>Hi, {FirstName} and welcome to {OrgUnitName}. 
We're going to have a great time this semester. 
Please take a few minutes to look through Module 1 in the <strong>Course Content</strong> area, where you'll find the Syllabus and Course Schedule.</p>
`````

###Quiz Footer

`````html
<p>By submitting this assessment, I {FirstName} {LastName} acknowledge that I have read and complied by the academic honesty policy contained in the Content section of this course.</p>
`````

###Conditional Release

````html
<p>Hi {FirstName}. It looks like you didn't do so well on the Unit 1 test. For the next exam, you may want to spend some additional time looking at the <strong>Study Guide</strong> and <strong>Practice Test</strong>. Please get in touch if you have any questions!</p> 
````

###Help Widget

````html
<!-- Create a new custom widget and place the following code in the Content area -->

<h2>Need help? Having trouble?</h2>

<ul>
  <li><a href="/Shared/documentation/help.html?role={rolename}" target="_blank">Online Help</a></li>
	<li><a href="#">Quick Reference Guides</a></li>
	<li>Call the HelpDesk (865.694.6537) or <a href="#">email them</a></li>
</ul>


<h2>BEFORE YOU CALL THE HELPDESK, HERE IS SOME INFORMATION YOU MIGHT NEED:</h2>

<p>Your username is <strong>{UserName}</strong></p>

<p>Your Banner Number (also called P Number) is: <strong>{OrgDefinedId}</strong></p>

<p>Your campus email address is: <strong>{ExternalEmail}</strong></p>

<p>This Course's ID is: {OrgUnitCode}</p>

````

###Google Form

1. Start off by creating a new Google Form
2. Add several form fields
3. Access the **Responses** menu and select the **Get pre-filled URL** option
4. Type in some sample information in the fields and click the **Submit** button
5. Copy the URL and paste it into a D2L News item, Quicklink, etc. 
6. Delete the palceholder information and add Replacement Strings
7. Test the link. Each user should have the form pre-filled with their own name and email address.

Here's an example of what your Quicklink should look like:

````html
https://docs.google.com/forms/d/1VzR_yxemDtTH9qQaHOCwtVMylsFv-p6-TAvyGmOgkLY/viewform?entry.1860738625={FirstName}&entry.2039771014={LastName}
````

###Course Certificate
