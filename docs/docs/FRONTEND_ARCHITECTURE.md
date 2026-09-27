# OMPYR Frontend Architecture

## 1. Purpose

The OMPYR Frontend is the user-facing interface of the OMPYR ecosystem.

It provides secure, responsive and scalable interfaces for:

- Founder
- OMPYR OP
- Departments
- Agents
- Employees
- Users
- Customers
- Future OMPYR products

The frontend must communicate with the backend through controlled APIs.

Core principle:

> The frontend displays and requests actions. The backend verifies and executes them.

The frontend must never be treated as the final security boundary.

---

# 2. Frontend Architecture

```text
                         OMPYR FRONTEND
                               │
                 ┌─────────────┴─────────────┐
                 │                           │
             Public UI                  Protected UI
                 │                           │
        ┌────────┼────────┐          ┌───────┼────────┐
        │        │        │          │       │        │
      Home     About    Products   Founder  User   Agent
                                      │
                                      ▼
                              Authentication
                                      │
                                      ▼
                               Authorization
                                      │
                                      ▼
                                  API Layer
                                      │
                                      ▼
                                OMPYR Backend
