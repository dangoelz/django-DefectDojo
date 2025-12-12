---
title: "About Engagements"
date: 2025-12-11
draft: false
type: docs
weight: 1
---

## About Engagements

![placeholder image](images/sla_settings.png)

## What is an Engagement? 

In DefectDojo’s product hierarchy, Engagements are the “buckets” that represent groups of related Tests within a specific Asset. 

Examples of Engagements include: 

* One-off penetration tests  
* Recurring monthly or quarterly scans  
* Bug bounty review periods  
* CI/CD pipeline runs (for teams who treat each pipeline run as its own engagement)  
* Code release cycles (e.g., “v4.2 release security review”)

Engagements sit below Assets and above Tests in the product hierarchy. As such, one’s access to an Engagement is determined by one’s access to the Asset that contains it.

### What Information can be Added to Engagements? 

As the containers that organize testing activity, Engagements can store or track a variety of data:

* Target start and end dates  
* Engagement type (e.g., “Pen Test,” “CI/CD,” “API Security Review”)  
* Description and scope notes  
* Status (ongoing, planned, completed, etc.)  
* Assignee / Lead  
* Associated Tests (scans, pen tests, manual tests, etc.)  
* Threat models or risk acceptance info  
* Tags  
* Files and notes  
* Environment details (e.g., staging vs. production)  
* Build IDs (if linked to CI/CD)  
* Historical data from past Tests within the Engagement   
* And more\! 

## Create Engagements 

### Engagement Types 

Prior to creating your Engagements, it’s important to note that there are two types: 

1) **Interactive Engagements** are typically meant for manual, human-driven testing that takes place over a set period of time. They’re focused on testing the application while the app is running and use an automated test, human tester, or any activity “interacting” with the application functionality. See [OWASP’s definition of IAST](https://owasp.org/www-project-devsecops-guideline/latest/02c-Interactive-Application-Security-Testing#:~:text=Interactive%20Application%20Security%20Testing,interacting%E2%80%9D%20with%20the%20application%20functionality.).

* Examples include: quarterly pentests, sprint reviews, manual QA, and bug bounties.  
* Interactive Engagements always have expiry dates. Expiry dates can be used for reporting or progress tracking using the Calendar, but otherwise have no impact on the Engagement, Findings or Tests therein.  
* You can continue to add Tests to an Engagement after it has expired.

2) **CI/CD Engagements** are for recurring integration with a CI/CD pipeline. They’re meant to import data as an automated action, triggered by a step in the release process.

* Examples include: GitHub Actions, GitLab CI, Jenkins, or other scanners running on every commit or merge.  
* CI/CD Reimports can also be triggered by cron jobs or other automation, they don’t strictly require a CI/CD pipeline to function.  
* The duration of a CI/CD Engagement is potentially infinite (unless you end-of-life a product or pipeline).   
* Each tool within a CI/CD engagement creates a persistent test into which updated results are continually reimported. 

## Create an Engagement (Pro)

In order to create an Engagement, you must first have created an Asset to contain it. Learn how to create an Asset here.

There are several ways to create an Engagement in the Pro version: 

1) Within the Engagements dropdown in the Manage section of the sidebar  
   1) You will have to select the Asset to which to attribute the Engagement when completing the New Engagement form  
2) The gear icon located at the top right corner of an Asset’s landing page  
3) The “+ New Engagement” button found in the list of Engagements within an Asset  
4) If you haven’t already created an Engagement within an Asset, you can do so while importing a scan. 

### Importing a Scan to an Engagement (Pro)

To manually import the results of scan, you can do so either in: 

* The gear icon located at the top right corner of an Asset’s landing page  
* The gear icon located at the top right corner of an Engagement’s landing page

## Create an Engagement (OS)

There are also multiple approaches to creating Engagements in the OS version of DefectDojo. As with the Pro version, each approach requires that you first create an Asset to contain the Engagement. 

Once you’ve created an Asset, you can add a new Interactive or CI/CD Engagement in the Engagements section of the Asset’s navigation bar.

### Importing a Scan to an Engagement (OS)

To manually import the results of scan, you can do so either: 

1) From the dropdown menu at the top right of the Tests section of an Engagement  
2) From the Findings section of the navigation bar on a Product  
3) While creating an Engagement

The first method requires that you have already created an Engagement. However, the second method does not. If you manually import the results of a scan into that Asset without first creating an Engagement, it will automatically create an Engagement entitled “Ad Hoc Import.”

If you wish for the results of a scan to be housed within a particular Engagement, use the first method, first creating/selecting that Engagement, viewing that Engagement’s landing page, and then clicking “Import Scan Results” from the dropdown menu in the top right corner of the Tests section.

[def]: ../assets/images/_index.png