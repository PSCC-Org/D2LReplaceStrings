D2LReplaceStrings
=================

Resources for Audrey and Brandon's Fusion 2013 Presentation

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

###Course Certificate
