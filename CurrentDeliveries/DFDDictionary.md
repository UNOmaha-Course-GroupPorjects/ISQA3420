----------------------------------------------------
DFD Dictionary
----------------------------------------------------



----------------------------------------------------
Entities:
----------------------------------------------------
Developer - Internal employees in charge of developing, maintaining and integrating, internal, proprietary, as well as external, open source code. To be used in any software or project, for internal or external use, by the company.

Project Manager - A manager directly overseeing the related development project, This person is responsible for the project and all its parts including; risk, OS use, funding, etc.

----------------------------------------------------
Sub Entities:
----------------------------------------------------
Web Source - This refers to the OSS's source repository such as Github.

National Vulnerability Database - This is the National Vulnerability Database which hold all of the CPE and CVE information.




----------------------------------------------------
Data Stores:
----------------------------------------------------
Integration Mng DB - This contains the viability, SPDX manifests, and the approved (or allowed) usage of any piece of open source code a developer wishes to integrate into a project.

OSS DB - This contains a repository of the versions of received OS File Packages that have been submitted for usage approval, and defines how/where that open source is can be used in a project.

Project DB - This is the repository of internal, proprietary, as well as external, open source code, that is being used in any software or project, for internal or external use, by the company.

NIST CPE Information - This is a local copy of all the current CPEs from the National Vulnerabilities Database.





----------------------------------------------------
Processes:
----------------------------------------------------
PRC 1.0: Submittal For Use - This takes a new OS File Package, the project, it is to be used for and how it is going to be integrated into the project, and then stores it in OSS DB and assesses its risk and defines what can or cannot be done with the OSS in relation to the project. Finally, it complies this (licencing, vulnerability and allowed project usage/integration info) into a Risk Assessment Report that is sends off to the Developer, and stores in the Integration Mng DB for use later.

PRC 1.1: OS Package Risk Assessment - This takes a new OS File Package, the project, it is to be used for and how it is going to be integrated into the project. It uses that to get SHA1 of Package, get licencing info, get vulnerability info (CPE and CVE), adds it to OSS DB and passes everything to PRC 1.1: Generate Risk Assessment Report.

PRC 1.1: Generate Risk Assessment Report - Extracts risk objects from the risk info recieved and determines company's usage policy for each one. It then complies this (licencing, vulnerability and allowed project usage/integration info) into a Risk Assessment Report that is sends off to the Developer, and stores in the Integration Mng DB for use later.

PRC 1.2: Extract Licensing Information (FOSSology) - Utilizes FOSSOLOGY to scan the OS Package for licences and then returns this info.

PRC 1.2: Gen OS Package SHA1 - Generates a SHA1 from the recieved OS Package and returns it.

PRC 1.2: Assess Risk Object Policy - Takes the recieved risk object and queries the Integration Mng DB for the allowed usage/integration info for that risk object, and then returns that information. If an unrecognized risk object is found, then the proccess requeries the database for the unknown risk policy, and returns that instead. 

PRC 1.2: Get OS Package CPE - Queries the NIST CPE Information DB for the OS Package's CPE and then stores it into OSS DB and sends it to PRC 1.2: Get The CVE from The OS CPE.

PRC 1.2: Get The CVE from The OS CPE - Queries the National Vulnerability Database for the recieved CPE's CVE, and then sends that back to PRC 1.1: OS Package Risk Assessment, for use.

PRC 1.3: Manage CPE Information (Daily Job) - Updates our local NIST CPE Information from the National Vulnerability Database, daily.

PRC 2.0: Submittal For Exception - Receives a Risk Assessment Report and an Exception Request and sends it to the project manager to approve use case given the Vulnerabilities, Licensing's effect on the project. It then takes the managers response (Approved Use Report) and sends it to be stored in the Integration Mng DB, as well as to the developer.

PRC 2.1: Request Usage Exception - Receives a Risk Assessment Report and an Exception Request and gets the related project's info, and sends the data on, to have an exception report generated.

PRC 2.1: Generate Exception Report - Generates an exception report, and sends it on, to get reviewed by a project manager.

PRC 2.1: Request Exception - Sends the Exception Report to the project manager, once a response is recieved from the manager, it is sent to the developer and stored in the Integration Mng DB.

PRC 2.2: Get Assessment Project Info - Recieves a Risk Assessment Report and queries the Project DB for the project info related to that assessment, and returns it.

PRC 3.0: Submittal To Project - Recieves source code for a project, evaluates that source code to find both proprietary and open source code, from the project and OSS databases, as well as any of the found open source code's risk and allowed usage info from the Integrated Mng DB. Using all this info, it determines, if the source code meets allowed use and if so what licensing obligations must be met. If allowed, obligations are met, it sends an Integration report to the developer and adds the source code file to the project DB.

PRC 3.1: Integrate New Project Code into Project - Recieves source code for a project, passes it along to determine allowed use. When approved use and compliance is returned it generates and sends an integration report to the developer. If it was approved it, finally,  adds the source code file to the project DB.

PRC 3.2: Search Code for Previously Existing Source - Sends the recieved source code off to be searched for Proprietary and OSS, and then sends the source code on to get any obligations fullfilled.

PRC 3.2: Find Proprietary Code in the Project Code File - Searches through the recieved source code for existing proprietary code from the Project DB and passes any found project files found.

PRC 3.2: Find OS Code in the Project Code File - Searches through the recieved source code for submitted open source software code from the OSS DB and passes any found open source found.

PRC 3.2: Determine Approved Use of OS Code - Gets any of the found open source code's risk and allowed usage info from the Integrated Mng DB. Using all this info, it determines, if the source code meets allowed use and if so what licensing obligations must be met. If allowed, meets obligations.





----------------------------------------------------
Data FLows:
----------------------------------------------------

----------------------------------------------------
(PRC 1)

OS Package - An Open Source File Package Obtained from outside the company.

OS Package: Query - An SQL Select Query for the OS CPE, for the given OS Package.

Project Name - The name of a Project.

Project Name: Query - An SQL Select Query for the Project ID (primary key) with the given Project Name.

Project ID - The Unique Primary Key of a project.

OS Useage Info - A structured data or file containing a meaningfull description of how the provided OS Package is planned on being integrated into the given project. Wheather it remain un edited, changed, or integrated with existing proprietary source code.

OS License - License information for the given Open Source File or Package.

OS License: Add - An SQL Update and/or Insert Into Query that adds the OS License information to a Project and/or Project file(s) in the Database.

OS Package SHA1 - Hash of the OS Package file (e.g. http://www.sha1-online.com/).

OS Package SHA1: Add - An SQL Update and/or Insert Into Query that adds the OS Package's SHA1 to a Project and/or Project file(s) in the Database.

OS CPE - A document that can be used to determine if an OS Package has any CVEs (Common Platform Enumeration – A standard naming scheme for software packages)

OS CPE: Query - An SQL Select Query for the open source package's CVE, that matches the given open source package's CPE.

OS CPE: Add - An SQL Update and/or Insert Into Query that adds the OS CPE information to a Project and/or Project file(s) in the Database.

OS CPE: Response - All the current CPEs from the National Vulnerability Database.

OS CPE: Request - A structured request to the National Vulnerability Database for all known CPEs in the Database.

OS CVE - The OS Package's Common Vulnerability Enumeration information.

OS CVE: Add - An SQL Update and/or Insert Into Query that adds the OS CVE information to a Project and/or Project file(s) in the Database.

Risk Info - A file or structured compilation of data, containing a meaningfull description of a OS Package's identified risk information. This includes risks identified within its CVE information, and its license information.

Risk Object - A file or structured data containing a meaningfull description of an identified risk from a given OS Package. This includes risks identified within both the open source package's CVE vulnerabilities, and the open source packages's licenses.

Risk Object: Query - An SQL Select Query for the given Risk Object's Risk Policy Information.

Risk Policy - A file or structured data containing a meaningfull description of the company's policies regarding the predefined allowed use of an OS Package containing the given risk.

Risk Assessment Report - A file, containing the meaningfull description of a OS Package's risk and use information and their related policies for the specified project. (Contains: OS Package SHA1, OS CVE, OS License, Risk Objects, Risk Policies, OS Usage Info and Project ID)

Risk Assessment Report: Add - An SQL Insert Into Query that adds the Risk Assessment Report File, containing the risk and use information related to the OS Package and the Project, to a Database.

----------------------------------------------------
(PRC 2)

Exception Request - A file, containing a fomal, meaningfull description from a developer, as to why a policy exception should be made, on a particular OS Package's Risk.

Project: Query - An SQL Select Query for Project Information given a Project ID.

Project: Info - Information about the project that requires an exception.

Risk Info: Unapproved - The Risk Information that has been marked as unapproved, from the Risk Assessment Report.

Exception Report - A file, containing the meaningfull description of a OS Package's risk information that has been marked as unapproved, from the Risk Assessment Report and written exception requests that identify why this can or needs to be overlooked.

Exception Report: Request - An sent request for followup and response from a project manager, pertaining to an included Exception Report.

Exception Report: Response - An Exception Request that has been approved or disapproved and describes why, from the project manager.

----------------------------------------------------
(PRC 3)

Project Code File - A source code file being submitted into a specified project.

Project Code File: Add - An SQL Insert Into Query that adds the Project's new source code file, to a Database.

Integration Report - A report that tells us whether or not the Project code file was successfully added to the Project DB.

Proprietary Code: Query - An SQL Select Query for Proprietary code found in the given Project Code File.

Proprietary Code Found - Proprietary Source Code and it's related project information found in the provided Project Code File.

OS Code: Query - An SQL Select Query for any OS Code files based upon the provided project source code file.

OS Code Found - Open Source Code and it's related Package information found in the provided Project Code File.

Licencing Obligations - Any obligations that may need to be addressed given any found OS's use.

OS Approved Use and Compliance - Whether the Project Code File can be used, and complies with all obligations and policies.



