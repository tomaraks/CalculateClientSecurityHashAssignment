# CalculateClientSecurityHashAssignment

Process Design Document
Calculate Client Security Hash 
Process Design Document – Calculate Client Security Hash 1
Process Design Document History
Date Version Role Name Organization Function Comments
28.09.2017 1.0 Draft Olfa Ben
Taarit
ACME Systems
Inc.
SME Creation
v 1.0
28.09.2017 1.2 Reviewer Vrabie
Stefan UiPath BA
Approved
v 1.0
09.01.2019 1.3 Reviewer Silviu
Predan UiPath RPA Dev Updated
Process Design Document – Calculate Client Security Hash 2
Table of Contents
1. Introduction ...............................................................................................................................................3
1.1 Purpose of the document..................................................................................................................3
1.2 Objectives.............................................................................................................................................3
1.3 Process key contacts...........................................................................................................................3
2. AS IS Process Description.........................................................................................................................4
2.1 Process overview.................................................................................................................................4
2.2 Detailed Process map.........................................................................................................................6
2.3 Detailed Process Steps .......................................................................................................................8
2.4 Exceptions handling......................................................................................................................... 11
2.5 Error mapping and handling .......................................................................................................... 12
2.6 In-Scope application details............................................................................................................ 12
3. Development details.............................................................................................................................. 13
3.1 Prerequisites for development...................................................................................................... 13
3.2 Password policies............................................................................................................................. 13
3.3 Credentials and asset management ............................................................................................. 13
4. Document Approval Flow...................................................................................................................... 13
5. Appendix ................................................................................................................................................. 14
5.1 UiPATH automated process details............................................................................................... 14
Process Design Document – Calculate Client Security Hash 3
1. Introduction
The Process Design Document describes the business processes chosen for automation using the
UiPath Robotic Process Automation (RPA) technology.
This document describes the sequence of steps performed as part of the process, as well as the
conditions and requirements prior to its automation. This design document serves as a base
documentation for developers to collect the details required for robotic automation of the same
business process.
The process has been selected for RPA as part of the larger project initiative conducted within
ACME Systems Inc., the Finance and Accounting department.
The objective of this process automation is linked to the project business case and is mainly
intended to:
➢ Deliver faster processing
➢ Reduce redundant activities
➢ Improve overall performance and reliability
The Design Document includes a brief, but comprehensive set of requirements for the process. Its
structure is based on the input provided by the Subject Matter Expert (SME) in the process.
Role Name Date of action Notes
Process SME Aurel Vlaicu TBD
Point of contact for questions related
to business exceptions and
passwords
Reviewer /
Owner
Sergiu Celibidache TBD POC for process exceptions
Approval for
production Nicoale Herlea TBD Escalations, Delays
Process Design Document – Calculate Client Security Hash 4
2. AS IS Process Description
General information about the process selected for RPA implementation, prior to its automation:
AS IS process details
Process full name Calculate Client Security Hash
Function Security
Department Finance and Accounting
Process short description
(operation, activity, outcome)
Generate the Security Hash for each Client based on their
personal information.
Role required for performing
the process
System 1 User
Process schedule Daily
# of item processes / day 7 – 15 Clients
Average handling time per
item
2 min / Client
Peak period (s) No peak period
# of FTEs supporting this
activity
1
Level of exception rate No expected exceptions
Input data Client Data
Output data Client Security Hash
Process Design Document – Calculate Client Security Hash 5
2.1.1 In scope for RPA
The activities and exceptions in this process that are in the scope for RPA, are listed below:
➢ Full Scope for RPA - the process is to be 100% automated.
2.1.2 Out of scope for RPA
There are no activities out of scope for RPA
Process Design Document – Calculate Client Security Hash 6
This chapter presents the chosen process in detail, which enables the developer to build the automated process.
Step Short Description
1.1 Open the ACME System 1 Web Application.
1.2 Log in to System 1. Required input data: email and password.
1.3 Access the Dashboard - the central location, where the user can pick a specific menu item.
1.4 Access the Work Items listing to view all the available tasks to be performed (Output data: Work Items).
1.5 For each activity of the WI5 type, perform the following steps:
Start
Log in to ACME
System 1 web
application
Access “Work Items”
on the dashboard
Select an activity of
type WI5
Copy Client
information from
the details page
Open SHA1 website
and enter the
correct formula
Retrieve Client
security hash from
the website
Go back to Work
Item and open
“Update Work Item”
page
Set the status to
Completed and the
Security Hash as a
comment
End
Process Design Document – Calculate Client Security Hash 7
1.5.A Open the Details page of the selected activity to retrieve the Client Information Details.
1.5.B Open the SHA1 Online webpage - http://www.sha1-online.com/, and provide the following input: [ClientID]-
[ClientName]-[ClientCountry]. Replace all the variables with the corresponding values. Use dashes between items,
as shown above.
1.5.C Retrieve the Client Security Hash value from the webpage.
1.5.D Go back to Work Item Details and open Update Work Item.
1.5.E Set the status to “Completed”. Add a comment with the obtained [SecurityHash].
1.6 Continue with the next WI5 Activity.
Process Design Document – Calculate Client Security Hash 8
The complete set of steps in the process, including keystrokes and clicks, are to be defined with
screenshots. If there are any data restrictions, mask the sensitive information, such as Policy
Number, Customer ID, bank account number, etc).
#
Step action
description Screenshot Expected
result Remarks
1.1
Open the ACME
System 1 Web
Application
The display
of the
System 1
Web App
screen.
Possible
exception:
- Handle
exception if
Web app not
available
1.2
Log in to System
1. Required input
data: email and
password.
Access to the
dashboard
Possible
exception:
- Handle
exception if
Incorrect email
or Password
1.3
Access the
Dashboard - the
central location,
where the user
can pick a specific
menu item
The display
of each item
in the menu
Process Design Document – Calculate Client Security Hash 9
1.4
Access the Work
Items listing to
view all the
available tasks to
be performed
The display
of the task
list
1.5
For each activity
of the type WI5
perform the
following steps:
Possible
exception:
Handle
exception if no
task of type
'Calculate
Client Security
Hash’ exist
1.5.A
Open the Details
page of the
selected activity
to retrieve the
Client Details
(Output data:
Client Details)
1.5.B
Open the SHA1
Online Webpage -
http://www.sha1-
online.com/ and
provide the
following input:
[ClientID]-
[ClientName]-
[ClientCountry]
Replace all the
variables with the
corresponding
values. Use
dashes between
items, as shown
above.
Process Design Document – Calculate Client Security Hash 10
1.5.C
Retrieve Client
Security Hash
from the
webpage
1.5.D
Go back to the
Work Item Details
and select Update
Work Item
1.5.E
Set the status to
“Completed”. Add
a Comment with
the obtained
[SecurityHash]
1.6
Continue with the
next WI5 Activity
Process Design Document – Calculate Client Security Hash 11
The types of exceptions identifiable in the automation process can be classified according to the
table below.
Based on the above criteria, the table below should reflect all the known exceptions identified
throughout the process and map the expected action the robot needs to take in each case.
Insert as many rows as required in the table, to capture all exceptions in a comprehensive list.
For any other unanticipated or unknown exceptions, the robot should send an email notification
at exceptions@acme-test.com with the original email and error message screenshot attached.
Area Known Unknown
Business
Previously encountered situation. A
possible scenario is defined, and
clear actions and workarounds are
provided for each case.
A situation never encountered before. It
can be caused by external factors.
#
Exception
name
Step where
exception is
encountered
Parameters Action to be taken
1
Incorrect email
or password Step # 1.2
If message for
incorrect
username or
password
exist
Send email to exceptions@acmetest.com
“Hello,
The username or the email is incorrect. Please
check and restart
Thank you’’
2
No task of type
WI5 exists Step # 1.5 Stop process
Process Design Document – Calculate Client Security Hash 12
A comprehensive list of all the errors, warnings, or notifications should be consolidated here with
the description and action to be taken by the Robot in each case.
The errors identified in the automation process can be classified according to the table below.
Based on the above criteria, the table below should reflect all the identifiable errors in the process,
and map the expected action of the Robot in each case.
Insert as many rows as required in the table, to capture all the errors in a comprehensive list.
*Feel free to insert an additional error mapping table for more complete explanation.
The table below lists all the applications that are used as part of the automated process.
#
Application
name &
Version
Syst.
Lang.
Login
module Interface
Environment/
Access method Comments
1 ACME System 1 EN Web Web Web Browser
2 SHA1 Online EN n/a Web Web Browser
Area Known Unknown
Technology
Previously encountered situation
- action plan or workaround
available.
A situation never encountered before, or
may happened independent of the
applications used in the process.
# Error Name
Step where
error is
encountered
Parameters Action to be taken
1
Application
unresponsive
/ page not
loading
Any step
No response /
blank page
Retry 2 times.
Close application and run the sequence
again
Process Design Document – Calculate Client Security Hash 13
3. Development details
• Development or testing environment are to be provided for development purposes.
• The provided development and testing environments are exact replicas of the production
environment.
• Dedicated system and application access are given to developers with the adequate
permissions.
Users manage their own passwords. There are no special policies in place.
Login details (user IDs and passwords) should be stored under Windows Credential Manager or
UiPath Orchestrator Assets.
4. Document Approval Flow
Version Flow Role Name
Organization
(Dept.)
Signature
and Date:
1.0 Document
prepared by
Business
Analyst Name Surname
1.0 Document
Approved by:
Business
Process
Owner
Name Surname
1.0 Document
Approved by:
Dev/RPA
Solution
Architect
Name Surname
Process Design Document – Calculate Client Security Hash 14
5. Appendix
Note: this step is to be filled in after automation process is complete
Automation overview: (time to dev, test, etc)
Robots type: Unattended
Level of human intervention required:
Use of Orchestrator:
Exceptions recorded in automation process:
Errors identified in the automation process:
Challenges identified in the automation process:
Lessons Learned:
Any adjustments made to facilitate the automation process and any steps taken to shift from the
human way of working to the automatic one. Any activity performed to improve the As Is process
and to enable higher rates of automation of the process:
➢ Process Assumption
➢ Input data assumption
➢ Number or types of input to be received
➢ Skipping the login interface and collecting backend details
➢ Extracting backend data without opening the file
➢ Data conversion / formatting
Reporting: The details and format of the logging mechanism available in the workflow have to be
specified here, whether it is a local log report or the Orchestrator log).
The format should be specified by the business users.
Workflow and scripts: A brief overview of each workflow and the sequence in which it is executed
should be provided here.
