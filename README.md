Robot Framework - Begineers Guide
=================================

Contents:
----
1. Introduction

	a. What is Robotframework
	
	b. Features 
	
	c. How to install
	
2. Writing the Test case

	a. Test case format
	
	b. Simple Test cases
	
	c. UI Test cases (Selenium)
	
	d. REST API Test cases
	
	e. others

3. Execute the Test Cases 

	a. Simple
	
	b. TAG 
	
	c. Suite
	
4. Advanced Features


1.Introduction
----

What is Robotframework

	It is a Generic Test Automation Framework.  It uses  Keyword Driven testing methodology.
	Released as Opensource (Apache Licence), Supported by Nokia Siemens.

	Test case can be written in PLAIN TEXT format.  

	Example:
	```
	Open a Browser
	Click Register Button
	```

Features

	From the Tester perspective,

	a. Excellent Test Report in HTML Format.
	b. Detailled Logging is supported (Execution Time can be measured)
	c. Easy to Write the test case  (Plain Text Model)
	d. Supports many inbuild libary (String, OS, etc)
	d. Supports third party library (Seleinum, REST API, SSH)
	f. Support of Executing the full set or sub set of the test cases.
	g. No need to Learn another Scripting language.




How To Install

In ubuntu 14.04 Desktop,
	sudo apt-get install python-pip
	sudo pip install robotframework

	Install the required library
	sudo pip install robotframework-selenium2library

	Verify the installation

	$ pybot --version



2. Writing the Test case

	a. Test case format

	GuideLines:


	Test cases are  written in a tabular format. 
	'#' is used to comment a Line
	Test case consists of multiple sections, such as "Settings","Variables","Keywords","Test Cases". 
	```
	Settings -   used as Global settings such as Loading the library.
	Variables -  used to declare the variables
	Keywords -   place for defining the custom keywords 
	Test Cases - test case which is getting executed by the user.
	```
	Each Section Line will begin with '***' and end with '***'

	Varibles will be declared and used in ${variable_name} format.


	In the below example, Seleinum Library is used in this example
	The following actions are performed.
	   1.  Run the Firefox Browser
	   2.  Open the Rediff.Com page.
	


	```
	*** Settings ***
	Library           Selenium2Library
	
	*** Variables ***
	${URL}		Rediff.com
	${BROWSER}	Firefox


	*** Keywords ***
	Open Browser To Login Page
		Open Browser   ${URL}		${BROWSER}

	*** Test Cases ***
	Test Case 1
		Open Browser To Login Page
	```

	save the above test cases in text format, and run as below

	pybot test1.txt



3. Simple Test cases

Lets understand and execute the Robot framework inbuild library functionlity.

Robots standard library includes the followng,
	Builtin,Collections,String, Telnet,OperatingSystem, Dialogs, Process, DateTime,etc.



Example1:

In this example, we will demonstrate the  'variable assignement', 'argument passing',and 'return value'

```
*** Settings ***
Library           Selenium2Library

*** Variables ***
${var1}		10
${var2}		20

*** Keywords ***
Add Example
	[Arguments]    ${element1}    ${element2}
	${result}=   Evaluate   ${element1}+${element2}
	Return from Keyword    ${result}


*** Test Cases ***
Test2 Return Example
	${result}=   Add Example  ${var1}   ${var2}
	Log  ${result}
```

Execution:

pybot test2.txt








