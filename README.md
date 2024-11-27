# Zap-TechNova-WorkFlow-Challenge

## Overview
This repository contains the implementation of the **TechNova Lead Management Workflow Challenge**, a comprehensive solution to automate and optimize lead management processes using tools 
like Zapier, Google Sheets, Gmail, and Google Calendar. The project focuses on capturing leads, scoring them based on predefined criteria, handling edge cases, and implementing advanced workflows 
for scaling operations.

## Key Features
1. **Automated Lead Capture and Scoring**:
   - Leads are captured via Google Forms and scored based on attributes such as company size, budget, industry, and urgency.
2. **Edge Case Handling**:
   - Manages incomplete data, prioritizes high-value leads, and adjusts for time zones.
3. **Advanced Features**:
   - Assigns sales reps to leads using even distribution logic.
   - Analyzes lead comments for categorization.
   - Schedules follow-ups using Google Calendar based on urgency.

---

## Repository Structure
```
Zap-TechNova-WorkFlow-Challenge/
│
├── Task1_Basic_Lead_Capture/
│   ├── lead_scoring_system.js       # Logic for lead scoring automation.
│   ├── scoring_spreadsheet.xlsx     # Lead data with calculated scores.
│   ├── zap_screenshot.png           # Screenshot of Zapier workflow for Task 1.
│   ├── workflow_logic.md            # Detailed documentation of Task 1 workflow.
│
├── Task2_Edge_Cases/
│   ├── edge_case_handling.md        # Documentation for edge case management.
│   ├── zap_screenshot_edge.png      # Screenshots for Task 2 workflows.
│
├── Task3_Scaling_Advanced/
│   ├── advanced_features.md         # Documentation for advanced features in Task 3.
│   ├── zap_advanced_features.png    # Screenshot for advanced workflows.
│   ├── demo_video_link.txt          # Link to a demo video for Task 3 solutions.
│
├── README.md                        # Project overview and navigation.
└── .gitignore                       # Ignore unnecessary files.
```

---

## Tasks Breakdown

### Task 1: Basic Lead Capture and Scoring
- **Goal**: Automate lead scoring and segmentation using predefined criteria.
- **Highlights**:
  - Scores calculated based on company size, budget, industry, and urgency.
  - High-scoring leads (>70) receive welcome emails, while lower-scoring leads are added to a nurturing campaign.
- **Tools Used**: Zapier, Google Forms, Google Sheets, Gmail.

### Task 2: Handling Edge Cases
- **Goal**: Address issues such as incomplete submissions, high-value lead prioritization, and time zone adjustments.
- **Highlights**:
  - Flags incomplete leads and notifies TechNova.
  - Manages high-value leads with custom workflows.
  - Converts time zones for leads outside IST.
- **Tools Used**: Zapier, Google Sheets, Gmail.

### Task 3: Scaling and Advanced Implementation
- **Goal**: Enable scalable lead management by distributing leads and automating follow-ups.
- **Highlights**:
  - Assigns leads to sales reps using Python-based logic for even distribution.
  - Analyzes comments for lead categorization.
  - Schedules follow-ups in Google Calendar based on urgency levels.
- **Tools Used**: Zapier, Google Sheets, Google Calendar, Python.

---

## Setup Instructions
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/Ascend-vg/Zap-TechNova-WorkFlow-Challenge.git
   ```
2. **Review Files**:
   - Refer to markdown files (`.md`) for each task to understand the workflow and logic.
3. **Run Workflows**:
   - Configure Zapier with the provided scripts and screenshots.

---

## My Understanding
This project leverages automation to streamline lead management for TechNova, a SaaS company. The solution prioritizes scalability, efficiency, and adaptability, using a combination of tools 
to address both standard workflows and edge cases. Advanced features such as sales rep assignment and comment analysis demonstrate innovative use of Zapier and Python, making the solution 
robust for real-world applications.

---
