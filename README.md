# ServiceNow Administration Fundamentals — Capstone Project

![ServiceNow](https://img.shields.io/badge/ServiceNow-Xanadu-002B49?style=flat&logo=servicenow)
![Build](https://img.shields.io/badge/Status-Completed-success)
![Type](https://img.shields.io/badge/Artifact-Update%20Set-blue)

Comprehensive end-to-end implementation of the **ServiceNow Administration Fundamentals Capstone Project**. This repository contains the complete XML Update Set, detailed task breakdowns, platform configurations, and flow automation deliverables.

---

## 📌 Executive Summary

This project demonstrates core system administration capabilities across the ServiceNow platform, covering:
- **Data Modeling & Form Design:** Custom Incident fields, choices, and views.
- **User Administration & Security:** Nested group hierarchies, roles, and manager assignments.
- **Process Automation:** Service Catalog customization and multi-stage Flow Designer workflows.
- **Knowledge Management:** Knowledge Base setup and publishing workflows.
- **Analytics & Reporting:** Platform Analytics (PAR) visualizations, interactive dashboards, and scheduled exports.

---

## 📂 Repository Contents

| File Name | Description |
| :--- | :--- |
| `sys_remote_update_set_*.xml` | Exported ServiceNow Update Set containing all 18 customer updates for the Capstone project. |
| `README.md` | Complete project overview, architecture, and task documentation. |

---

## 🛠️ Detailed Implementation Breakdown

### 🎯 Task 1: Incident Management Configuration
- Added custom field `sFone Model` (String, Small length: 40) to the Incident table.
- Configured the **Default View** on the Incident form, placing `sFone Model` directly under `Configuration item`.
- Expanded the `Category` choice list to include `sFone`.
- Created a Non-P1 sFone Incident record to verify form layout and field behavior.

### 👥 Task 2: User Administration & Security
- Created a child group **Strawberry Support** under the existing **Service Desk** parent group.
- Assigned **Fred Luddy** as the group manager.
- Granted the `itil` role to the **Strawberry Support** group.
- Populated group membership with users (Beth Anglin, Bud Richman, David Loo, Kara Prince, Waldo Edberg).
- Set **Fred Luddy** as the direct manager in **Kara Prince's** user profile.

### ⚡ Task 3: Service Catalog & Flow Automation
- Imported the `cd_sfone_catalog_item.xml` Update Set for the **Strawberry sFone** catalog item.
- Built a multi-stage automated workflow (**Strawberry Workflow**) in **Flow Designer**:
  1. **Manager Approval Stage:** Routes request to the requester's direct manager.
     - *Rejected Path:* Sets state to Rejected, triggers automated email notification, and terminates flow.
     - *Approved Path:* Sets state to Approved and proceeds to catalog tasks.
  2. **Sequential Catalog Tasks:**
     - **Task 1:** Order sFone (Assigned to *Procurement*).
     - **Task 2:** Configure sFone software (Assigned to *Software*).
     - **Task 3:** Deliver sFone (Assigned to *Service Desk*).
  3. **Completion:** Auto-closes the Request Item (RITM) upon task resolution.

### 📚 Task 4: Knowledge Base Administration
- Managed Knowledge Base settings, user criteria, and publishing workflows.
- Configured access controls and knowledge submission processes.

### 🔔 Task 5: Task Assignment & Communication
- Created custom **Email Notifications** (e.g., P1 sFone Incident alerts).
- Configured related list layouts, dictionary overrides, and system properties to enhance communication workflows.

### 📊 Task 6: Platform Analytics & Scheduled Visualizations
- Created **Platform Analytics (PAR)** Data Visualizations (e.g., *Active sFone Incidents by Priority*).
- Added visualizations to interactive dashboards and set role permissions.
- Configured **Scheduled Exports** (`sysauto_par`) to automatically email PDF report exports to stakeholders.

---

## 🚀 How to Import and Deploy This Update Set

If you want to apply these configurations to your ServiceNow personal developer instance (PDI):

1. **Download XML:** Download `sys_remote_update_set_*.xml` from this repository.
2. **Elevate Roles:** Log in to your ServiceNow instance as System Administrator (`admin`).
3. **Retrieve Update Set:**
   - Navigate to **System Update Sets > Retrieved Update Sets**.
   - Click the **Import Update Set from XML** related link.
   - Upload the downloaded `.xml` file.
4. **Preview and Commit:**
   - Open the retrieved update set record: **System Administration Fundamentals-Capstone Project**.
   - Click **Preview Update Set** to verify no conflicts exist.
   - Click **Commit Update Set** to deploy all 18 customizations to your instance.

---

## 📄 License & Acknowledgments

This project was built as part of the **ServiceNow Administration Fundamentals** course (Xanadu Release). All trademarks and platform features belong to **ServiceNow, Inc.**
