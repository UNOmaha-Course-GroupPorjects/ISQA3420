## Title: Submit For Use
**Primary Actor:** Corporate Developer

**Goal in Context:** A developer submits a package to the system, and it sucessfully creates a hash file, locates license and vulnerability information which is written to a database, then launches the risk assessment portion of the workflow.

__Stakeholders:__
  >-Corporate Developer: To submit package and file information to the system to determine acceptable use.
  
  >-Corporate Manager: To have information about potential external source available for accetable use determinations.
  
__Preconditions:__
  >-The package or file is not already in the system, submission is not required if the file is already present.
  
  >-The file or package has a Common Platform Enumeration (CPE)
  
**Main Success Scenario:** The package or file is submitted to the database with relevant associated vulnerabilities and license information.

**Failed End Conditions:** The package or file is not submitted to the database, or the system is unable to locate the associated licesne anv vulnerability information.

**Trigger:** Corporate developer locates a package or file intended for use, and submits it to the system.
