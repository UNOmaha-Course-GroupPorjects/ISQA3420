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

PRC 1.2: Assess Risk Object Policy - Takes the recieved risk object and queries the Integration Mng DB for the allowed usage/integration info for that risk object, and then returns that information.

PRC 1.2: Get OS Package CPE - Queries the NIST CPE Information DB for the OS Package's CPE and then stores it into OSS DB and sends it to PRC 1.2: Get The CVE from The OS CPE.

PRC 1.2: Get The CVE from The OS CPE - Queries the National Vulnerability Database for the recieved CPE's CVE, and then sends that back to PRC 1.1: OS Package Risk Assessment, for use.

PRC 1.3: Manage CPE Information (Daily Job) - Updates our local NIST CPE Information from the National Vulnerability Database, daily.

PRC 2.0: Submittal For Exception - Receives a Risk Assessment Report and an Exception Request and sends it to the project manager to approve use case given the Vulnerabilities, Licensing's effect on the project. And then takes the managers response (Approved Use Report) and sends it to store in the Integration Mng DB, as well as to the developer

PRC 2.1: Request Usage Exception

PRC 2.1: Generate Exception Report

PRC 2.1: Request Exception

PRC 2.2: Get Assessment Project Info

PRC 3.0: Submittal To Project

PRC 3.1: Integrate New Project Code into Project

PRC 3.2: Search Code for Previously Existing Source

PRC 3.2: Find Proprietary Code in the Project Code File

PRC 3.2: Find OS Code in the Project Code File

PRC 3.2: Determine Approved Use of OS Code





----------------------------------------------------
Data FLows:
----------------------------------------------------

----------------------------------------------------
(PRC 1)

OS Package

OS Package: Query

Project Name

Project Name: Query

Project ID: Info

OS Useage Info

OS License

OS License: Add

OS Package SHA1

OS Package SHA1: Add

OS CPE

OS CPE: Info

OS CPE: Query

OS CPE: Add

OS CPE: Response

OS CPE: Request

OS CVE

OS CVE: Info

OS CVE: Add

Project Info

Risk Info

Risk Object

Risk Object: Query

Risk Policy

Risk Policy: Info

Risk Assessment Report

Risk Assessment Report: Add

----------------------------------------------------
(PRC 2)

Exception Request

Project: Query

Project: Info

Risk Info: Unapproved

Exception Report

Exception Report: Request

Exception Report: Response

----------------------------------------------------
(PRC 3)

Project Code File

Project Code File: Add

Integration Report

Proprietary Code: Query

Proprietary Code: Files

Proprietary Code: Found

OS Code: Query

OS Code: Files

OS Code: Found

OS Approved Use: Query

OS Approved Use: Info

Licencing Obligations

Project Code File

OS Approved Use and Compliance



