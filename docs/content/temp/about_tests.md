---
title: "About Tests"
date: 2025-12-11T20:46:29+01:00
draft: false
type: docs
weight: 1
---

Organizations → Assets → Engagement → **TEST** → Findings

## What is a Test? 

Tests are a grouping of activities conducted by engineers to attempt to discover flaws in an Asset. They are the final, most granular component of DefectDojo’s product hierarchy and serve as the container for the Findings that result from an execution of a security tool or manual assessment. 

Each Test belongs to one Engagement, which itself belongs to an Asset. As such, one’s access to a Test is determined by one’s access to the Asset that contains it.

### What Information can be Added to Tests? 

Tests store a variety of metadata that helps to document various components of each testing effort, such as: 

* Test type  
* Test title / name   
* Test description / notes  
* Timing information   
* The environment in which the Test was run (e.g., Development, Staging, Pre-Production, Production, etc.)  
* Version / Branch / Build Number  
* Personnel associated with the Test   
* Additional files that can be used for later audits or re-imports  
* And more\! 

### 

Ultimately, the metadata captured within each Test is intended to ensure full reproducibility, traceability, and historical context.

### Test Types 

DefectDojo supports two categories of Test Types:

1) **Parser-based Test Types**: These correspond to specific security scanners that produce output in formats like XML, JSON, or CSV. When importing scan results, DefectDojo uses specialized parsers to convert the scanner output into Findings.

2) **Non-parser Test Types**: These are used for manually created findings not imported from a scan file. The following Test Types appear in the “Scan Type” dropdown when creating a new test, but will not appear when selecting “Import Scan”:  
* API Test  
* Static Check  
* Pen Test  
* Web Application Test  
* Security Research  
* Threat Modeling  
3) Manual Code Review

Non-parser Test types should be used when you need to manually create Findings that require remediation but don’t originate from automated scanner output.

### CI/CD Metadata

When Tests are created or updated through a CI/CD pipeline, you’re able to include metadata from the pipeline run so that Tests can be properly linked to the code they scanned. This allows you to:

* Associate scan results with a specific commit or branch.  
* Track how Findings evolve across code changes.  
* Improve Deduplication by understanding when two scans apply to the same or different versions of the code.  
* Support auditability by showing exactly what code was scanned and when.

Common examples of metadata include 

* Version  
* Branch/Tag  
* Build ID  
* Commit Hash   
* Build ID  
* And more\! 

DefectDojo’s CLI and API accept these values during Import or Reimport so they can be stored directly in the resulting Test. This metadata can be used to identify commit hashes or anything associated with any relevant repository information associated with a CI/CD run. 

### Metadata, Reimport, and Scheduled Scans 

Scans may also be scheduled to run at routine intervals, such as those triggered by cron jobs. Because scheduled scans are not tied to repository activity, There’s no use for CI/CD metadata in this case because you’re not importing data from a CI/CD pipeline, but using Reimport is still useful if you prefer to keep a rolling record of your security posture within a single Test.

### Automated Reimport 

Although metadata can be updated manually through the Reimport Scan form, most automated environments will handle this by calling the  `/api/v2/reimport-scan/` endpoint directly or using the DefectDojo CLI (`defectdojo-cli reimport`) as part of the build process. This approach allows the pipeline to automatically attach metadata upon Reimport.

## Creating Tests

Tests can be automatically created when scan data is imported directly into an Engagement, resulting in a new Test containing the scan data. Tests can also be created in anticipation of planning future Engagements, or for manually entered security findings requiring tracking and remediation.

### Create a Test (Pro)

In order to make a Test, you must first have created the Engagement that will contain it, as well as the Asset that will contain the Engagement. Afterwards, there are several ways to create a Test: 

1) Within the Tests dropdown in the Manage section of the sidebar  
   1) You will have to select the pre-existing Engagement to which to attribute the Test when completing the New Test form.   
2) The gear icon located at the top right corner of an Asset’s landing page  
   1) “Import Scan” will automatically create a Test; if you haven’t already created an Engagement within an Asset prior to clicking “Import Scan,” you’ll have the opportunity to name it while completing the Import Scan form.   
3) The gear icon located at the top right corner of an Engagement’s landing page  
   1) “Import Scan” will automatically create a Test within the Engagement from which you accessed the “Import Scan” menu  
   2) “Add Test” will create a Test shell that doesn’t include a scan to test (which is useful in anticipation of planning future Tests, or for manually entered security findings requiring tracking and remediation)

If you used method 3b and later wish to manually import the results of a scan to a Test, you can do so by opening the Test, and clicking Reimport Scan. 

While completing the Import Scan form, you’ll may add metadata such as the version, branch tag, commit hash, build ID, and service. This will be reflected in the Import History section of the Test’s landing page, which will also include the same metadata from prior scan imports. 

## 

### Create a Test (OS)

There are several ways to create a Test in the OS version:

1) Select an Asset and click “Import Scan Results” from the Findings menu in the navigation bar   
2) Select an Engagement within an Asset, click the dropdown menu in the Tests subsection, and click either “Add Tests” or  “Import Scan Results”  
3) While creating an Engagement

Using the third method above, you can do the following while creating an Engagement:

* Immediately import scan results  
* Create a Test shell (into which you will later import a scan)  
* Do neither and simply create the Engagement by clicking “Done” 

You will have the opportunity to add metadata while either importing a scan or creating a Test shell. Any metadata will be reflected in the Import History section of the Test’s landing page.

### Add New Data to an Existing Test (Pro)

In order to add new data to an existing Test, open the Test to which you’re adding new data and click the “Reimport Scan” button. 

While completing the Reimport Scan form, you’ll have the option to update metadata for the scan being reimported, including the branch tag, build ID, commit hash, and version. These changes are reflected in the Import History section of the Test’s landing page. 

For example, in the below screenshot, the branch tag, build ID, commit hash, and version were all manually updated from “Branch Tag \#1” to “Branch Tag \#2,” “Build ID \#1” to “Build ID \#2,” etc. 

To edit the metadata of the most recently reimported scan, click the gear icon located at the top right corner of an Engagement’s landing page and select “Edit Test.” Note that it is only possible to edit the metadata of the most recently reimported scan.

### Add New Data to an Existing Test (OS)

In order to add new data to an existing Test, open the Test within its parent Engagement, open the dropdown menu to the right of the Documentation Test modal, and click “Re-Upload Scan.” 

While completing the resulting form, you’ll have the option to update metadata for the scan being reimported, including the branch tag, build ID, commit hash, and version. These changes are reflected in the Import History section of the Test’s landing page. 

For example, in the below screenshot, the branch tag, build ID, commit hash, and version were all manually updated from “Branch Tag \#1” to “Branch Tag \#2,” “Build ID \#1” to “Build ID \#2,” etc. 

To edit the metadata of the most recently reimported scan, click open the dropdown menu to the right of the Documentation Test modal and select “Edit Test.” Note that it is only possible to edit the metadata of the most recently reimported scan.