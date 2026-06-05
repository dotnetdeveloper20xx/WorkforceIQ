# Phase 1 – Workforce Foundation & Organisational Structure

# Introduction

Welcome to the first implementation phase of WorkforceIQ.

This document is intentionally written for multiple audiences:

* Junior Developers
* Senior Developers
* Technical Leads
* Product Owners
* Business Owners
* Future Contributors

The goal is not simply to explain what we are building.

The goal is to explain why we are building it.

Understanding the business reason behind a feature is just as important as understanding the technical implementation.

A developer who understands the business will make better decisions than a developer who only understands the code.

---

# What Are We Building?

We are building the foundation of WorkforceIQ.

Think of this phase as pouring the concrete foundations of a skyscraper.

Nobody gets excited about foundations.

But if the foundations are weak, everything built later will eventually fail.

This phase establishes:

* Organisations
* Departments
* Employees
* Managers
* Reporting Structure
* Roles
* Job Titles
* Employee Profiles
* Career Interests
* Security Model
* Audit Framework

Every future phase depends on this information.

---

# Business Goal

Imagine a company with:

* 500 employees
* 50 managers
* 10 departments

The company wants answers to questions like:

Who works here?

Who reports to whom?

Who manages which team?

Which department does an employee belong to?

What role do they perform?

What career path are they interested in?

Before we can talk about promotion readiness or future leaders, we must know these basics.

---

# Real World Example

Let's use real people.

Employee:

```text
Afzal Ahmed
Senior Software Developer
Technology Department
```

Manager:

```text
Mumtaz Hussain
Engineering Manager
```

Executive:

```text
Gulshan Sheikh
Chief Executive Officer
```

WorkforceIQ needs to understand:

```text
Gulshan
    ↓
Mumtaz
    ↓
Afzal
```

Without this hierarchy:

* Appraisals cannot work
* Manager reviews cannot work
* Development plans cannot work
* Succession planning cannot work

---

# High Level Architecture

```text
Organisation
    ├── Departments
    │
    ├── Employees
    │
    ├── Managers
    │
    ├── Roles
    │
    └── Reporting Structure
```

This becomes the foundation of WorkforceIQ.

---

# Core Domain Entities

The Domain Layer should contain the following entities.

---

## Organisation

Represents a company using WorkforceIQ.

Example:

```text
Contoso Ltd
```

Properties:

```csharp
public class Organisation
{
    public Guid Id { get; private set; }

    public string Name { get; private set; }

    public string Industry { get; private set; }

    public string Country { get; private set; }

    public bool IsActive { get; private set; }
}
```

---

## Department

Example:

```text
Technology

Human Resources

Finance

Operations
```

Properties:

```csharp
public class Department
{
    public Guid Id { get; private set; }

    public Guid OrganisationId { get; private set; }

    public string Name { get; private set; }
}
```

---

## Role

Examples:

```text
Developer

Senior Developer

Engineering Manager

Director

CEO
```

Properties:

```csharp
public class Role
{
    public Guid Id { get; private set; }

    public string Name { get; private set; }

    public string Description { get; private set; }
}
```

---

## Employee

This becomes the heart of the platform.

Example:

```text
Afzal Ahmed
```

Properties:

```csharp
public class Employee
{
    public Guid Id { get; private set; }

    public string FirstName { get; private set; }

    public string LastName { get; private set; }

    public string Email { get; private set; }

    public Guid DepartmentId { get; private set; }

    public Guid RoleId { get; private set; }

    public Guid? ManagerId { get; private set; }

    public DateTime JoinedDate { get; private set; }

    public bool IsActive { get; private set; }
}
```

---

# Why We Store ManagerId

Many junior developers ask:

Why store ManagerId?

Because:

```text
Afzal
Reports To
Mumtaz
```

This creates hierarchy.

Example:

```text
CEO

 └── Director

      └── Manager

            └── Employee
```

Future phases depend heavily on this structure.

---

# Employee Profile

Do NOT confuse employee profile with employee appraisal.

This phase only stores profile information.

Examples:

```text
Bio

Career Interests

Location

Skills Summary

Professional Background
```

No ratings.

No assessments.

No scoring.

That comes later.

---

# Career Interests

This is important.

Employees should be able to express interests.

Example:

```text
Leadership

Architecture

People Management

Cyber Security

Product Development
```

Notice:

These are interests.

Not skills.

This distinction is important.

---

# Security Architecture

This phase introduces role-based security.

Roles:

```text
Employee

Manager

HR

Administrator

Executive
```

Each role receives different permissions.

---

# Example Permissions

Employee:

```text
View Own Profile

Edit Own Profile
```

Manager:

```text
View Team Members

View Reporting Structure
```

HR:

```text
Manage Employees

Manage Departments
```

Executive:

```text
Read Workforce Reports
```

---

# CQRS Structure

Following our architecture standards.

Commands:

```text
CreateEmployee

UpdateEmployee

CreateDepartment

UpdateDepartment

AssignManager

CreateRole
```

Queries:

```text
GetEmployee

GetDepartment

GetOrganisation

GetReportingStructure
```

---

# Example Command

```csharp
public record CreateEmployeeCommand(
    string FirstName,
    string LastName,
    string Email,
    Guid DepartmentId,
    Guid RoleId);
```

---

# Example Query

```csharp
public record GetEmployeeByIdQuery(Guid EmployeeId);
```

---

# Database Design

Tables:

```sql
Organisations

Departments

Roles

Employees

EmployeeCareerInterests

UserAccounts

Permissions
```

---

# Employee Table

```sql
CREATE TABLE Employees
(
    Id UNIQUEIDENTIFIER PRIMARY KEY,

    FirstName NVARCHAR(100),

    LastName NVARCHAR(100),

    Email NVARCHAR(255),

    DepartmentId UNIQUEIDENTIFIER,

    RoleId UNIQUEIDENTIFIER,

    ManagerId UNIQUEIDENTIFIER NULL,

    JoinedDate DATETIME2,

    IsActive BIT
)
```

---

# API Endpoints

Organisation

```http
GET /api/organisations

POST /api/organisations
```

Department

```http
GET /api/departments

POST /api/departments
```

Employee

```http
GET /api/employees

GET /api/employees/{id}

POST /api/employees

PUT /api/employees/{id}
```

---

# Angular Screens

Phase 1 Screens.

---

## Login

Authentication.

---

## Dashboard

Simple welcome screen.

---

## Employee Directory

Search employees.

---

## Employee Profile

View employee information.

---

## Department Management

Manage departments.

---

## Organisation Structure

Visual hierarchy.

---

# Organisation Chart

This becomes a valuable feature.

Example:

```text
CEO

 ├── Finance Director

 ├── Technology Director

      ├── Engineering Manager

           ├── Afzal Ahmed

           ├── Sarah Khan

           └── David Jones
```

---

# Audit Logging

Everything should be auditable.

Examples:

```text
Employee Created

Employee Updated

Manager Assigned

Department Changed
```

Store:

```text
Who

What

When

Old Value

New Value
```

This becomes critical in later phases.

---

# Definition Of Done

Phase 1 is complete when:

✓ Organisations can be created

✓ Departments can be managed

✓ Roles can be managed

✓ Employees can be managed

✓ Managers can be assigned

✓ Reporting hierarchy exists

✓ Security roles exist

✓ Audit logging exists

✓ Employee profiles exist

✓ Career interests exist

---

# AI Prompt For Implementing Phase 1

```text
You are a Senior Enterprise Solution Architect and Principal ASP.NET Core Developer.

Your task is to fully implement Phase 1 of WorkforceIQ.

Technology Stack:

- ASP.NET Core 10
- C#
- SQL Server
- Entity Framework Core
- CQRS
- MediatR
- FluentValidation
- Clean Architecture
- Angular 20
- Tailwind CSS
- DaisyUI

Requirements:

1. Create Clean Architecture solution structure.

2. Create Domain entities:

- Organisation
- Department
- Role
- Employee
- EmployeeCareerInterest

3. Create Entity Framework configurations.

4. Create database migrations.

5. Create CQRS commands and handlers.

6. Create CQRS queries and handlers.

7. Create repositories where required.

8. Create FluentValidation validators.

9. Create REST API endpoints.

10. Create Angular feature modules.

11. Create Angular routes.

12. Create employee directory page.

13. Create employee profile page.

14. Create organisation hierarchy page.

15. Create department management page.

16. Implement role-based authorization.

17. Implement audit logging.

18. Generate production-quality code.

19. Follow SOLID principles.

20. Follow Clean Architecture strictly.

Output every file completely.

Do not use placeholders.

Generate all entities, DTOs, validators, handlers, mappings, controllers, Angular pages, services, interfaces, SQL scripts, migrations, and tests required for a complete working implementation.
```

---

# Closing Thoughts

This phase may not look exciting.

There is no AI.

There are no dashboards.

There is no promotion readiness.

There is no succession planning.

But this phase creates the trusted organisational foundation that every future WorkforceIQ capability will depend upon.

Build this phase properly and every future phase becomes easier.

Build it poorly and every future phase becomes harder.
