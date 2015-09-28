DFD Dictionary



-----------------------------------------------------
ENTITIES
-----------------------------------------------------
Developer - Internal employees in charge of developing, maintaining and integrating, internal, proprietary, as well as external, open source code. To be used in any software or project, for internal or external use, by the company.

Project Manager LVL 1 - A manager directly overseeing the related development project, This person is responsible for the project and all its parts including; risk, OS use, funding, etc.

OSS Repository / Community - This refers to the OSS Repositories such as Github.



-----------------------------------------------------
DATA STORES
-----------------------------------------------------
Inegration Mng DB - This contains the viability, SPDX manifests, and the approved (or allowed) usage of any piece of open source code a developer wishes to integrate into a project.

OSS DB - This contains a repository of the versions of received OS File Packages that have been submitted for usage approval, and defines how/where that open source is can be used in a project.

Project DB - This is the repository of internal, proprietary, as well as external, open source code, that is being used in any software or project, for internal or external use, by the company.



-----------------------------------------------------
PROCESSES
-----------------------------------------------------
Process OS Integration Info - This takes a new OS File Package, the project it is to be used for and how it is going to be integrated into the project, and then stores it in OSS DB and assesses its Viability (or Risk) to generate a report that is sends off to the Developer, the Integration Mng DB and for approval by the Project Manager.

Create SPDX Manifest - Takes the OS File Package and returns the SPDX Software Manifest(s) back for further processing and to store with the code in OSS DB

Identify Vulnerabilities from NIST - Takes the OS File Package and returns the found vulnerabilities in that OS code for further processing.

Approval Process - Receives a Viability (or Risk) Report and sends it to the project manager to approve use case given the Vulnerabilities, Licensing's effect on the project. And then takes the managers response (Approved Use Report) and sends it to store in the Integration Mng DB, as well as to the developer



-----------------------------------------------------
Data Flows
-----------------------------------------------------




