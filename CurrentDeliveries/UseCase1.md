## Title: Submittal for Exception
**Primary Actor:** Project Manager

**Goal in Context:**  The project manager is able to review license and vulnerability information for the reqeusted exception, review it in context against existing policy, and provide a response to the requesting developer on whether the exception request is approved or denied.

__Stakeholders:__
  >-Project Manager:  To determine receive clear information on the requested exception, including identified risks, and determine if an exception can be made. 
  
  >-Developer: To gain approval for for exception to be made to existing policy, in the context of the project that open source package is intended to be used in.  

__Preconditions:__
  >-Relevant file/package with licesne and vulnerability information was previously retrieved successfully and that information is in the OSS database. 
  
  >-A risk assessment report has been previously generated.
  
  >-Proper project information is in the project database.  
  
  >-Developer provided intended use and the correct project name when generating the risk assessment report.  

**Main Success Scenario:**  Project manager receives required information in the exception report, approves or denies the exception request, and a response is returned to the developer.

**Failed End Conditions:**  Project manager does not receive the request, request is missing critical information needed to determine whether the request is approved, a response of approval/denial is not received by the developer.

**Trigger:**  Developer submits an exception request along with a previously generated risk assessment report.
