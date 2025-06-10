# 🧙 Lug Deploy Tracker (Beta)

[![Codacy Badge](https://app.codacy.com/project/badge/Grade/9e802cb50f2f44f28364efb1b68a0c1b)](https://app.codacy.com/gh/mpdigitals/lug-deploy-tracker-sfdc/dashboard?utm_source=gh&utm_medium=referral&utm_content=&utm_campaign=Badge_grade) [![Codacy Badge](https://app.codacy.com/project/badge/Coverage/9e802cb50f2f44f28364efb1b68a0c1b)](https://app.codacy.com/gh/mpdigitals/lug-deploy-tracker-sfdc/dashboard?utm_source=gh&utm_medium=referral&utm_content=&utm_campaign=Badge_coverage)

**Beta version of a 100% native Salesforce solution to visually track, analyze and review deployment activity over time**, complementing Salesforce’s default DeployRequest retention with extended historical tracking.
It also allows you to easily review **deployed components**, quickly identify **failed deployments**, access **deployment status** directly from deployment result records, and gain deeper visibility into your deployment process.

https://github.com/user-attachments/assets/fe78ea5e-d8f0-4544-bb6c-1fa737117af2

## Overview ✨

**Lug Deploy Tracker** is a Salesforce solution designed to track and analyze deployment activity by retrieving `DeployRequest` data via the Tooling API.  

It provides advanced scheduling, synchronization, and reporting features to help administrators and developers gain full visibility into past deployment activity.

This app is **heavily inspired** (in spirit and in look & feel) by the great [Nebula Logger](https://github.com/jongpie/NebulaLogger) — though much simpler and focused on deployment tracking.  
Some structural and UI ideas are also borrowed from [chat-gpt-sfdc](https://github.com/ArnasBaronas/chat-gpt-sfdc), a very well-structured LWC Salesforce project.

### Features ⚙️

- 🔍 Synchronize `DeployRequest` records using the Tooling API.
- 📊 Store detailed deployment results in custom objects:
  - `DeployResult__c`
  - `DeployResultComponent__c`
  - `DeployResultTest__c`
- ⏰ Configure automatic synchronization frequency (daily, hourly).
- 🎛️ View and manage settings via **Lightning Web Components** (LWC):
  - Schedule settings
  - Advanced options
  - Manual synchronization
- 🚥 Track progress of batch synchronization via Platform Events and progress bar.
  
---

## Dashboard Example 📊

Here's a visual example of a full **Deployment Dashboard** built using the results provided by this app:

![Dashboard](media/images/deploy_dashboard.png)

---

## Installation 📥

You can install **Lug Deploy Tracker** in your Salesforce org using one of the following links:

<div style="display: flex; justify-content: center; align-items: center; gap: 48px; margin: 16px 0;">
  <a href="https://login.salesforce.com/packaging/installPackage.apexp?p0=04tQy0000009mDVIAY" target="_blank" style="text-decoration: none;">
    <img src="https://img.shields.io/badge/Install%20in%20Developer%20Edition-Unlocked%20Package-brightgreen?style=for-the-badge" 
         alt="Install in Developer Edition"
         style="height: 30px;"/>
  </a>
  <a href="https://test.salesforce.com/packaging/installPackage.apexp?p0=04tQy0000009mDVIAY" target="_blank" style="text-decoration: none;">
    <img src="https://img.shields.io/badge/Install%20in%20Sandbox-Unlocked%20Package-brightgreen?style=for-the-badge" 
         alt="Install in Sandbox"
         style="height: 30px;"/>
  </a>
</div>

---

## Installation Steps 🛠️

1. **Before using the app, you must create a Named Credential** for Tooling API access.

👉 [How to create a Named Credential](https://help.salesforce.com/s/articleView?id=platform.perm_uapa_create_a_named_credential.htm&type=5)

2. **After installing Lug Deploy Tracker:**

- Open the app via **App Launcher**.
- Go to the **Advanced Options** tab.

![Advanced Options](media/images/deploy_advance.png)

- Select the Named Credential you just created.
- Configure advanced options:
    - Retrieve Components
    - Retrieve Tests
    - Retrieve Intermediate States
- Assign the **DeployAdminAccess** permission set to any users who should have access to the Lug Deploy Tracker app.

---

## Usage 🖥️

### Manual Synchronization

You can trigger sync manually by using the **Synchronization Settings** tab.

- If the **Start Date** field is left empty, the app will automatically retrieve data from the last 30 days.
- If the **End Date** field is left empty, the app will retrieve data up to today.

![Synchronization Settings](media/images/deploy_sync.png)

### Scheduled Synchronization

You can also configure periodic automatic sync:

- If you schedule synchronization to start at 16:00 with a frequency of 2 hours, the app will automatically retrieve DeployRequests from the last 2 hours starting from 16:00, and will repeat this process every 2 hours.
- The next scheduled execution time is always displayed in the form.

![Schedule Settings](media/images/deploy_schedule.png)

---

## Visual Results 🔍

### Deploy Results

Overview of the captured `DeployResult__c` records:

![Deploy Results](media/images/deploy_results.png)

### Deploy Result Details

Example of a `DeployResult__c` record details page:

![Deploy Result Details](media/images/deploy_details.png)

### Deploy Result Components

List view of `DeployResultComponent__c` records:

![Deploy Result Components](media/images/deploy_result_components.png)

### Deploy Result Components Related List

Related List of components on a `DeployResult__c` record:

![Deploy Result Components Related List](media/images/deploy_component_rl.png)

### Deploy Result Tests

List view of `DeployResultTest__c` records:

![Deploy Result Tests](media/images/deploy_result_tests.png)

### Deploy Result Tests Related List

Related List of tests on a `DeployResult__c` record:

![Deploy Result Tests Related List](media/images/deploy_test_rl.png)

---

## Next Steps 🚀

Planned features for upcoming versions:

- ⚙️ **Handling Partial Results in Batch Apex** to improve resilience on very large datasets.
- 🗑️ **Purge management**: implement automatic cleanup of old `DeployResult__c` records after configurable retention period.
- 📈 **Lines covered / FlowCoverage**: expose visual coverage metrics for both code and flows.
- 🗂️ **Component and Test Class Summary Views**:
  - Provide a clear **list of component names** that have errors or warnings (without duplicating full line-by-line error details).
  - Provide a clear **list of test classes** that have errors or coverage warnings (without showing individual test methods, which are already detailed elsewhere).
    
---

## Disclaimer ⚠️

This package is provided "as is", without warranties or guarantees of any kind, either express or implied.  
You assume full responsibility for any outcomes resulting from its use. The author and contributors shall not be liable for any direct, indirect, incidental, or consequential damages, or any data loss arising from the use of this package in any Salesforce environment (production or sandbox).

---

## Contact & Feedback 📬

Feedback, ideas, and contributions are very welcome!  
Feel free to reach out:

📧 **develop@mpdigitals.com**

---
