# Phase 6 – Promotion Readiness, Career Progression & Internal Mobility Platform

# Introduction

Welcome to Phase 6 of WorkforceIQ.

This is the phase where everything we have built so far starts producing real outcomes.

Let's remind ourselves what we already have.

---

# What We Have Built So Far

## Phase 1

Workforce Foundation

We know:

* Employees
* Managers
* Departments
* Roles
* Reporting Structure

---

## Phase 2

Evidence & Verification

We know:

* Achievements
* Contributions
* Competencies
* Manager Assessments
* Verified Evidence

---

## Phase 3

Employee Growth Platform

We know:

* Employee Goals
* Career Aspirations
* Development Plans
* Recognition

---

## Phase 4

AI Growth Companion

We know:

* Growth Recommendations
* Coaching Conversations
* Development Opportunities

---

## Phase 5

Learning Intelligence

We know:

* Learning Progress
* Certifications
* Mentorship
* Leadership Programmes

---

# The Big Question

At this point an employee might ask:

> I've completed the learning.

> I've gathered evidence.

> I've received recognition.

> I've followed my development plan.

> I've completed mentoring.

> I've gained certifications.

Now what?

This phase answers:

# When Am I Ready?

and

# What Is My Next Career Move?

---

# The Mission

The goal of this phase is simple.

Help employees understand:

```text
Where am I?

Where could I go?

How close am I?

What do I still need?
```

At the same time help managers and leadership identify:

* Promotion candidates
* Future leaders
* Internal mobility opportunities
* Succession candidates

This is where WorkforceIQ starts changing careers.

---

# The Philosophy

Most companies handle promotions poorly.

Example:

```text
Manager Opinion

↓

Promotion Decision
```

Sometimes this works.

Sometimes it creates:

* Bias
* Frustration
* Politics
* Lack of transparency

WorkforceIQ introduces something better.

---

# Evidence-Based Promotion Readiness

Promotions should be supported by:

```text
Verified Skills

+

Verified Achievements

+

Manager Assessments

+

Development Progress

+

Learning History

+

Leadership Evidence

+

Career Interests
```

No single factor decides.

No single person decides.

Everything contributes.

---

# Important Principle

WorkforceIQ does NOT promote employees.

Managers do.

Leadership teams do.

HR does.

The platform simply provides intelligence.

---

# What Are We Building?

Phase 6 introduces:

## Promotion Readiness Engine

## Career Progression Framework

## Internal Mobility Platform

## Role Readiness Assessment

## Talent Pools

## Career Gap Analysis

## Promotion Recommendations

## Opportunity Discovery

---

# Career Frameworks

The platform must understand how careers progress.

Example:

```text
Graduate Developer

↓

Junior Developer

↓

Developer

↓

Senior Developer

↓

Lead Developer

↓

Engineering Manager
```

Without this framework we cannot calculate readiness.

---

# New Domain Entity

## CareerFramework

```csharp
public class CareerFramework
{
    public Guid Id { get; private set; }

    public string Name { get; private set; }

    public string Description { get; private set; }
}
```

---

# Career Path Mapping

Example:

Current Role:

```text
Senior Developer
```

Possible Next Roles:

```text
Lead Developer

Engineering Manager

Solution Architect
```

WorkforceIQ maps relationships.

---

# Readiness Engine

One of the most important components in the entire platform.

---

# Example

Employee:

```text
Afzal Ahmed
```

Target Role:

```text
Engineering Manager
```

Required Competencies:

```text
Leadership

Communication

Budgeting

Stakeholder Management

People Development
```

Current Status:

```text
Leadership

4.3
```

Communication:

```text
4.1
```

Budgeting:

```text
2.5
```

Stakeholder Management:

```text
3.8
```

People Development:

```text
4.0
```

---

# Readiness Result

```text
Engineering Manager Readiness

78%
```

Not promoted.

Not approved.

Just informed.

---

# Readiness Breakdown

Employees should see exactly why.

Example:

```text
Strengths

Leadership

People Development

Communication
```

Development Areas:

```text
Budget Ownership

Commercial Awareness
```

Suggested Actions:

```text
Join Budget Planning

Lead Department Initiative
```

Transparency builds trust.

---

# Promotion Candidate Pools

Managers need visibility.

Example:

Engineering Department

Potential Promotion Candidates:

```text
Afzal Ahmed

78%
```

---

```text
Sarah Khan

74%
```

---

```text
David Jones

70%
```

Managers can start development conversations.

---

# Internal Mobility Platform

One of the biggest reasons employees leave:

They cannot see opportunities.

The company often hires externally.

Meanwhile internal talent remains invisible.

WorkforceIQ changes that.

---

# Example

Internal Opportunity:

```text
Technical Architect
```

The platform identifies:

```text
Afzal Ahmed

Match 82%
```

This creates visibility.

---

# Internal Opportunity Types

Not only jobs.

Examples:

### Project Leadership

### Mentorship Roles

### Architecture Committees

### Working Groups

### Internal Vacancies

### Future Leadership Programmes

Growth opportunities matter.

---

# Career Gap Analysis

Employees often ask:

> What am I missing?

WorkforceIQ answers.

Example:

Target Role:

```text
Engineering Manager
```

Current Readiness:

```text
78%
```

Missing:

```text
Budget Planning

Commercial Awareness

Strategic Planning
```

Now employees know exactly where to focus.

---

# AI Career Progression Companion

The AI Companion becomes more advanced.

Example:

Employee asks:

```text
How do I become an Engineering Manager?
```

AI responds:

```text
Current Readiness

78%

Recommended Next Steps

Join Budget Meetings

Lead Cross-Team Initiative

Complete Strategic Leadership Programme
```

Actionable guidance.

---

# Manager Promotion View

Managers receive:

### Promotion Candidates

### Development Needs

### Future Leaders

### Career Interests

### Readiness Trends

---

# Example Dashboard

```text
Promotion Ready

2
```

Future Candidates:

```text
5
```

Development Needed:

```text
4
```

Managers can prepare succession plans.

---

# Talent Pools

One of the strongest features.

Example:

Future Leaders Pool

Contains:

```text
Afzal Ahmed

Sarah Khan

David Jones
```

These employees receive focused development.

---

# Internal Talent Marketplace

The organisation can advertise:

### Vacancies

### Projects

### Leadership Opportunities

### Temporary Assignments

### Development Programmes

The platform automatically identifies suitable candidates.

---

# Employee Career Hub

This becomes one of the most visited screens.

Employee sees:

Current Role:

```text
Senior Developer
```

Potential Future Roles:

```text
Lead Developer

Engineering Manager

Solution Architect
```

Readiness:

```text
82%

78%

85%
```

Employees can visualise their future.

---

# Promotion Governance

Very important.

The platform must remain fair.

---

# Rules

Promotion readiness does NOT equal promotion.

Promotion requires:

### Business Need

### Leadership Approval

### Budget

### Vacancy

### Organisational Decision

The platform informs.

Humans decide.

---

# Anti-Bias Controls

To ensure fairness:

### Evidence Required

### Manager Justification Required

### Audit Trail

### Historical Records

### HR Moderation

### Transparent Calculations

Nobody should be surprised by outcomes.

---

# New Domain Entities

---

## PromotionReadiness

```csharp
public class PromotionReadiness
{
    public Guid Id { get; private set; }

    public Guid EmployeeId { get; private set; }

    public Guid TargetRoleId { get; private set; }

    public decimal ReadinessScore { get; private set; }
}
```

---

## InternalOpportunity

```csharp
public class InternalOpportunity
{
    public Guid Id { get; private set; }

    public string Title { get; private set; }

    public string Description { get; private set; }
}
```

---

## TalentPool

```csharp
public class TalentPool
{
    public Guid Id { get; private set; }

    public string Name { get; private set; }
}
```

---

## CareerFramework

```csharp
public class CareerFramework
{
    public Guid Id { get; private set; }

    public string Name { get; private set; }
}
```

---

# CQRS Commands

Examples:

```text
CreateCareerFramework

CalculatePromotionReadiness

CreateInternalOpportunity

CreateTalentPool

AssignEmployeeToTalentPool
```

---

# Queries

Examples:

```text
GetPromotionReadiness

GetCareerPathOptions

GetInternalOpportunities

GetTalentPools

GetCareerGapAnalysis
```

---

# Database Tables

```sql
CareerFrameworks

CareerFrameworkSteps

PromotionReadiness

InternalOpportunities

OpportunityMatches

TalentPools

TalentPoolMembers

CareerGapAnalysis
```

---

# API Endpoints

Career Progression

```http
GET /api/careers/frameworks

GET /api/careers/readiness
```

Promotion Readiness

```http
GET /api/promotions/readiness
```

Internal Opportunities

```http
GET /api/opportunities

POST /api/opportunities
```

Talent Pools

```http
GET /api/talent-pools
```

---

# Angular Screens

Phase 6 introduces:

---

## Career Hub

Employee career progression centre.

---

## Promotion Readiness Dashboard

Visual readiness analysis.

---

## Career Gap Analysis

Development requirements.

---

## Internal Opportunities

Opportunity marketplace.

---

## Talent Pools

Future leader visibility.

---

## Manager Promotion Dashboard

Promotion candidate insights.

---

# Employee Experience

What does Afzal receive?

### Career Visibility

### Promotion Readiness

### Development Guidance

### Internal Opportunities

### Future Career Options

For the first time he can clearly see:

```text
Where am I?

How close am I?

What should I do next?
```

---

# Manager Experience

What does Mumtaz receive?

### Promotion Candidates

### Future Leaders

### Team Development Visibility

### Succession Preparation

Managers can develop people proactively.

---

# HR Experience

HR receives:

### Talent Pools

### Promotion Analytics

### Internal Mobility Trends

### Leadership Pipeline Visibility

This becomes strategic workforce intelligence.

---

# Executive Experience

Executives can finally answer:

```text
Who are our future leaders?

Who is promotion ready?

Who should enter succession planning?
```

Without spreadsheets.

Without guesswork.

---

# Definition Of Done

Phase 6 is complete when:

✓ Career Frameworks exist

✓ Promotion Readiness Engine exists

✓ Career Gap Analysis exists

✓ Internal Mobility Platform exists

✓ Talent Pools exist

✓ Opportunity Discovery exists

✓ Career Hub exists

✓ Promotion Dashboards exist

✓ AI Career Guidance exists

✓ Anti-bias controls exist

✓ Promotion governance exists

---

# AI Prompt For Implementing Phase 6

```text
You are a Principal Enterprise Architect and Senior Full Stack Developer.

Implement Phase 6 of WorkforceIQ.

Technology:

- ASP.NET Core 10
- SQL Server
- Entity Framework Core
- CQRS
- MediatR
- Clean Architecture
- Angular 20
- Tailwind CSS
- DaisyUI

Requirements:

1. Create entities:

- CareerFramework
- CareerFrameworkStep
- PromotionReadiness
- InternalOpportunity
- OpportunityMatch
- TalentPool
- TalentPoolMember
- CareerGapAnalysis

2. Create EF Core configurations.

3. Create migrations.

4. Create CQRS commands and handlers.

5. Create CQRS queries and handlers.

6. Create REST APIs.

7. Create Angular screens:

- Career Hub
- Promotion Readiness Dashboard
- Career Gap Analysis
- Internal Opportunities
- Talent Pools
- Manager Promotion Dashboard

8. Implement readiness calculations.

9. Implement career framework mapping.

10. Implement opportunity matching.

11. Implement talent pool management.

12. Implement AI career progression recommendations.

13. Implement anti-bias and audit controls.

14. Follow Clean Architecture.

15. Follow SOLID principles.

16. Generate production-ready code.

Output complete files.

Generate entities, handlers, validators, APIs, Angular pages, services, migrations, SQL scripts, tests, and documentation required for a complete implementation.
```

---

# Closing Thoughts

Phase 1 answered:

> Who works here?

Phase 2 answered:

> What have they achieved?

Phase 3 answered:

> How can they grow?

Phase 4 answered:

> What should they do next?

Phase 5 answered:

> How do they get there?

Phase 6 answers:

> Are they ready for the next step?

This is the phase where employees begin seeing tangible career progression, managers begin identifying future leaders, and organisations start promoting from within using trusted evidence rather than guesswork.

For many organisations, this alone would justify investing in WorkforceIQ.
