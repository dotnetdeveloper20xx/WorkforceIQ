# Phase 2 – Appraisal, Evidence Collection & Verification Engine

# Introduction

Welcome to Phase 2 of WorkforceIQ.

This is the phase where WorkforceIQ begins to separate itself from traditional HR systems.

Phase 1 gave us organisational structure:

* Organisations
* Departments
* Employees
* Managers
* Roles
* Reporting Hierarchy

Those things are important.

However, they only tell us:

> Who works here?

They do not tell us:

> What has this employee achieved?

> What skills have they demonstrated?

> What evidence exists?

> What potential do they have?

> Are they growing?

> Are they ready for greater responsibility?

Phase 2 begins answering those questions.

This phase creates the trust engine that powers every future capability.

Without this phase:

* Promotion Readiness cannot work
* Succession Planning cannot work
* Leadership Pipelines cannot work
* Workforce Intelligence cannot work
* Employee Growth cannot work

Everything depends on trusted evidence.

---

# The Business Problem

Let's imagine a real situation.

Employee:

```text
Afzal Ahmed
Senior Software Developer
```

Afzal says:

"I have strong leadership skills."

Question:

How do we know?

Did he:

* Lead a team?
* Mentor developers?
* Run projects?
* Manage stakeholders?

Or is it simply an opinion?

Traditional systems often rely on self-assessment.

WorkforceIQ does not.

Instead WorkforceIQ asks:

> Show us the evidence.

This phase introduces:

# Evidence Before Opinion

---

# Core Philosophy

Most appraisal systems work like this:

```text
Employee

↓

Self Assessment

↓

Manager Assessment

↓

Annual Review
```

WorkforceIQ works differently.

```text
Employee

↓

Evidence

↓

AI Analysis

↓

Manager Verification

↓

Verified Workforce Intelligence
```

This creates trust.

---

# What Are We Building?

Phase 2 introduces:

## Evidence Collection

## Achievement Tracking

## Manager Verification

## Competency Frameworks

## Appraisal Workflows

## Review Cycles

## Audit History

## Development Planning

---

# The New Workflow

WorkforceIQ now becomes a living system.

Not a yearly appraisal form.

Employees continuously contribute evidence.

Managers continuously validate.

The organisation continuously learns.

---

# Evidence Collection

This becomes one of the most important modules.

Employees can submit evidence.

Examples:

## Project Contribution

```text
Led CRM Migration Project

Delivered 3 weeks early

Managed 5 developers
```

---

## Achievement

```text
Reduced support tickets by 25%
```

---

## Mentoring

```text
Mentored two graduate developers
```

---

## Innovation

```text
Automated deployment process
saving 10 hours per week
```

---

## Certification

```text
AZ-305

Certified Scrum Master
```

---

# Important Rule

Employees provide evidence.

Employees do NOT provide scores.

No:

```text
Leadership = 9/10
```

No:

```text
Communication = 8/10
```

No:

```text
Stakeholder Management = 10/10
```

This is critical.

---

# New Domain Entities

This phase introduces several important entities.

---

## Achievement

Represents a measurable contribution.

```csharp
public class Achievement
{
    public Guid Id { get; private set; }

    public Guid EmployeeId { get; private set; }

    public string Title { get; private set; }

    public string Description { get; private set; }

    public DateTime AchievedDate { get; private set; }

    public AchievementStatus Status { get; private set; }
}
```

---

## Evidence

Represents supporting information.

```csharp
public class Evidence
{
    public Guid Id { get; private set; }

    public Guid AchievementId { get; private set; }

    public string Description { get; private set; }

    public EvidenceType Type { get; private set; }
}
```

---

## Competency

Represents organisational competencies.

Examples:

```text
Leadership

Communication

Technical Excellence

Problem Solving

Coaching

Project Delivery

Stakeholder Management
```

---

## AppraisalCycle

Represents formal review periods.

Example:

```text
2026 Annual Review

2026 Mid-Year Review
```

---

## ManagerAssessment

Stores manager evaluation.

```csharp
public class ManagerAssessment
{
    public Guid Id { get; private set; }

    public Guid EmployeeId { get; private set; }

    public Guid ManagerId { get; private set; }

    public Guid CompetencyId { get; private set; }

    public int Rating { get; private set; }

    public string Comments { get; private set; }
}
```

---

# Competency Framework

One of the biggest mistakes HR systems make is allowing every manager to invent their own scoring.

WorkforceIQ uses a structured competency framework.

---

# Example Framework

## Technical Competencies

```text
Technical Excellence

System Design

Problem Solving

Quality
```

---

## Leadership Competencies

```text
Leadership

Coaching

People Development

Decision Making
```

---

## Business Competencies

```text
Communication

Stakeholder Management

Commercial Awareness
```

---

## Delivery Competencies

```text
Planning

Execution

Ownership
```

---

# Standard Rating Scale

Keep it simple.

```text
1 = Developing

2 = Emerging

3 = Competent

4 = Strong

5 = Exceptional
```

Managers understand this immediately.

---

# AI Evidence Analysis

This is where AI enters WorkforceIQ.

AI never makes decisions.

AI assists.

Example:

Employee submits:

```text
Led migration project involving
5 engineers and multiple stakeholders.
```

AI suggests:

```text
Leadership

Project Delivery

Communication

Stakeholder Management
```

Manager still decides.

AI helps.

Humans verify.

---

# Verification Workflow

One of the most important workflows.

---

## Step 1

Employee submits achievement.

Status:

```text
Pending Review
```

---

## Step 2

Manager receives notification.

```text
Achievement Requires Review
```

---

## Step 3

Manager reviews evidence.

Options:

```text
Approve

Request Clarification

Reject
```

---

## Step 4

Decision recorded.

Audit history created.

---

## Step 5

Employee notified.

Example:

```text
Congratulations.

Your contribution to Project Phoenix
has been verified.
```

Recognition matters.

---

# Appraisal Workflow

Formal reviews happen periodically.

---

## Employee Preparation

Employee reviews:

* Achievements
* Learning
* Certifications
* Contributions

No scoring.

Only evidence.

---

## Manager Assessment

Manager reviews evidence.

Scores competencies.

Provides comments.

Provides development recommendations.

---

## Example

Leadership:

```text
Rating: 4

Comments:

Successfully led migration project.

Mentored junior staff.

Demonstrates strong leadership.
```

---

# Development Planning

Appraisals should not end with scores.

They should create growth.

Example:

Strengths:

```text
Leadership

Technical Delivery
```

Development Areas:

```text
Budgeting

Strategic Planning
```

Recommended Actions:

```text
Lead Cross-Team Initiative

Attend Leadership Programme
```

---

# HR Moderation

Managers are human.

Bias exists.

WorkforceIQ supports moderation.

Example:

Manager A:

```text
Everybody gets 5
```

Manager B:

```text
Nobody gets above 3
```

WorkforceIQ identifies unusual patterns.

HR reviews.

This improves fairness.

---

# Anti-Fraud Controls

This platform must be trusted.

---

## Rule 1

No self-scoring.

---

## Rule 2

Evidence required.

---

## Rule 3

Manager justification required.

---

## Rule 4

All changes audited.

---

## Rule 5

Historical records retained.

---

## Rule 6

No silent modifications.

---

# Audit Logging

Every action creates history.

Example:

```text
Achievement Submitted

Achievement Approved

Manager Assessment Updated

Competency Rating Changed
```

Store:

```text
Who

What

When

Old Value

New Value
```

This becomes invaluable later.

---

# CQRS Commands

Examples:

```text
CreateAchievement

SubmitEvidence

ApproveAchievement

RejectAchievement

CreateAppraisalCycle

SubmitManagerAssessment
```

---

# Example Command

```csharp
public record CreateAchievementCommand(
    Guid EmployeeId,
    string Title,
    string Description);
```

---

# Queries

Examples:

```text
GetAchievements

GetEmployeeEvidence

GetManagerAssessments

GetAppraisalCycle
```

---

# Database Tables

Phase 2 introduces:

```sql
Achievements

Evidence

Competencies

AppraisalCycles

ManagerAssessments

AssessmentComments

AchievementReviews

AuditHistory
```

---

# API Endpoints

Achievements

```http
GET /api/achievements

POST /api/achievements
```

Evidence

```http
POST /api/evidence
```

Assessments

```http
POST /api/manager-assessments

GET /api/manager-assessments
```

Appraisals

```http
GET /api/appraisal-cycles

POST /api/appraisal-cycles
```

---

# Angular Screens

Phase 2 Screens.

---

## Achievement Centre

Employee achievements.

---

## Evidence Submission

Evidence management.

---

## Manager Review Queue

Pending approvals.

---

## Competency Assessment

Manager scoring.

---

## Appraisal Workspace

Review process.

---

## Audit History

Historical changes.

---

# Employee Experience

What does Afzal get?

Afzal receives:

* Recognition
* Verified achievements
* Development plans
* Career visibility
* Encouragement

The system helps him grow.

---

# Manager Experience

What does Mumtaz get?

Mumtaz receives:

* Trusted evidence
* Structured reviews
* Team visibility
* Development planning tools

The system helps him develop talent.

---

# HR Experience

What does Sarah get?

Sarah receives:

* Fairness controls
* Appraisal visibility
* Competency analytics
* Organisational consistency

---

# Definition Of Done

Phase 2 is complete when:

✓ Employees can submit achievements

✓ Employees can submit evidence

✓ AI can analyse evidence

✓ Managers can review achievements

✓ Managers can approve or reject

✓ Competency framework exists

✓ Assessments exist

✓ Appraisal cycles exist

✓ Audit logging exists

✓ Development plans exist

✓ HR moderation exists

✓ No self-scoring exists

---

# AI Prompt For Implementing Phase 2

```text
You are a Principal Enterprise Architect and Senior ASP.NET Core Developer.

Implement Phase 2 of WorkforceIQ.

Technology:

- ASP.NET Core 10
- SQL Server
- EF Core
- CQRS
- MediatR
- FluentValidation
- Angular 20
- Tailwind CSS
- DaisyUI

Requirements:

1. Create entities:

- Achievement
- Evidence
- Competency
- AppraisalCycle
- ManagerAssessment
- AchievementReview
- DevelopmentPlan

2. Create EF Core configurations.

3. Create database migrations.

4. Create CQRS commands and handlers.

5. Create CQRS queries and handlers.

6. Create REST APIs.

7. Create Angular screens:

- Achievement Centre
- Evidence Submission
- Manager Review Queue
- Competency Assessment
- Appraisal Workspace
- Audit History

8. Implement AI evidence analysis service abstraction.

9. Implement approval workflow.

10. Implement audit logging.

11. Implement HR moderation capability.

12. Implement role-based authorization.

13. Follow Clean Architecture.

14. Follow SOLID principles.

15. Generate production-quality code.

Output every file completely.

Do not use placeholders.

Generate all entities, DTOs, handlers, validators, APIs, Angular pages, services, migrations, SQL scripts, tests, and documentation required for a complete implementation.
```

---

# Closing Thoughts

This phase is where WorkforceIQ becomes trustworthy.

Phase 1 told us who works here.

Phase 2 tells us what they have actually done.

From this point onwards we now have trusted organisational evidence.

Everything that follows—employee growth, promotion readiness, leadership development, succession planning, and workforce intelligence—will be built on top of this foundation.
