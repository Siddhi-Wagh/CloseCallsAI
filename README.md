# CloseCalls AI : Sales Call Intelligence & Operations Tool.

## 🚀 Project Overview

**CloseCalls AI** is a sales operations tool built using data from the **Close CRM API**. It combines call analytics, AI-assisted call outcome validation, phone number management, automated monitoring, and Slack notifications to help sales teams improve efficiency and data quality.

The project was developed using **Claude Code for AI-assisted development**, with Git-based collaboration, testing, and deployment workflows.

---
## 📌 Key Skills Demonstrated

**Data Analysis · Data Cleaning · API Integration · AI-Assisted Development · Call Transcript Analysis · Automation · Webhooks · Sales Analytics · Excel · Git · Collaboration · Testing · Deployment**

---

## 🎯 Business Problem

Sales teams faced challenges with:

- Manual daily sales reporting
- Incorrectly marked call outcomes by salespersons
- Repeated overuse of phone numbers and potential spam-related issues
- Manual tracking of phone number usage, mostly ignored
- Lack of call-limit monitoring, leading to every number in spam

---

## ✨ Key Features

### 🤖 Call Outcome Validation
Analyzes call transcripts based on training data and compares the predicted call outcome with the outcome marked by the salesperson. Mismatches are highlighted for review.

### 🔄 Data-Informed Number Rotation
Maintained and analyzed **30 days of phone number usage and spam-status data**. Based on observed patterns, built a rotation system that manages numbers as:

**Active → Warm-Up → Resting**

The tool displays the numbers approved for calling each day at a scheduled time.

### 🚦 Daily Phone Call Limits
Tracks daily call limits for each phone number and notifies the sales team when a number reaches its configured limit.

Monitoring starts approximately **2 hours before calling hours** instead of running continuously, helping reduce unnecessary webhook credit usage.

### 📊 Sales Analytics
Provides insights into:

- Total and connected calls
- Connection rates
- Call performance
- Salesperson/ISA performance
- Opportunities and deals
- Calling trends by time and day
- Historical comparison Daily(last 7 days),weekly and monthly basis

### 🔔 Automated Slack Reporting
Fetches daily sales data and automatically sends important metrics such as:

**Total Calls | Opportunities Created | Deals Created**

using **Slack Webhooks**.

---

## 🔄 How It Works

```text id="9vrr6v"
                  CLOSE CRM API
                       │
                       ▼
               Sales & Call Data
                       │
                       ▼ 
                 Data Cleaning
        ┌──────────────┼──────────────┐
        ▼              ▼              ▼
   Call Transcript   Phone Numbers   Sales KPIs
        │              │              │
        ▼              ▼              ▼
   AI Outcome       Rotation &      Analytics
   Validation       Call Limits        │
        │              │              ▼
        ▼              ▼         Slack Webhook
   Mismatch         Alerts
   Detection
        │
        └──────────────┬──────────────┘
                       ▼
                  CloseCalls AI
```

---

## 🛠️ Tools & Technologies

| Area | Tools / Technologies |
|---|---|
| CRM Data | Close CRM API |
| APIs | REST APIs |
| Data | JSON, Excel, Google Sheets |
| AI-Assisted Development | Claude Code |
| Automation | Scheduled workflows |
| Notifications | Slack Webhooks |
| Version Control | Git |
| Collaboration | Git, Merge Conflict Resolution |
| Deployment | Test & Production Servers |

---


## 📸 Screenshots

### Sales Overview & Analytics
Overview:
<img width="1992" height="1112" alt="1  Overview" src="https://github.com/user-attachments/assets/9b78e0aa-43f6-42da-a0c6-dafc92e5c209" />
Trends:
<img width="1858" height="928" alt="6A" src="https://github.com/user-attachments/assets/d7c4e021-fdd5-480b-a704-4e9e2410e330" />
Comparison:
<img width="1858" height="928" alt="7A" src="https://github.com/user-attachments/assets/ba8de1e0-f09e-4282-8087-e0e5089671e9" />
Historical Comparison:
<img width="1858" height="928" alt="8A" src="https://github.com/user-attachments/assets/bed51fe6-41ae-4d66-b555-13ea2864ca04" />


### Phone Number Rotation & Monitoring

<img width="1991" height="1006" alt="2 Daily Use Numbers" src="https://github.com/user-attachments/assets/96b3f0e1-bb68-4295-9392-531479a26286" />
<img width="1995" height="999" alt="3 Number Rotation" src="https://github.com/user-attachments/assets/8682745c-4576-4cac-b539-3a02786ad94e" />


### Call Outcome Validation

<img width="1991" height="994" alt="4 Call Outcome Validation" src="https://github.com/user-attachments/assets/3c6497cb-fd6b-4949-98b3-80e8fe02a3d7" />


### Opportunities & Deals 

<img width="1994" height="1001" alt="5 Opportunities" src="https://github.com/user-attachments/assets/f694cf0b-aa7e-4e37-aeb6-d6aa957a6b7d" />

---

## 🔒 Privacy Note

This repository is a **portfolio showcase**. Proprietary source code, API credentials, customer information, call transcripts, phone numbers, and internal infrastructure details are not included.
The following information has been anonymized or excluded:

- Sales representative names 
- Customer information 
- Sensitive company information
   
- **Screenshots and examples are included for portfolio demonstration purposes.**

