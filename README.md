D2L Replace Strings
=================

**Replace Strings** are variables you add to the HTMl editor in the Learning Environment. When a page is accessed, these variables are populated with specific information about the course or user accessing the page. Replace strings make it possible to both create customized content and save time when developing course materials. This page contains information about replace strings presented by Audrey Williams and Brandon Ballentine at D2L's Fusion 2013 conference.

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
 
##Where can you use **replace strings**?

* Dropbox feedback and instructions
* News Items
* Custom widgets
* Email
* Grades - comments
* Intelligent Agents
* Quizzes - header/footer
* Quicklinks
* **Discussions??**

> DO NOT USE replace strings in the Content tool. Recent versions of the Learning Environment have changed the way strings work (they don't) in this tool!

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

In the example above, we used URL parameters to pre-fill items into our form. Passing information between pages in this way is very common in web services. In the example below, we'll use a similar technique to create a course completion certificate. 

We're going to be passing student information into a PDF form, so you'll need Adobe Acrobat Pro to complete the following steps.

* In MS Word, Pages, or the desktop publishing app of your choice, create a certificate and Export/Save as a PDF.
* Open the form in Acrobat Pro. Add fields for the student's name and course name - I'm calling my fields "Name" and "Course."
* Add the following Javascript to the PDF document. For a description of the code, visit [Adobe's Website](http://blogs.adobe.com/pdfdevjunkie/2009/12/populating_pdf_form_fields_fro.html)

````javascript
//only run the script if the PDF file is being viewed in a browser window
if (this.external)
{
//The whiteList defines which fields are permitted to be changed by the URL.

whiteList = ["Name", "Course"]

//get the parameters portion of the URL and unescape it so we get the spaces and punctuation back

parametersString = this.URL.substring(this.URL.indexOf("?")+1)

//only run the script if there are parameters
if (parametersString.length > 0)
{

//create an array of key/value pairs
parameters = parametersString.split("&")

//loop through the array...
for each (parameter in parameters)
{

//create a 2 element array for each parameter as [key, value]
kvPair = parameter.split("=")

//set the field named "key" to "value"
fieldName = unescape(kvPair[0])
if (whiteList.length > 0)
{
if (whiteList.indexOf(fieldName) > -1)
{
this.getField(fieldName).value = unescape(kvPair[1])
}
}
else
{
this.getField(fieldName).value = unescape(kvPair[1])
}
}
}
}
````
* Upload the PDF to your course. Take note of the full URL of the form. For example, https://elearn.pstcc.edu/content/enforced/3839437-BCBALLENTINE-TUTORIALS/Certificate.pdf
* Create a new Quicklink and paste the URL for the uploaded PDF
* Add replace strings as URL parameters to pre-fill the student's name and course name. Your final URL should look something like this:

````html
https://elearn.pstcc.edu/content/enforced/3839437-BCBALLENTINE-TUTORIALS/Certificate.pdf?Name={FirstName}%20{LastName}&Course={OrgUnitName}
````

Once you save your link, students who click the link can access the PDF!
