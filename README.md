# jazzClient
http client written in python to perform http requests against CLM (RQM RTC) server

headers:
OSLC-Core-Version 	2.0
Accept 	application/xml
Content-Type 	application/rdf+xml

useful urls

to get the project UIDs:
https://localhost:9443/qm/oslc_qm/catalog


OSLC API resources:
QM Root Services URL 	https://localhost:9443/qm/rootservices
QM Users 	https://localhost:9443/qm/oslc/users
QM Service Provider catalog (basically all QM Project Areas) 	https://localhost:9443/qm/oslc_qm/catalog
“JKE Banking (Quality Management)” project area 	https://localhost:9443/qm/oslc_qm/contexts/_7C2_YDQIEeKh2o37xigryw/services.xml
Test Plans 	https://localhost:9443/qm/oslc_qm/contexts/_7C2_YDQIEeKh2o37xigryw/resources/com.ibm.rqm.planning.VersionedTestPlan
Test Cases 	https://localhost:9443/qm/oslc_qm/contexts/_7C2_YDQIEeKh2o37xigryw/resources/com.ibm.rqm.planning.VersionedTestCase
Test Case #32 	https://localhost:9443/qm/oslc_qm/contexts/_7C2_YDQIEeKh2o37xigryw/resources/com.ibm.rqm.planning.VersionedTestCase?oslc.where=oslc:shortId=%2232%22
Test Cases (requesting partial representation title+creator in results) 	https://localhost:9443/qm/oslc_qm/contexts/_7C2_YDQIEeKh2o37xigryw/resources/com.ibm.rqm.planning.VersionedTestCase?oslc.properties=dcterms:title,dcterms:creator
Test Results 	https://localhost:9443/qm/oslc_qm/contexts/_7C2_YDQIEeKh2o37xigryw/resources/com.ibm.rqm.execution.ExecutionResult
Test Scripts 	https://localhost:9443/qm/oslc_qm/contexts/_7C2_YDQIEeKh2o37xigryw/resources/com.ibm.rqm.planning.VersionedExecutionScript
Test Script Steps (v4.0.6+) 	https://localhost:9443/qm/oslc_qm/contexts/_Vq7X0qK7EeOXe4hxHLy8DQ/resources/com.ibm.rqm.planning.ExecutionElement2
TERS/TCERs 	https://localhost:9443/qm/oslc_qm/contexts/_7C2_YDQIEeKh2o37xigryw/resources/com.ibm.rqm.execution.TestcaseExecutionRecord
TER/TCER #39 	https://localhost:9443/qm/oslc_qm/contexts/_7C2_YDQIEeKh2o37xigryw/resources/com.ibm.rqm.execution.TestcaseExecutionRecord?oslc.where=oslc:shortId=%2239%22



REST API resources:
Project Areas (for process related information) 	https://localhost:9443/qm/process/project-areas
Users/members of a Project Area 	https://localhost:9443/qm/process/project-areas/_7C2_YDQIEeKh2o37xigryw/members
Team areas of a Project Area 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/teamarea?abbreviate=false
Test Plans 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/testplan
Test Plan (#2) 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/testplan/urn:com.ibm.rqm:testplan:2
Test Plan (filtered by “System” title name and wildcard in the title) 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/testplan?fields=feed/entry/content/testplan%5Btitle=’System X’]/(title|description)&wildcard=X
Test Cases 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/testcase
Test Cases (filtered by a category) 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/testcase?fields=feed/entry/content/testcase/(title|description|category[@term=’Function’ and @value=’Data entry’])
Test Cases (filtered by a custom attribute value) 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/testcase/?fields=feed/entry/content/testcase%5BcustomAttributes/customAttribute/name=&#8221;custom1” and (customAttributes/customAttribute/value=”AAA” or customAttributes/customAttribute/value=”BBB“)]/*
Test Cases included in Test Suite #2 (filtered by a test suite) 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/testcase?fields=feed/entry/content/testcase/(*|testsuite[@href=’https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/testsuite/urn:com.ibm.rqm:testsuite:2′%5D)
Test Case (#32) 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/testcase/urn:com.ibm.rqm:testcase:32
Test Case (#33) with UUIDs (Categories, etc.) 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/testcase/urn:com.ibm.rqm:testcase:33?metadata=UUID
Keywords 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/keyword
Keyword (#3)
	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/keyword/urn:com.ibm.rqm:keyword:3
Keyword (filtered by title “JKE Logout”)  (v4.0.3+)
	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/keyword?fields=keyword%5Btitle=”JKE Logout”]
Test Case Execution Results 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/executionresult
Test Case Execution Result (#47) 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/executionresult/urn:com.ibm.rqm:executionresult:47
Test Case Execution Results (filtered by test case #14) 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/executionresult?fields=feed/entry/content/executionresult/testcase%5B@href=’https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/testcase/urn:com.ibm.rqm:testcase:14′%5D
Test Suite Execution Result (#267) 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/testsuitelog/urn:com.ibm.rqm:testsuitelog:267
TCERs 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/executionworkitem
TCERs (filtered by owner ‘Deb’) 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/executionworkitem?fields=feed/entry/content/executionworkitem%5Bowner=’deb’%5D
TCERs (filtered by test phase #4 – identifiers returned) 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/executionworkitem?fields=feed/entry/content/executionworkitem/(testphase%5B@href=’https://clmserver:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/testphase/urn:com.ibm.rqm:testphase:4′%5D|identifier)
TSER (#67) 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/suiteexecutionrecord/urn:com.ibm.rqm:suiteexecutionrecord:67
Test Environment (“TE13”) 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/configuration/TE13
Test Cells 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/testcell
Test Phase (#36) 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/testphase/urn:com.ibm.rqm:testphase:36
Test Phases (filtered by test phase name ‘S1’) 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/testphase?fields=feed/entry/content/testphase%5Btitle=”S1″%5D/identifier
Test Script (#31) 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/testscript/urn:com.ibm.rqm:testscript:31
Adapters 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/adapter
Adapter Task (#2) 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/tasks/urn:com.ibm.rqm:tasks:2
Attachment (#2) 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/attachment/urn:com.ibm.rqm:attachment:2
Attachments (in Test Case #38) 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/testcase/urn:com.ibm.rqm:testcase:38?fields=testcase/attachment
Test Plan, Test Case and Test Suite Templates 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/template
Test Plan Template (“Default”) 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/template/testplan/com.ibm.rqm.planning.templates.testplan.default
Project Properties (from the “Manage Project Properties” menu) 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/project/JKE+Banking+%28Quality+Management%29/settings
“Lab Resource and Channel Properties” (from the “Manage Project Properties” menu) 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/catalog
Lab resources (v4.0.2+) 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/labresource
Lab resources (#22) (v4.0.2+) Format: simple, tdm 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%292/labresource/urn:com.ibm.rqm:labresource:22
Lab resources (experimental, v4.0.5+) – for a complete interactivity, open this URL directly in a Browser 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/labresource?propertyDictionary=true
Lab resources groups (v4.0.2+) 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/resourcegroup
Requests (v4.0.2+) 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/request
Reservations (v4.0.2+) 	https://localhost:9443/qm/service/com.ibm.rqm.integration.service.IIntegrationService/resources/JKE+Banking+%28Quality+Management%29/reservation
