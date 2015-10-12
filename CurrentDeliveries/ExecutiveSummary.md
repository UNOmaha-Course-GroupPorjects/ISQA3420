# ISQA3420: Executive Summary

### Overview
Open source code frequently and freely enters the organization.  Open source saves our developers time and organization money, but with that source comes inherent risk. Source code contains vulnerabilities and license considerations that must be managed to ensure our development remains viable and secure. Failure to the address these issues leaves us vulnerable to license requirements that would force us to share vital development secrets with our competitors.  Weak code brought in from external source leaves our products subject to the same risk.

##**Implementation**
____________________
###Risk Logging
To manage this risk, a system has been developed to track and log risks and allow for managerial review and approval of all external source brought in by our developers. When our developers bring in external source, they will submit the package containing the source, along with standard naming (CPE) information, information on the project which it will be utilized in, and the intended use within that project. The system will submit the package to a FOSSology cheking utility and the National Vulnerability Database to retrive any known licenses and vulnerabilities.  The system will break the package down to the file level, generate hashes for each, and record those hashes along with the associated license, vulnerability score (CVE), and CPE into an internal database.

###Risk Assessment
The system will generate a risk assessment from the initial submittal which is sent to developer who submitted the original request and is logged into an integration management database. 


