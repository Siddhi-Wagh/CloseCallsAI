# Architecture

## Overview

CloseCalls AI is a sales call intelligence and operations tool that integrates data from **Close CRM** to support call analytics, AI-assisted call outcome validation, phone number rotation, call-limit monitoring, and automated sales reporting.

The architecture consists of four main layers:

1. Data Integration
2. Data Processing & Business Logic
3. Analytics & Automation
4. User Interface & Notifications

---

## High-Level Architecture

```text
                         ┌─────────────────┐
                         │    Close CRM    │
                         │       API       │
                         └────────┬────────┘
                                  │
                                  ▼
                        ┌───────────────────┐
                        │ Data Extraction & │
                        │    Processing     │
                        └─────────┬─────────┘
                                  │
             ┌────────────────────┼────────────────────┐
             │                    │                    │
             ▼                    ▼                    ▼
      Call & Transcript      Phone Number         Sales Data
           Data               Management       & Opportunities
             │                    │                    │
             ▼                    ▼                    ▼
       AI-Assisted Call       Number Rotation      KPI Analysis
       Outcome Validation      & Call Limits            │
             │                    │                    │
             ▼                    ▼                    ▼
       Mismatch Detection     Alerts & Monitoring  Slack Webhook
             │                    │                    │
             └────────────────────┼────────────────────┘
                                  │
                                  ▼
                         CloseCalls AI Tool
                                  │
                                  ▼
                       Dashboards & Insights
```

---

# 1. Data Integration

The system retrieves sales and call-related data using the **Close CRM API**.

### Data Used

- Call records
- Call transcripts
- Phone numbers
- Sales activities
- Opportunities
- Deals
- Sales performance metrics

The API data is processed and used by different modules of the application.

```text
Close CRM
    ↓
REST API
    ↓
Sales & Call Data
    ↓
Application Processing
```

---

# 2. Phone Number Rotation Architecture

Before automating number rotation, approximately **30 days of phone number usage and spam-status data** was manually maintained.

### Data Preparation

```text
Phone Number Usage
       ↓
Google Sheets
       ↓
30 Days Historical Data
       ↓
Export to Excel
       ↓
Claude Code-Assisted
Pattern Analysis
```

The historical data was analyzed to identify observed patterns related to:

- Number usage
- Usage frequency
- Spam status
- Rest periods

Based on these patterns, the number rotation strategy was designed.

---

## Number Lifecycle

Phone numbers are managed across three operational states:

```text
        ┌───────────┐
        │  RESTING  │
        └─────┬─────┘
              │
              ▼
        ┌───────────┐
        │  WARM-UP  │
        └─────┬─────┘
              │
              ▼
        ┌───────────┐
        │  ACTIVE   │
        │  CALLING  │
        └─────┬─────┘
              │
              ▼
         Rotation Cycle
              │
              └──────────► RESTING
```

At a configured time each day, the system evaluates the rotation logic and displays the phone numbers selected for that day's calling activity.

```text
Scheduled Time
      ↓
Evaluate Number States
      ↓
Apply Rotation Logic
      ↓
Select Active Numbers
      ↓
Display Today's Numbers
      ↓
Sales Team Calling
```

---

# 3. Phone Call Limit Monitoring

Each phone number can have a configured daily calling limit.

The monitoring process tracks call activity and checks whether the configured limit has been reached.

```text
Phone Number
      ↓
Track Daily Calls
      ↓
Check Daily Limit
      ↓
Limit Reached?
   ↓           ↓
  NO          YES
   ↓           ↓
Continue     Alert Team
Monitoring       ↓
             Switch Number
```

## Monitoring Optimization

Monitoring does not run continuously for 24 hours.

Instead, monitoring starts approximately **two hours before the scheduled sales calling time**.

This design helps:

- Reduce unnecessary webhook activity
- Optimize webhook credit usage
- Align monitoring with business operations

```text
2 Hours Before
Calling Starts
      ↓
Start Monitoring
      ↓
Monitor Call Activity
      ↓
Check Limits
      ↓
Send Alert if Required
```

---

# 4. AI-Assisted Call Outcome Validation

Call transcripts are retrieved from Close CRM and analyzed using historical call outcome examples and training data.

The predicted outcome is compared with the outcome manually selected by the salesperson.

```text
Close CRM
     ↓
Call Transcript
     ↓
Historical Call
Outcome Examples
     ↓
AI-Assisted Analysis
     ↓
Predict Outcome
     ↓
Compare with
Salesperson Outcome
     ↓
   Match?
  ↙     ↘
Yes      No
 ↓        ↓
Valid   Highlight
        Mismatch
```

This workflow helps identify potential inaccuracies in manually recorded call outcomes.

---

# 5. Sales Analytics

Sales and calling data is processed to generate dashboards and performance insights.

### Key Metrics

- Total calls
- Connected calls
- Connection rate
- Call duration
- Positive and negative calls
- Wrong numbers
- Salesperson/ISA performance
- Opportunities created
- Deals created
- Deal value

### Analysis Dimensions

- Time and day
- Salesperson
- Lead source
- Contact source
- Call direction
- Call method

---

# 6. Slack Notification Architecture

Daily sales metrics are automatically sent to Slack using webhooks.

```text
Close CRM API
      ↓
Fetch Previous Day's Data
      ↓
Calculate Sales Metrics
      ↓
Create Daily Summary
      ↓
Slack Webhook
      ↓
Send Team Notification
```

### Metrics Reported

- Total calls
- Opportunities created
- Deals created

---

# 7. Development & Deployment Workflow

The project followed a Git-based collaborative development workflow.

```text
Feature Development
       ↓
Local Changes
       ↓
Git Commit
       ↓
Collaboration / Merge
       ↓
Resolve Merge Conflicts
       ↓
Test Server Deployment
       ↓
Testing & Validation
       ↓
Production Deployment
```

### Development Practices

- Git version control
- Regular commits
- Collaborative development
- Merge conflict resolution
- Testing before production deployment

---

# Technology Overview

| Layer | Tools / Technologies |
|---|---|
| CRM Data | Close CRM API |
| API Integration | REST APIs |
| Data Format | JSON |
| Historical Data | Google Sheets, Excel |
| AI-Assisted Development | Claude Code |
| Call Analysis | AI-assisted transcript analysis |
| Automation | Scheduled workflows |
| Notifications | Slack Webhooks |
| Version Control | Git |
| Testing | Test Server |
| Deployment | Production Server |

---

# Architecture Summary

CloseCalls AI follows a workflow where:

**Close CRM Data → Processing & Business Logic → AI/Automation/Analytics → Dashboards & Notifications**

The architecture combines historical data analysis, CRM API integration, AI-assisted call validation, phone number management, sales analytics, automation, and collaborative development practices to support sales operations.