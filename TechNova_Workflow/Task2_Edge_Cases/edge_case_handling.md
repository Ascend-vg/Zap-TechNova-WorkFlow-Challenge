# Edge Case Handling

## 1. Trigger Configuration
- **Tool Used**: Google Sheets  
- **Setup Details**:
  - **Spreadsheet**: `Lead_Scoring_System`
  - **Worksheet**: `Lead Scores`
  - **Trigger Column**: Any column (triggered when a new row is added).  
- **Condition**:  
  The workflow is triggered whenever a new form submission adds a row in the Google Sheets.

---

## 2. **Handling Incomplete Data**
- **Tool Used**: Google Sheets  
- **Condition**:  
  The workflow identifies incomplete data when **Annual Budget for SaaS** or **Urgency of Need** is missing in the newly submitted row after a Google Form submission.
- **Actions**:  
  1. **Google Sheets**: The details of the incomplete lead are written into the `Incomplete Leads` sheet, including any missing values.
  2. **Email**: An email is sent to TechNova, highlighting the missing information and providing a direct link to review the details in the `Incomplete Leads` sheet.

### **Path 1**: Handling Incomplete Data  
- **Condition**: If either **Annual Budget** or **Urgency of Need** is missing from the row.
- **Actions**:
  - Write incomplete lead details to `Incomplete Leads` sheet.
  - Notify TechNova via email with a link to review the incomplete leads.

---

## 3. **Handling Priority Leads**
- **Tool Used**: Google Sheets  
- **Condition**:  
  A lead is marked as "Priority" if:
  - **Annual Budget for SaaS** is **$100,000**.
  - **Urgency of Need** is **Immediate** (within 1 month).
- **Actions**:  
  1. **Google Sheets**: Write the details of priority leads to the `Priority Leads` sheet.
  2. **Email**: Send an email to TechNova with the priority lead details and a direct link to review the `Priority Leads` sheet.

### **Path 2**: Handling Priority Leads  
- **Condition**: If **Annual Budget** = **$100,000** and **Urgency of Need** = **Immediate**.
- **Actions**:
  - Add priority lead details to the `Priority Leads` sheet.
  - Notify TechNova via email with a link to review the priority leads.

---

## 4. **Handling Different Time Zones**
- **Tool Used**: Zapier Formatter  
- **Condition**:  
  If the **Preferred Time Zone** does not contain **IST** but contains **EST**, **PST**, or **GMT**, the workflow enters this loop.
- **Actions**:  
  1. **Zapier Formatter**: Convert the **Timestamp** from the lead’s time zone (e.g., EST, PST, GMT) to the **Asia/Kolkata** time zone.
  2. **Google Sheets**: Write the lead details, along with the converted time, into the `Time Zone Management` sheet.
  3. **Google Calendar**: Create a calendar event in TechNova’s Google Calendar with the lead's details and a follow-up time limit of 1 day.

### **Path 3**: Handling Time Zones  
- **Condition**: If the **Preferred Time Zone** includes **EST**, **PST**, or **GMT**, but **IST** is missing.
- **Actions**:
  - Convert the lead’s **Timestamp** to **Asia/Kolkata** time zone using Zapier Formatter.
  - Write the converted details to the `Time Zone Management` sheet.
  - Create a Google Calendar event for a follow-up within 1 day.

---

## 4. **Assumptions and Limitations**
- **Assumptions**:
  - Leads will provide a valid time zone, either in **EST**, **PST**, **GMT**, or **IST**.
  - All required fields are completed in the form unless specified as incomplete.
- **Limitations**:
  - Time zone conversions depend on accurate time zone data provided by the lead.
  - The email notification system is only triggered if the required fields are missing or if a lead meets the criteria for priority.

---