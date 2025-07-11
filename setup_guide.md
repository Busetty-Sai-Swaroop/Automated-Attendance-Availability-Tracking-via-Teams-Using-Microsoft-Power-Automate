# 🚀 Setup Guide – Automated Attendance & Availability Tracking via Teams Using Microsoft Power Automate

This guide helps you set up the **Automated Availability Flow** using Microsoft Power Automate, Microsoft Teams, and Excel Online.

---

## 🛠️ Prerequisites

- A Microsoft 365 account with:
  - Access to **Power Automate**
  - Access to **Microsoft Teams**
  - Access to **OneDrive for Business** or **SharePoint**
- Basic knowledge of Power Automate (Flows, Triggers, Actions)
- Excel Online with two tables:
  - ✅ **Team Member List**
  - ✅ **Availability Log**

---

## 📁 Step 1: Prepare Your Excel Files

### 1. Team Member List (Input)
Create an Excel file named `Members_List.xlsx` with the following columns:

| Name           | Email               |
|----------------|---------------------|
| Sai Swaroop    | sai@example.com     |
| Jane Doe       | jane@example.com    |

Place this file in OneDrive or SharePoint and convert the data to a **Table**.

### 2. Response Log (Output)
Create an Excel file named `Response_Log.xlsx` with a table containing:

| Name           | Email               | Availability Status | Timestamp              |
|----------------|---------------------|----------------------|-------------------------|
| Sai Swaroop    | sai@example.com     | Yes                  | 2025-06-26T10:01:22 AM  |

---

## ⚙️ Step 2: Import the Power Automate Flow

1. Go to [Power Automate](https://make.powerautomate.com/)
2. Click on **Import** > **Import Package (.zip)**
3. Select the file `AutomatedAttendance&AvailabilityTrackingviaTeamsUsingMicrosoftPowerAutomate` from the `Flow_Exports/` folder.
4. Reconnect the required services:
   - Excel Online (Business)
   - Microsoft Teams
5. Update file paths and table names in the flow to match your Excel files.

---

## 💬 Step 3: Configure Adaptive Card

- In the **“Post an Adaptive Card and wait for a response”** action, use the card from `Adaptive_Cards/Message.json`.
- The card should ask:
  > "Hi {Name}, Are you available today?" with Yes/No options.

---

## 🔁 Step 4: Test the Flow

1. Add a few entries to `Members_List.xlsx`
2. Run the flow manually or wait until 10:00 AM
3. Team members should receive the card in Teams
4. Check `Response_Log.xlsx` for captured responses

---

## ✅ You're Done!

Your system is now ready to automatically collect daily availability from your team via Teams and log it in Excel.