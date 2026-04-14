# Workshop: SDA Developer Productivity

## Overview

| **Goal** | Demonstrate how Devin accelerates bug fixing, feature development, testing, and security |
|---|---|
| **Duration** | 3-4 hours (spread out over 3 days) |
| **Audience** | Saudi Digital Authority (SDA) engineers |
| **Application** | [app_timesheet](https://github.com/Cognition-Partner-Workshops/app_timesheet) — React 19 + Node.js/Express + SQLite (full-stack timesheet & billing app) |

## Workshop Narrative

Every engineering team deals with the same daily challenges: bugs in production, feature backlogs, insufficient test coverage, and security findings that pile up. 

This workshop uses a real full-stack application (timesheet and billing tracker) to show how Devin handles these tasks end-to-end — from reading code and understanding context, through implementation and testing, to opening a pull request for review.

---

## Get started
Sign in to Cognition through the invite you received in your email.

## Repos Required

[app_timesheet](https://github.com/Cognition-Partner-Workshops/app_timesheet) (already added to your Devin org)

## Lab 1 — Fix Known Bugs (45 min)

- **Objective:** Fix two known bugs — a visual CSS issue and a data persistence problem — demonstrating Devin's ability to investigate, diagnose, and fix issues across the frontend and backend

### Bug A: UI Strikethrough Bug (20 min)

#### Step 1: Paste into Devin

> There's a UI bug in app_timesheet: on the /work-entries page, the Client dropdown label has a strikethrough. Investigate the CSS/styling causing this issue and fix it. Take a screenshot before and after the fix. Open a PR.

#### Step 2: Research with Ask Devin

- *"What CSS or Material-UI styling is applied to the Client dropdown on the /work-entries page?"*
- *"Are there any global styles that might be causing the strikethrough?"*

### Bug B: Data Persistence Bug (25 min)

#### Step 1: Paste into Devin

> There's a data bug in app_timesheet: clients created by one user are not visible to other users after logging out and back in with a different email. Clients should be shared across all users. Investigate the database schema and queries, find the root cause, and fix it. Make sure work entries still belong to individual users. Open a PR.

#### Step 2: Research with Ask Devin

- *"How does the app_timesheet database schema handle multi-tenancy? Are clients scoped per-user or org-wide?"*
- *"What queries does the backend use to fetch clients? Are they filtered by user ID?"*

#### Step 3: Read the DeepWiki

Open the [app_timesheet DeepWiki](https://deepwiki.com/Cognition-Partner-Workshops/app_timesheet) page. Explore the database schema and data flow sections. Ask questions right there.

#### Step 4 (Optional): Review & Give Feedback

- Review the PR diff — does the fix handle edge cases (e.g., deleting a shared client that has work entries)?
- Ask Devin to add a test that verifies clients are visible across users

**Target Outcomes:** Two merged PRs with before/after evidence, understanding of how Devin traces bugs through frontend and backend layers

---

## Lab 2 — New Feature Development (60 min)

- **Objective:** Build a complete new feature (backend API + frontend UI + database changes + tests) in a single Devin session

### Step 1: Paste into Devin

> Add a "Projects" management feature to app_timesheet. Users should be able to create, view, edit, and delete projects. Each project has a name, description, client assignment, start date, and status (active/completed/on-hold). Add both the backend API endpoints and the frontend UI page. Follow the existing patterns in the codebase for the data model, API structure, and React components. Write tests for the backend endpoints. Open a PR.

### Step 2: Research with Ask Devin

- *"What patterns do the existing features follow? What conventions should a new feature match?"*
- *"What database migration approach does the app use?"*
- *"How are React components structured in the frontend — what state management pattern is used?"*

### Step 3 (Optional): Read the DeepWiki

Open the [app_timesheet DeepWiki](https://deepwiki.com/Cognition-Partner-Workshops/app_timesheet) page. Try adding validation rules, audit logging, or API documentation to the new feature.

### Step 4 (Optional): Review & Give Feedback

- Review for code style consistency with existing patterns
- Ask Devin to add input validation, error handling, or additional test cases
- Try: *"Add a filter on the Projects page to filter by status and client"*

**Target Outcomes:** Full-stack feature (DB schema + API routes + React UI + tests) delivered via PR, following existing codebase conventions

---

## Lab 3 — Unit Testing & Coverage (45 min)

- **Objective:** Analyze test coverage gaps and generate meaningful unit tests for the backend API

### Step 1: Paste into Devin

> Analyze the current test coverage of app_timesheet. Add missing Jest unit tests for the backend API routes and service layer. Generate a coverage report and fix any failing tests. Open a PR with the changes.

### Step 2: Research with Ask Devin

- *"What's the current test coverage in app_timesheet? Which modules are most at risk?"*
- *"What testing patterns does the codebase use? Jest, Supertest, mocking?"*
- *"Which API endpoints have no test coverage at all?"*

### Step 3 (Optional): Read the DeepWiki

Open the [app_timesheet DeepWiki](https://deepwiki.com/Cognition-Partner-Workshops/app_timesheet) page. Try generating edge case tests, integration tests, or adding test data factories.

### Step 4 (Optional): Review & Give Feedback

- Review tests for meaningful assertions (not just coverage padding)
- Ask Devin to add edge case tests: *"Add tests for invalid input, empty results, and concurrent access"*
- Ask Devin to add integration tests using Supertest for the full HTTP request/response cycle

**Target Outcomes:** Improved test coverage with meaningful assertions, coverage report, understanding of Devin's test generation quality

---

## Lab 4 — Security Audit & Remediation (45 min)

- **Objective:** Run a security code review against the OWASP Top 10 and have Devin fix the most critical findings

### Step 1: Paste into Devin

> Perform a security code review of app_timesheet against the OWASP Top 10. Focus on: authentication weaknesses (email-only, no password), SQL injection risks in the SQLite queries, XSS vulnerabilities in the React frontend, and CSRF protection. For each finding, explain the vulnerability, its severity, and provide a recommended fix. Implement fixes for the top 3 most critical findings. Open a PR.

### Step 2: Research with Ask Devin

- *"What authentication mechanism does app_timesheet use? What are its weaknesses?"*
- *"Are the SQLite queries parameterized or vulnerable to injection?"*
- *"Does the Express backend use helmet, CORS, or rate limiting?"*

### Step 3 (Optional): Read the DeepWiki

Open the [app_timesheet DeepWiki](https://deepwiki.com/Cognition-Partner-Workshops/app_timesheet) page. Explore the authentication flow and API security sections.

### Step 4 (Optional): Review & Give Feedback

- Review security fixes for completeness — did Devin address the root cause or just a symptom?
- Ask Devin to add: *"Run npm audit and fix any critical dependency vulnerabilities too"*
- Try: *"Add rate limiting to the login endpoint and document the security improvements in a SECURITY.md"*

**Target Outcomes:** Security audit report with OWASP Top 10 findings, fixes for critical vulnerabilities, PR with before/after evidence

---

## Key Takeaways

- **"Devin understands your codebase"** — it reads existing patterns (API structure, component conventions, database schema) before making changes
- **"Bug fix to feature to security in one session"** — participants see the full spectrum of daily development tasks accelerated
- **"Review, don't rewrite"** — the developer's role shifts from writing code to reviewing Devin's PRs and providing feedback
- **"One prompt, full-stack result"** — a single natural language prompt produces database changes, API routes, React UI, and tests
