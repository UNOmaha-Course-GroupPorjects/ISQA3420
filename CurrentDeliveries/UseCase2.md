## Title: Submittal For Use
**Primary Actor:** Corporate Developer

**Goal in Context:** A developer submits a package to the system, and it sucessfully creates a hash file, locates license and vulnerability information which is written to a database, then launches the risk assessment portion of the workflow.

__Stakeholders:__
  >-Corporate Developer: To submit package and file information to the system to determine if the code is acceptable for use.
  
__Preconditions:__
  >-The package or file is not already in the system, submission is not required if the package or file is already present.
  
  >-The file or package has a Common Platform Enumeration (CPE)
  
**Main Success Scenario:** The package or file is submitted to the database with relevant associated vulnerabilities and license information and a risk assessment report is provided back to the developer indicating whether the package or file is aceeptable to use.

**Failed End Conditions:** The package or file is not submitted to the database, the system is unable to locate the associated licesne anv vulnerability information, or the developer either does not receive a risk assessment report or the report is incomplete/innacurate.

**Trigger:** Corporate developer locates a package or file intended for use, and submits it to the system along with the associated project and intended use.
