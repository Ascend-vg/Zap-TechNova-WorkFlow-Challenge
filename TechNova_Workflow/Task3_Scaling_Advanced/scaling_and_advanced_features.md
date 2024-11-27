# Advanced Features in Task 3

This document details the configuration and logic of two Zaps created for advanced implementation in Task 3: **Sales Rep Assignment and Comment Analysis (Zap 1)**,
 and **Follow-Ups (Zap 2)**.

---

## 1. Trigger Configuration
- **Tool Used**: Google Sheets  
- **Setup Details**:
  - **Spreadsheet**: `Lead_Scoring_System`
  - **Worksheet**: `Lead Scores`
  - **Trigger Column**: Any column (triggered when a new row is added).  
- **Condition**:  
  The workflow is triggered whenever a new form submission adds a row in the Google Sheets.

---

## 2. Zap 1: Sales Rep Assignment and Comment Analysis

### **Action 1: Fetch Sales Rep Details**
- **Tool Used**: Google Sheets  
- **Purpose**: Retrieve the sales reps' names and their current assignment counts from the `Sales Rep` worksheet.

### **Action 2: Calculate Minimum Assignment (Using Python)**
- **Tool Used**: Code by Zapier (Python)  
- **Purpose**: Determine the sales rep with the lowest assignment count to ensure even distribution of leads.  
- **Logic**:
  - Fetch the names and counts of all sales reps.
  - Identify the sales rep with the minimum count.
  - Increment the count by 1 for assignment.
  - Output the updated counter and the row ID where the increment needs to be written.

### **Action 3: Analyze Comments for Categorization**
- **Tool Used**: Zapier Formatter (Exact Pattern Matching)  
- **Purpose**: Analyze the "Comments" field to identify patterns indicating lead categories such as:
  - Technology
  - Finance
  - Healthcare
  - Retail

### **Action 4: Update Sales Rep Count**
- **Tool Used**: Google Sheets  
- **Purpose**: Write the incremented count for the assigned sales rep back into the `Sales Rep` worksheet.

### **Action 5: Write Assignment and Category**
- **Tool Used**: Google Sheets  
- **Purpose**:
  - Record the assigned sales rep’s name in the `Assigned Sales Rep` column of the `Lead Scores` sheet.
  - Write the categorized lead type (from comment analysis) in the `Category` column of the same sheet.

---

## 3. Zap 2: Follow-Ups

**Note**: This Zap runs **only after Zap 1** has executed. If Zap 1 has not run, the `Assigned Sales Rep` column in the `Lead Scores` sheet will contain null values, causing Zap 2 to fail.

### **Action 1: Fetch Assigned Sales Rep**
- **Tool Used**: Google Sheets  
- **Purpose**: Lookup the assigned sales rep for each lead from the `Lead Scores` sheet.

---

### Path Logic in Zapier

#### **Path 1: Urgency = Immediate (Within 1 Month)**
- **Condition**: The lead's "Urgency of Need" field is marked as **Immediate (within 1 month)**.
- **Actions**:
  1. **Format Timestamp**:
     - **Tool Used**: Zapier Formatter
     - Convert the lead's timestamp into a proper format and increment it by 1 day, scheduling follow-ups the next day.
  2. **Create Calendar Event**:
     - **Tool Used**: Google Calendar
     - Create a follow-up event in the assigned sales rep's calendar for the next day, with a time limit of 1 day to complete the follow-up.

#### **Path 2: Urgency = Short-Term (1-3 Months)**
- **Condition**: The lead's "Urgency of Need" field is marked as **Short-term (1-3 months)**.
- **Actions**:
  1. **Format Timestamp**:
     - **Tool Used**: Zapier Formatter
     - Convert the timestamp into a proper format and increment it by 7 days. This allows sales reps to prioritize immediate leads while preparing for short-term follow-ups.
  2. **Create Calendar Event**:
     - **Tool Used**: Google Calendar
     - Schedule a follow-up event in the assigned sales rep's calendar with a start time after 7 days and a time limit of 1 day.

---

## 4. Assumptions and Limitations

### **Assumptions**:
- Sales reps’ names and initial assignment counts are accurately maintained in the `Sales Rep` worksheet.
- Leads will always have valid timestamps and urgency details for follow-up scheduling.
- Zap 1 must run before Zap 2 to avoid null values in the `Assigned Sales Rep` column.

### **Limitations**:
- Handling ambiguous or missing data in the "Comments" field during categorization may reduce the effectiveness of comment analysis.

---