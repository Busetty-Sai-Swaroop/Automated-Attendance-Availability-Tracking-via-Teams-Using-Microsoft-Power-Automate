
## Automated Attendance & Availability Tracking via Teams Using Microsoft Power Automate – Detailed Explanation

The Availability_Flow is a fully automated solution created using Microsoft Power Automate to collect daily availability responses from team members or Employees or interns or volunteer. The responses are captured through Adaptive Cards in Microsoft Teams and are automatically logged into an Excel sheet for tracking and reporting.

---

### 1. Trigger – Scheduled Daily

- Uses the **“Recurrence”** trigger.
- Runs **every day at [Specified Time] AM IST**.
- Ensures consistent daily execution without manual intervention.

---

### 2. Fetch Team Member List from Excel

- Uses **“List rows present in a table”** action.
- Reads team member data from an Excel file stored in **OneDrive or SharePoint**.
- Required columns: `Name`, `Email`.

---

### 3. Loop Through Each Team Member

- A **“Apply to each”** loop iterates over every team member.
- Personalizes message using their name and targets message using their email.

---

### 4. Send Adaptive Card in Teams Chat

- Uses **“Post an Adaptive Card and wait for a response”** to send an Adaptive Card in Microsoft Teams.

#### 🔹 Adaptive Card JSON Used:

```json
{
  "type": "AdaptiveCard",
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "version": "1.2",
  "body": [
    {
      "type": "TextBlock",
      "text": "Hi @{items('Apply_to_each')?['Name']}, Are you available today?",
      "wrap": true,
      "weight": "Bolder",
      "size": "Medium"
    },
    {
      "type": "Input.ChoiceSet",
      "id": "availability",
      "style": "expanded",
      "isRequired": true,
      "choices": [
        { "title": "Yes", "value": "Yes" },
        { "title": "No", "value": "No" }
      ]
    }
  ],
  "actions": [
    {
      "type": "Action.Submit",
      "title": "Submit",
      "data": {
        "submitLocation": "availability"
      }
    }
  ]
}
```

---

### 5. Capture the Response

- Captures the selected value and metadata:
  - Name
  - Email
  - Response (Yes/No)
  - Timestamp

---

### 6. Log the Response in Excel

- Uses **“Add a row into a table”** to log each response.
- Stores data in Excel with columns:
  - Name
  - Email
  - Availability Status
  - Timestamp

---

### 7. Purpose and Benefits

Feature | Description
|-------|--------------|
| Daily Automation | Avoids manual check-ins |
| Personalized | Uses name for personal message |
| Scalable | Works for small or large teams |
| Accurate | Logs responses with timestamp |
| Centralized | All data is stored in one place |

---

### 8. Tools Used

| Tool | Purpose |
|------|---------|
| Power Automate | Main automation engine |
| Microsoft Teams | Sends Adaptive Card |
| Adaptive Cards v1.2 | Collects responses |
| Excel Online (Business) | Stores input & output data |
| OneDrive/SharePoint | Hosts Excel files |

### Image of the Flow
![image](https://github.com/user-attachments/assets/dbf8ad9f-4b9d-4754-8935-6210e22eeee4)


