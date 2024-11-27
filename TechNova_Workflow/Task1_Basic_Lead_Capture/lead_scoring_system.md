# Workflow Logic for Lead Scoring System

## 1. Trigger Configuration
- **Tool Used**: Google Sheets  
- **Setup Details**:
  - **Spreadsheet**: `Lead_Scoring_System`
  - **Worksheet**: `Lead Scores`
  - **Trigger Column**: Any column (triggered when a new row is added).  
- **Condition**:  
  The workflow is triggered whenever a new form submission adds a row in the Google Sheets.

---

## 2. Actions and Logic

### **Action 1 - 4: Assign Scores**
- **Tool Used**: Zapier Formatter  
- **Purpose**: Assign scores based on individual criteria: Company Size, Annual Budget, Industry, and Urgency of Need.
- **Details for Each Column**:
  1. **Company Size**:
     - 1-50 employees: 10 points
     - 51-200 employees: 20 points
     - 201-1000 employees: 30 points
     - 1000+ employees: 40 points
  2. **Annual Budget for SaaS Solutions**:
     - Less than $10,000: 5 points
     - $10,000 - $50,000: 15 points
     - $50,001 - $100,000: 25 points
     - More than $100,000: 35 points
  3. **Industry**:
     - Technology: 20 points
     - Finance: 15 points
     - Healthcare: 10 points
     - Retail: 5 points
     - Other: 5 points
  4. **Urgency of Need**:
     - Immediate: 30 points
     - Short-term: 20 points
     - Medium-term: 10 points
     - Long-term: 5 points

### **Action 5: Calculate Lead Score**
- **Tool Used**: Zapier Formatter  
- **Purpose**: Calculate the total lead score by summing the values assigned for Company Size, Annual Budget, Industry, and Urgency.

### **Action 6: Lookup Row ID**
- **Tool Used**: Google Sheets Lookup  
- **Purpose**: Locate the row ID in the Google Sheets where the new lead entry was added.

### **Action 7: Write Lead Score**
- **Tool Used**: Google Sheets  
- **Purpose**: Write the calculated lead score into the corresponding row at column `Total Scores` in the `Lead Scores` worksheet.

---

## 3. Path Logic in Zapier

### **Path 1: High-Value Leads**
- **Condition**: Lead score > 70
- **Actions**:
  1. **Google Sheets**: Add the lead details into the `High-Value Leads` sheet.
  2. **Email**: Send a welcome email to the lead.  
     - **Subject**: Welcome to TechNova!
     - **Body**: A personalized note introducing TechNova and its offerings.

### **Path 2: Nurturing Leads**
- **Condition**: Lead score ≤ 70
- **Actions**:
  1. **Google Sheets**: Add the lead details into the `Nurturing Leads` sheet.

---

## 4. Assumptions and Limitations
- **Assumptions**:
  - All necessary fields (Company Size, Annual Budget, Industry, and Urgency) are filled in the Google Form.
  - Email addresses provided by leads are valid.
- **Limitations**:
  - The scoring system relies on static point allocation; it doesn't adapt dynamically to changes in business priorities.
  - Leads with missing information are not handled in this workflow (addressed in Task 2 for edge cases).

---