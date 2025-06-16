# Software Requirements Specification (SRS)

## Skillio - learning Management System (LMS)

**Version:** 1.0\
**Date:** June 15, 2025\
**Organization:** 8200's Alumni Association

---

## Table of Contents

1. [Introduction](#1-introduction)
2. [System Overview](#2-system-overview)
3. [Functional Requirements](#3-functional-requirements)
4. [Non-Functional Requirements](#4-non-functionnal-requirements)
5. [Technical Architecture](#5-technical-architecture)
6. [Appendices](#6-appendices)

---

## 1. Introduction

### 1.1 Purpose

This Software Requirements Specification (SRS) document describes the requirements for the **Skillio** Online Learning Management System (LMS) designed for the 8200's Alumni Association. The LMS facilitates program-based learning, course management, and educational content delivery.

### 1.2 Scope

**Skillio** provides a tailored LMS platform for the 8200's Alumni Association, enabling:

- Manage multiple programs with distinct courses and their own content
- Facilitate program/course creation, enrollment, and management
- Facilitate instructor-student interactions within programs
- Track student progress and performance across programs and courses
- Deliver assessments and assignments with grading capabilities, within structured learning paths
- Support the organization's specific learning methodologies and workflows

### 1.3 Definitions, Acronyms, and Abbreviations

See [Appendix 6.1 - Glossary](#61-glossary) for definitions of terms used throughout this document.

### 1.4 References

- [IEEE Standard 830-1998](https://ieeexplore.ieee.org/document/720574) for Software Requirements Specifications
- [Web Content Accessibility Guidelines (WCAG) 2.1](https://www.w3.org/WAI/WCAG21/quickref/)

---

## 2. System Overview

### 2.1 System Context

Skillio serves as the central learning hub for the 8200's Alumni Association, integrating with existing organizational tools (Monday, Canva) while providing specialized educational functionality.

### 2.2 Hierarchical Learning Structure

```
Programs (e.g., "Aharaitech", "TechLift")
├── Courses (e.g., Web Development, AI & Data Science)
    ├── Modules (e.g., Introduction to Web Dev)
        ├── Lessons & Content
        └── Assessments
```

### 2.3 User Requirements

#### 2.3.1 User Roles & Responsibilities

| Role                              | Scope                            | Primary Responsibilities                                     |
| --------------------------------- | -------------------------------- | ------------------------------------------------------------ |
| **LMS Administrator**             | System-wide                      | Full system access                                           |
| **Program Coordinator**           | Program-wide                     | Manage program operations, enrollments, and student progress |
| **R&D Lead**                      | Program-wide                     | Oversee course content development                           |
| **Content Developer**             | Course-level                     | Create and manage course content                             |
| **District/Regional Coordinator** | Course-level (District/Regional) | Local program management, student support                    |
| **Instructor/Assistant**          | Course-level                     | Deliver instruction, grade assignments, support students     |
| **Student**                       | Content-level (Invdividual)      | Participate in courses, complete assignments, track progress |

### 2.4 Operating Environment

- **Deployment:** Cloud-hosted (AWS/Azure/GCP)
- **Client Access:** Web browsers (Chrome, Firefox, Safari, Edge)
- **Mobile:** Responsive web application with PWA capabilities
- **Database:** PostgreSQL with Redis caching
- **Security:** HTTPS, encrypted data storage, role-based access control (RBAC)
- **OS:** Linux-based server, cross-platform client access

---

## 3. Functional Requirements

### 3.1 User Management

- **UM-01:** System shall support hierarchical role-based access contorl (RBAC)
- **UM-02:** Administrators shall manage user accounts (create, modify, deactivate, bulk import)
- **UM-03:** System shall provide secure authentication with password reset functionality
- **UM-04:** Users shall update their profiles and maintain activity logs
- **UM-05:** System shall support CSV-based bulk enrollment for programs

### 3.2 Program & Course Management

- **PCM-01:** System shall suport hierarchical program structure: Programs → Courses → Modules
- **PCM-02:** Program Coordinators shall create and configure programs
- **PCM-03:** District/Regional Coordinators shall manage student enrollment and day-to-day operations within their assigned district/region
- **PCM-04:** System shall support program templates based on organization's standard formats
- **PCM-05:** System shall allow course sequencing and prerequisite management
- **PCM-06:** System shall support program lifecycle management (Active, Completed, Archived)
- **PCM-07:** Program Coordinators shall have access to program-wide performance metrics and mentoring tools

### 3.3 Content Management

- **CM-01:** System shall support multimedia content types (documents, videos, presentations, interactive materials)
- **CM-02:** Content Developers shall create and manage course content
- **CM-03:** System shall provide content versioning and scheduled release capabilities
- **CM-04:** System shall enable offline content access and caching for field access
- **CM-05:** System shall organize content within modules

### 3.4 Assessment & Progress Tracking

- **APT-01:** System shall support various assessment types (quizzes, assignments, practical evaluations)
- **APT-02:** System shall provide automated scoring for objective assessments (e.g., MCQs, true/false, fill-in-the-blank, etc.)
- **APT-03:** System shall track individual and cohort progress through learning paths
- **APT-04:** System shall generate completion certificates based on program requirements

### 3.5 Communication & Collaboration

- **CC-01:** System shall provide course-level discussion spaces for participants
- **CC-02:** System shall suport direct messaging between users (participants, facilitators, instructors, etc.)
- **CC-03:** System shall enable role-appropriate announcements (e.g., Program Coordinators to participants)
- **CC-04:** System shall support group activities and collaborative project tools
- **CC-05:** System shall integrate with existing organizational communication tools

### 3.6 Reporting & Analytics

- **RA-01:** System shall provide role-specific dashboards and reporting capabilities
- **RA-02:** Program Coordinators shall access program-wide analytics with performance indicators
- **RA-03:** District/Regional Coordinators shall generate progress reports for their assigned districts/regions
- **RA-04:** System shall track engagement metrics and provide improvement recommendations
- **RA-05:** System shall support data export for external reporting requirements
- **RA-06:** System shall provide automated report generation (e.g., for organizational meetings)

### 3.7 Notifications & Alerts

- **NA-01:** System shall provide real-time notifications for important events (e.g., new content, assignment deadlines, grades)
- **NA-02:** System shall support email and in-app notifications
- **NA-03:** System shall allow users to customize notification preferences
- **NA-04:** System shall provide alerts for upcoming deadlines and important announcements

---

## 4. Non-Functional Requirements

### 4.1 Performance Requirements

- **PR-01:** System shall suport at least {} concurrent users without performance degradation
- **PR-02:** System shall load the main dashboard within 3 seconds on a standard broadband connection
- **PR-03:** System shall support content caching for offline access with a maximum sync time of 5 minutes
- **PR-04:** System shall handle large file uploads (e.g., video content) with a maximum upload time of {} minutes

### 4.2 Reliability, Availability, Maintainability and Safety (RAMS) Requirements

- **RAMS-01:** System shall have an uptime of 99.9% excluding scheduled maintenance
- **RAMS-02:** System shall provide automated backups with a maximum data loss of 1 hour
- **RAMS-03:** System shall support disaster recovery with a maximum recovery time objective (RTO) of 2 hours
- **RAMS-04:** System shall provide a user-friendly interface for administrators to manage system health and performance
- **RAMS-05:** System shall log all critical errors and provide an error reporting mechanism for users
- **RAMS-06:** System shall provide a rollback mechanism for content updates to ensure data integrity
- **RAMS-07:** System shall support regular security audits and vulnerability assessments

### 4.3 Scalability Requirements

- **SR-01:** System shall support horizontal scaling to accommodate increasing user load
- **SR-02:** System shall allow for dynamic resource allocation based on user demand
- **SR-03:** System shall support database sharding and replication for improved performance
- **SR-04:** System shall allow for the addition of new programs and courses without downtime
- **SR-05:** System shall support load balancing to distribute traffic evenly across servers

### 4.4 Testability Requirements

- **TR-01:** System shall provide comprehensive unit tests for all core functionalities
- **TR-02:** System shall support automated end-to-end testing for critical user flows
- **TR-03:** System shall provide a test environment that mirrors production for accurate testing
- **TR-04:** System shall support performance testing to validate scalability and load handling
- **TR-05:** System shall provide logging and monitoring tools to facilitate debugging and issue resolution

---

## 5. Technical Architecture

### 5.1 Frontend Architecture

**Core Stack:**

- Framework: [Next.js](https://nextjs.org/) 15+ with [TypeScript](https://www.typescriptlang.org/)
- State Management: [Redux Toolkit](https://redux-toolkit.js.org/) or [Zustand](https://zustand-demo.pmnd.rs/)
- UI Components: [Shadcn UI](https://ui.shadcn.com/), [Next UI](https://nextui.org/), [Magic UI](https://magicui.design/)
- CSS: [Tailwind CSS](https://tailwindcss.com/)
- Build Tool: [Turborepo](https://turbo.build/repo)
- Package Manager: [pnpm](https://pnpm.io/)

**Additional Libraries:**

- Routing: [App Router](https://nextjs.org/docs/app) (Next.js built-in)
- Forms: [React Hook Form](https://react-hook-form.com/) with [Zod](https://zod.dev/)/[Yup](https://github.com/jquense/yup) validation
- API: [TanStack Query](https://tanstack.com/query/latest)/[SWR](https://swr.vercel.app/) with [Axios](https://axios-http.com/)
- Rich Text: [TinyMCE](https://www.tiny.cloud/), [Draft.js](https://draftjs.org/), [Tiptap](https://tiptap.dev/), or [Slate.js](https://www.slatejs.org/)
- File Upload: [React Dropzone](https://react-dropzone.js.org/)
- Charts: [Chart.js](https://www.chartjs.org/) or [D3.js](https://d3js.org/)
- Video: [Video.js](https://videojs.com/) or [React Player](https://github.com/cookpete/react-player)

### 5.2 Backend Architecture

**Core Stack:**

- Runtime: [Bun](https://bun.sh/) or [Node.js](https://nodejs.org/) v24+ LTS
- Framework: [NestJS](https://nestjs.com/)
- Language: [TypeScript](https://www.typescriptlang.org/)
- Database ORM: [Prisma](https://www.prisma.io/) or [TypeORM](https://typeorm.io/)
- Authentication: [BetterAuth](https://www.better-auth.com/) or [NextAuth.js](https://next-auth.js.org/)
- File Upload: [Multer](https://github.com/expressjs/multer) with cloud storage

**Database & Storage:**

- Primary: [PostgreSQL](https://www.postgresql.org/) 17+
- Secondary: [MongoDB](https://www.mongodb.com/) (optional for NoSQL needs)
- Caching: [Redis](https://redis.io/)
- File Storage: [AWS S3](https://aws.amazon.com/s3/) or [Azure Blob Storage](https://azure.microsoft.com/en-us/products/storage/blobs)

**Additional Libraries:**

- Validation: [Zod](https://zod.dev/) or [class-validator](https://github.com/typestack/class-validator)
- Email: [Nodemailer](https://nodemailer.com/) with SMTP or [SendGrid](https://sendgrid.com/)
- Task Queue: [BullMQ](https://bullmq.io/) with [Redis](https://redis.io/)
- Logging: [Pino](https://getpino.io/)
- API Docs: [Swagger](https://swagger.io/)/[OpenAPI](https://www.openapis.org/)

### 5.3 Deployment & Infrastructure

**Development:**

- Version Control: [Git](https://git-scm.com/) with [GitHub](https://github.com/)
- Code Quality: [ESLint](https://eslint.org/), [Prettier](https://prettier.io/), [Husky](https://typicode.github.io/husky/) + [lint-staged](https://github.com/okonet/lint-staged)
- Testing: [Jest](https://jestjs.io/) (unit), [Cypress](https://www.cypress.io/)/[Playwright](https://playwright.dev/) (e2e)
- API Testing: [Postman](https://www.postman.com/)
- Database: [Prisma Studio](https://www.prisma.io/studio) or [pgAdmin](https://www.pgadmin.org/)

**DevOps:**

- Containerization: [Docker](https://www.docker.com/) and [Docker Compose](https://docs.docker.com/compose/)
- Cloud: [AWS](https://aws.amazon.com/), [Azure](https://azure.microsoft.com/), or [Google Cloud Platform](https://cloud.google.com/)
- Monorepo: [Turborepo](https://turbo.build/repo) with [pnpm](https://pnpm.io/)
- Web Server: [Nginx](https://nginx.org/) or [Cloudflare](https://www.cloudflare.com/)
- CI/CD: [GitHub Actions](https://github.com/features/actions) or [Jenkins](https://www.jenkins.io/)
- Monitoring: [New Relic](https://newrelic.com/), [DataDog](https://www.datadoghq.com/), [Grafana](https://grafana.com/), or [Prometheus](https://prometheus.io/)
- Error Tracking: [Sentry](https://sentry.io/)

**Security:**

- HTTPS: SSL/TLS certificates
- Rate Limiting: [@nestjs/throttler](https://docs.nestjs.com/security/rate-limiting)
- CORS: [@nestjs/platform-express](https://docs.nestjs.com/techniques/security#cors)
- Security Headers: [helmet.js](https://helmetjs.github.io/)
- Input Sanitization: [Zod](https://zod.dev/), [DOMPurify](https://github.com/cure53/DOMPurify), [NestJS](https://nestjs.com/) pipelines

### 5.4 Mobile and Performance

**Mobile Strategy:**

- Progressive Web App (PWA) with responsive design
- Service Workers for offline content caching
- Web Push API for notifications
- Future: [React Native](https://reactnative.dev/) consideration

**Optimization:**

- Frontend: [Next.js](https://nextjs.org/) App Router with dynamic imports, [Next.js Image](https://nextjs.org/docs/api-reference/next/image) component, ISR, CDN
- Backend: Database indexing, connection pooling, Gzip compression, efficient pagination

### 5.5 Database Design

#### 5.5.1 Entity-Relationship Diagram (ERD)

![ERD Diagram](/primary-database-erd.jpg)

---

## 6. Appendices

### 6.1 Glossary

| Term              | Definition                                                                               |
| ----------------- | ---------------------------------------------------------------------------------------- |
| **Skillio**       | Fictitious name for the LMS platform developed for the 8200's Alumni Association.        |
| **Program**       | A structured learning initiative consisting of multiple courses                          |
| **Course**        | A collection of modules within a program convering specific topics or skills             |
| **Module**        | Self-contained learning unit focusing on specific knowledge/skills                       |
| **Learning Path** | A sequential progression through courses and modules within a program                    |
| **Assessment**    | A method to evaluate student knowledge/skills, including quizzes, exams, and assignments |

### 6.2 Organizational Structure Example

```
8200 Alumni Association
├── "Aharaitech" Program
│   ├── Web Development Course
│   │   ├── Module 1: Introduction to Web Development
│   │   └── Module 2: Frontend Development
│   ├── Game Development Course
│   │   ├── Module 1: Python Basics
│   │   └── Module 2: Game Design Principles
│   └── AI and Data Science Course
│       ├── Module 1: Data Analysis with Python
│       └── Module 2: ...
└── "TechLift" Program
    ├── Cybersecurity Course
    └── Operating Systems Course
```

### 6.3 User Role Matrix

**CRUD** refers to the `Create`, `Read`, `Update`, and `Delete` operations. The table below outlines the permissions using checkmarks (✅) for allowed actions and crosses (❌) for restricted actions.

In some cases, a checkmark logically implies that the action is permitted only within the user’s own content, courses, or programs (e.g., for Program Coordinators or Instructors), and applies only to the corresponding CRUD operations.

| Feature / Permissions               | LMS Administrator | Program Coordinator | R&D Lead | Content Developer | District/Regional Coordinator | Instructor/Assistant | Student |
| ----------------------------------- | ----------------- | ------------------- | -------- | ----------------- | ----------------------------- | -------------------- | ------- |
| LMS Configuration & User Management | ✅                | ❌                  | ❌       | ❌                | ❌                            | ❌                   | ❌      |
| Assign Roles & Permissions          | ✅                | ✅                  | ❌       | ❌                | ❌                            | ❌                   | ❌      |
| Manage Programs                     | ✅                | ✅                  | ✅       | ❌                | ❌                            | ❌                   | ❌      |
| Manage Courses                      | ✅                | ✅                  | ✅       | ✅                | ❌                            | ❌                   | ❌      |
| Grade assignments                   | ✅                | ✅                  | ❌       | ❌                | ❌                            | ✅                   | ❌      |
| View grades                         | ✅                | ✅                  | ❌       | ❌                | ✅                            | ✅                   | ✅      |
| Submit assignments                  | ❌                | ❌                  | ❌       | ❌                | ❌                            | ❌                   | ✅      |
| Participate in forums               | ✅                | ✅                  | ✅       | ✅                | ✅                            | ✅                   | ✅      |
| View course content                 | ✅                | ✅                  | ✅       | ✅                | ✅                            | ✅                   | ✅      |
| Take quizzes                        | ❌                | ❌                  | ❌       | ❌                | ❌                            | ❌                   | ✅      |
| View reports and logs               | ✅                | ❌                  | ❌       | ❌                | ❌                            | ❌                   | ❌      |
| Import/Export Data                  | ✅                | ✅                  | ✅       | ✅                | ✅                            | ✅                   | ❌      |

#### 6.4 Tree Diagram of User Roles

![Tree Diagram of User Roles](/role-hierarchy-tree-diagram.jpg)

---

**Document Control**

| Version | Date       | Author        | Description     |
| ------- | ---------- | ------------- | --------------- |
| 1.0     | 2025-06-15 | Liron Abutbul | Initial version |
