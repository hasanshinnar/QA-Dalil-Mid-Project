# EduShop QA Testing Project — Midterm Assignment

![EduShop QA Status](https://img.shields.io/badge/Testing%20Scope-Manual%20%26%20API-blue?style=flat-square)
![Jira Integration](https://img.shields.io/badge/Jira%20%26%20Zephyr-Configured-0052CC?style=flat-square)
![Stack](https://img.shields.io/badge/Stack-ASP.NET%20Core%208%20|%20Angular%20|%20PostgreSQL-lightgrey?style=flat-square)

## Reference & Source Repository
This project builds upon the foundational EduShop test bed framework. For additional test scripts, API definitions, performance suites, and automation setups, refer to the source repository:
**[EduShop E-Commerce Test Project Repository](https://github.com/hasanshinnar/E-Commerce-test-project-for-API---JMeter---Automation)**

---

## Overview & Purpose
This repository documents the end-to-end Quality Assurance execution for **EduShop**, an e-commerce platform designed for university-level QA training. The platform features an **Angular** frontend, an **ASP.NET Core 8 Web API** backend, and a **PostgreSQL** database.

The primary objective of this project is to validate both functional business logic (via Manual UI testing) and server contract compliance (via REST API testing) against documented acceptance criteria.

---

## 📐 System Architecture & User Roles

### User Roles
* **Customer:** Browses catalog, manages shopping cart & wishlist, submits orders, writes reviews.
* **Admin:** Full customer access + product/category management, order status lifecycle management, and revenue dashboard oversight.

### Pre-seeded Accounts
| Role | Email | Password |
| :--- | :--- | :--- |
| **Admin** | `admin@test.com` | `Admin123!` |
| **Customer** | *(Self-registered during testing)* | *(Dynamic)* |

---

## Testing Scope

### 1. Manual Testing Scope
Coverage spans across **9 Epics** and **32 User Stories**, testing both happy paths and edge cases defined in the Product Backlog:

| Epic # | Epic Title | Stories | Scope Details |
| :---: | :--- | :---: | :--- |
| **1** | Authentication & Account Access | 5 | Register, Login, Refresh Token, Logout, Current User Info |
| **2** | Product Catalog & Discovery | 7 | Browse, Search, Filter, Sort, Pagination, Product Details |
| **3** | Category Management | 3 | Admin CRUD operations on Categories |
| **4** | Shopping Cart | 4 | Add/Update/Remove items, View Cart, Clear Cart |
| **5** | Checkout & Orders | 3 | Place Order, Order History, Admin Order Status Update |
| **6** | Product Reviews & Ratings | 2 | Submit Review, Delete Review |
| **7** | Wishlist | 3 | Add, Remove, View Wishlist items |
| **8** | Admin Dashboard & Reporting | 2 | Store Stats, Revenue Summary Reports |
| **9** | Cross-Cutting Platform Rules | 3 | RBAC Permissions, Data Validation, Error Handling |

### 2. API Testing Scope
Coverage spans **8 API Resources** and **32 Endpoints**, validating payload contracts, HTTP status codes, validation rules, and Role-Based Access Control (Unauthenticated / Customer / Admin):

| Resource | Base Path | Endpoints | Key Verification Areas |
| :--- | :--- | :---: | :--- |
| **Auth** | `/api/auth` | 5 | Token generation, refresh flow, auth guards |
| **Products** | `/api/product` | 5 | Query filters, pagination, schema validation |
| **Categories** | `/api/category` | 5 | Admin permission enforcement, payload checks |
| **Cart** | `/api/cart` | 5 | Item persistence, quantity boundaries |
| **Orders** | `/api/order` | 4 | Checkout validation, state transition logic |
| **Reviews** | `/api/review` | 3 | Author verification, rating range restrictions |
| **Wishlist** | `/api/wishlist` | 3 | User isolation, item duplication handling |
| **Admin** | `/api/admin` | 2 | Access controls, aggregate data integrity |

---

## Environment Setup & Prerequisites

### Docker Local Deployment
1. Clone the environment config and run Docker Compose:
   ```bash
   git clone https://github.com/hasanshinnar/E-Commerce-test-project-for-API---JMeter---Automation.git
   cd E-Commerce-test-project-for-API---JMeter---Automation
   docker-compose up -d
   ```
2. Verify local connectivity:
   * **Frontend Application:** `http://localhost:4200`
   * **Swagger API Docs:** `http://localhost:5000/swagger`
   * **Database (pgAdmin):** `http://localhost:5050`

---

## 🛠 Deliverables & Jira Workspace Structure

All test cases, execution runs, and defect reports are managed inside **Jira Scale / Zephyr Scale**.

### 1. Test Case Management (Zephyr)
* Every test case includes: `ID`, `Title`, `Preconditions`, `Steps`, `Test Data`, `Expected Result`, `Actual Result`, and `Status`.
* **Traceability:** Linked directly to corresponding User Stories or API Resources.
* **Tagging:** Labeled with `Manual` or `API`.

### 2. Defect Reporting (Jira Bugs)
Defects are filed with the following standard schema:
* **Custom Field - Severity:** `Critical` | `High` | `Medium` | `Low`
* **Custom Field - Issue Type:** `Database` | `API` | `Front-End`
* **Labels:** Tagged as `Manual` or `API`.
* **Traceability:** Mandatory link to the failing Test Case ID.

---

## Quality Criteria

* **Entry Criteria:** Local environment running successfully, backlog and API contracts reviewed, Jira board configured.
* **Exit Criteria:** $100\%$ scope coverage logged, all test cases executed with Pass/Fail status, failed test cases linked to open/verified Jira bugs, execution summary finalized.
