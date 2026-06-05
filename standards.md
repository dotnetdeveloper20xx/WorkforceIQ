# standard.md

# WorkforceIQ Coding Standards & Engineering Best Practices

## Purpose Of This Document

This document defines the engineering standards for WorkforceIQ.

It is written from the viewpoint of a Technical Director, Senior CTO, Lead Architect, and Principal Engineer.

Every developer, contributor, and AI coding assistant working on WorkforceIQ must follow these standards.

The goal is simple:

Build code that can survive serious enterprise code review.

WorkforceIQ is not a throwaway demo application. It is a portfolio-grade enterprise platform designed to demonstrate strong architecture, clean code, maintainability, security, scalability, and professional software engineering discipline.

This document must be read before implementing any phase, feature, class, API, database table, Angular component, or AI integration.

---

# Core Engineering Principles

## 1. Business First, Code Second

Every technical decision must support the business domain.

WorkforceIQ is about employee growth, evidence verification, appraisals, promotion readiness, succession planning, workforce intelligence, and strategic alignment.

Do not create generic CRUD screens without understanding the workflow.

Every feature must answer:

* Who uses this?
* Why do they need it?
* What decision does it support?
* What business value does it create?

If the feature does not support the business workflow, it should not be built.

---

## 2. Clean Architecture Must Be Respected

The solution must follow Clean Architecture.

The dependency direction must always point inward.

The Domain layer must not depend on Infrastructure.

The Application layer must not depend on Web UI.

The API must not contain business rules.

The Angular frontend must not duplicate backend business rules.

Expected solution structure:

```text
src/
  WorkforceIQ.Domain
  WorkforceIQ.Application
  WorkforceIQ.Infrastructure
  WorkforceIQ.Api
  WorkforceIQ.Web

tests/
  WorkforceIQ.UnitTests
  WorkforceIQ.IntegrationTests
  WorkforceIQ.ArchitectureTests
```

Layer responsibilities:

| Layer          | Responsibility                                                            |
| -------------- | ------------------------------------------------------------------------- |
| Domain         | Core business entities, value objects, domain rules, enums                |
| Application    | CQRS commands, queries, handlers, validators, interfaces, DTOs            |
| Infrastructure | EF Core, SQL Server, external services, AI providers, email, file storage |
| API            | Controllers, authentication, middleware, request/response handling        |
| Web            | Angular frontend, UI components, routes, state, API clients               |

---

# ASP.NET Core Standards

## API Design

All APIs must be clear, predictable, and RESTful.

Good examples:

```http
GET /api/employees
GET /api/employees/{id}
POST /api/employees
PUT /api/employees/{id}
DELETE /api/employees/{id}
```

Avoid unclear routes:

```http
POST /api/doEmployeeStuff
GET /api/getAllThings
```

API endpoints should be grouped by business capability.

Examples:

```text
/api/employees
/api/achievements
/api/appraisals
/api/learning-pathways
/api/promotion-readiness
/api/succession-plans
/api/workforce-intelligence
```

Controllers must remain thin.

Controllers should:

* Validate authentication
* Accept requests
* Send commands or queries through MediatR
* Return appropriate responses

Controllers must not:

* Contain business logic
* Query DbContext directly
* Perform calculations
* Build complex responses manually

---

## Command And Query Responsibility Segregation

WorkforceIQ must use CQRS.

Commands change state.

Queries read state.

Examples:

```csharp
public sealed record CreateEmployeeCommand(
    string FirstName,
    string LastName,
    string Email,
    Guid DepartmentId,
    Guid RoleId
) : IRequest<Guid>;
```

```csharp
public sealed record GetEmployeeByIdQuery(
    Guid EmployeeId
) : IRequest<EmployeeDto>;
```

Handlers must be focused and small.

One handler should do one thing well.

---

## Validation

All incoming commands must use FluentValidation.

Validation belongs in the Application layer.

Example:

```csharp
public sealed class CreateEmployeeCommandValidator
    : AbstractValidator<CreateEmployeeCommand>
{
    public CreateEmployeeCommandValidator()
    {
        RuleFor(x => x.FirstName)
            .NotEmpty()
            .MaximumLength(100);

        RuleFor(x => x.Email)
            .NotEmpty()
            .EmailAddress();

        RuleFor(x => x.DepartmentId)
            .NotEmpty();

        RuleFor(x => x.RoleId)
            .NotEmpty();
    }
}
```

Do not place validation only in Angular.

Frontend validation improves user experience.

Backend validation protects the system.

Both are required.

---

## Error Handling

Use consistent error handling.

The API must return meaningful responses.

Examples:

| Situation          | HTTP Status               |
| ------------------ | ------------------------- |
| Validation failure | 400 Bad Request           |
| Unauthenticated    | 401 Unauthorized          |
| Forbidden          | 403 Forbidden             |
| Not found          | 404 Not Found             |
| Conflict           | 409 Conflict              |
| Unexpected error   | 500 Internal Server Error |

Do not expose stack traces to users.

Use structured logging for internal diagnostics.

---

## Logging

Use structured logging.

Log useful business events.

Examples:

* Employee created
* Achievement submitted
* Achievement approved
* Manager assessment completed
* Promotion readiness calculated
* Succession plan updated

Avoid noisy logs.

Do not log sensitive personal data unnecessarily.

---

## Security

Security must be designed from the start.

WorkforceIQ contains sensitive employee data.

Minimum security standards:

* Authentication required for protected APIs
* Role-based authorization
* Manager can only see own team unless HR or Executive
* Employee can only edit own profile evidence
* HR can manage appraisal frameworks
* Executives can view aggregated dashboards
* All sensitive actions must be audited

Never trust the frontend.

All permissions must be enforced on the backend.

---

# Domain Modelling Standards

## Entities Must Represent Business Concepts

Do not create vague entities.

Bad:

```csharp
public class DataItem
{
}
```

Good:

```csharp
public class Achievement
{
}
```

Good domain entities:

* Employee
* Department
* Achievement
* Evidence
* AppraisalCycle
* ManagerAssessment
* LearningPathway
* PromotionReadiness
* SuccessionPlan
* WorkforceHealthSnapshot

The code should read like the business language.

---

## Avoid Anemic Domain Models Where Possible

Domain entities should protect their own rules.

Example:

```csharp
public void Approve(Guid approvedByEmployeeId)
{
    if (Status != AchievementStatus.PendingReview)
    {
        throw new DomainException("Only pending achievements can be approved.");
    }

    Status = AchievementStatus.Approved;
    ApprovedByEmployeeId = approvedByEmployeeId;
    ApprovedDate = DateTime.UtcNow;
}
```

Do not allow random code to freely mutate important business state.

---

## Use Enums Carefully

Enums are useful for stable concepts.

Examples:

```csharp
public enum AchievementStatus
{
    Draft = 1,
    PendingReview = 2,
    Approved = 3,
    Rejected = 4,
    ClarificationRequested = 5
}
```

Avoid magic strings.

---

## Use Value Objects For Important Concepts

Examples:

* EmailAddress
* DateRange
* Score
* Money
* Percentage

Value objects help protect rules.

---

# SQL Server & Database Standards

## Database Design

Tables must be designed clearly.

Use:

* Primary keys
* Foreign keys
* Indexes
* Required fields
* Sensible constraints
* Created/Updated timestamps

Every important table should include:

```text
Id
CreatedAtUtc
CreatedBy
UpdatedAtUtc
UpdatedBy
IsDeleted
```

Soft delete is preferred for important business records.

---

## Naming Standards

Use clear table names.

Good:

```text
Employees
Achievements
EvidenceItems
AppraisalCycles
ManagerAssessments
SuccessionPlans
```

Avoid:

```text
TblEmp
DataStore
UserStuff
```

Column names must be readable.

---

## EF Core Standards

Use proper entity configurations.

Example:

```csharp
public sealed class EmployeeConfiguration
    : IEntityTypeConfiguration<Employee>
{
    public void Configure(EntityTypeBuilder<Employee> builder)
    {
        builder.ToTable("Employees");

        builder.HasKey(x => x.Id);

        builder.Property(x => x.FirstName)
            .HasMaxLength(100)
            .IsRequired();

        builder.Property(x => x.Email)
            .HasMaxLength(255)
            .IsRequired();
    }
}
```

Avoid putting all configuration inside `OnModelCreating`.

Use separate configuration files.

---

## Query Performance

Avoid loading unnecessary data.

Use projections for read models.

Good:

```csharp
var employees = await dbContext.Employees
    .AsNoTracking()
    .Select(x => new EmployeeListDto
    {
        Id = x.Id,
        FullName = x.FirstName + " " + x.LastName,
        Email = x.Email
    })
    .ToListAsync(cancellationToken);
```

Avoid:

```csharp
var employees = await dbContext.Employees.ToListAsync();
```

Then mapping everything in memory.

---

## Indexing

Create indexes for common searches.

Examples:

* Employee email
* DepartmentId
* ManagerId
* OrganisationId
* Status fields
* CreatedAtUtc
* AppraisalCycleId

Poor indexing will destroy dashboard performance later.

---

## Migrations

Every database change must have a migration.

Migration names must be meaningful.

Good:

```text
AddEmployeeAchievementTables
AddAppraisalCycleSchema
AddSuccessionPlanningTables
```

Bad:

```text
Update1
FixStuff
NewChanges
```

---

# Angular Standards

## Project Structure

Use feature-based structure.

Example:

```text
src/app/
  core/
  shared/
  features/
    employees/
    achievements/
    appraisals/
    growth/
    learning/
    promotions/
    succession/
    workforce-intelligence/
```

Do not put everything in one giant module or folder.

---

## Components

Components must be small and focused.

A component should have one responsibility.

Good:

```text
employee-profile-card
achievement-list
manager-review-panel
promotion-readiness-widget
```

Bad:

```text
dashboard-everything-component
```

---

## Services

Angular services should handle API communication and shared logic.

Do not put HTTP calls directly inside components.

Example:

```typescript
@Injectable({ providedIn: 'root' })
export class EmployeeService {
  constructor(private http: HttpClient) {}

  getEmployees(): Observable<EmployeeListItem[]> {
    return this.http.get<EmployeeListItem[]>('/api/employees');
  }
}
```

---

## State Management

Use Angular Signals where appropriate.

Use RxJS for async streams.

Do not over-engineer simple screens.

Use NgRx only if the state becomes complex enough to justify it.

---

## Forms

Use reactive forms for business forms.

Validation must exist on both frontend and backend.

Display validation messages clearly.

Do not hide errors.

---

## UI Standards

Use Tailwind CSS and DaisyUI consistently.

Screens should be:

* Clean
* Visual
* Dashboard-friendly
* Easy to scan
* Low text
* High clarity

This project should avoid long walls of text in the UI.

Use:

* Cards
* Tables
* Badges
* Tabs
* Timelines
* Progress bars
* Scorecards
* Charts

---

# AI Integration Standards

AI must assist.

AI must not decide.

This rule is non-negotiable.

AI can:

* Summarise evidence
* Suggest possible skills
* Suggest development actions
* Generate growth recommendations
* Produce executive insights

AI must not:

* Promote employees
* Reject employees
* Finalise scores
* Make employment decisions
* Replace manager judgement
* Override HR moderation

All AI-generated output must be marked as AI-assisted.

Human approval is required for important workflow decisions.

---

# Audit & Compliance Standards

Every sensitive action must be audited.

Examples:

* Achievement approved
* Achievement rejected
* Manager rating changed
* Appraisal submitted
* Promotion readiness recalculated
* Succession candidate added
* Employee data modified

Audit records should include:

* UserId
* Action
* EntityName
* EntityId
* OldValue
* NewValue
* TimestampUtc
* CorrelationId

Audit logs must not be editable from the application UI.

---

# Testing Standards

Minimum test types:

## Unit Tests

For:

* Domain rules
* Command handlers
* Calculation services
* Validation rules

## Integration Tests

For:

* API endpoints
* Database persistence
* Authorization rules

## Architecture Tests

For:

* Layer dependency rules
* Naming conventions
* Forbidden dependencies

Example:

Domain must not reference Infrastructure.

Application must not reference API.

---

# Pull Request Standards

Every pull request must answer:

* What changed?
* Why was it changed?
* How was it tested?
* What risks exist?
* Are there database changes?
* Are there security implications?

Code must not be merged if:

* Tests fail
* Build fails
* Validation missing
* Authorization missing
* Business rules are unclear
* Controllers contain business logic
* Angular components contain API logic
* Database changes lack migrations

---

# AI Coding Assistant Rules

Any AI assistant generating code for WorkforceIQ must follow these rules:

1. Read this document before generating code.

2. Follow Clean Architecture.

3. Do not generate shortcuts.

4. Do not place business logic in controllers.

5. Do not place business logic in Angular components.

6. Do not skip validation.

7. Do not skip authorization.

8. Do not skip audit logging.

9. Do not create fake placeholder implementations.

10. Do not create massive files.

11. Do not create unclear naming.

12. Do not invent business rules without documenting them.

13. Do not allow AI to make final employee decisions.

14. Generate tests for important logic.

15. Use meaningful comments only where helpful.

16. Prefer simple, readable code over clever code.

17. Every generated feature must be production-minded.

---

# Final Engineering Standard

The final standard is simple.

A senior engineer should be able to open the codebase and say:

> This is clean, understandable, secure, testable, and maintainable.

A business owner should be able to say:

> This software supports the real workflow.

A junior developer should be able to say:

> I can understand how this works and safely contribute.

A code reviewer should be able to say:

> This is ready to merge.

That is the standard for WorkforceIQ.
