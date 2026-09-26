# OMPYR Database Architecture

## 1. Purpose

The OMPYR Database Architecture defines how company, Founder, AI, agent, project, task, security, knowledge, and operational data is stored, connected, protected, and managed.

The database must prioritize:

- Security
- Data integrity
- Privacy
- Scalability
- Auditability
- Reliability
- Least privilege
- Backup and recovery
- Controlled access

---

# 2. Core Architecture

OMPYR should use a central structured database for operational data.

High-level architecture:

Founder
↓
Founder Control HQ
↓
OMPYR OP
↓
Application / API Layer
↓
Authorization Layer
↓
Database
↓
Audit / Security / Backup Systems

Agents should not directly access the database unless explicitly permitted through approved interfaces.

---

# 3. Data Categories

OMPYR data should be divided into categories.

## 3.1 Identity Data

Examples:

- Founder account
- User accounts
- Agent identities
- Department identities
- Service identities

---

## 3.2 Organization Data

Examples:

- Departments
- Roles
- Managers
- Agents
- Organization hierarchy

---

## 3.3 AI Data

Examples:

- AI models
- Model providers
- Model configurations
- Model capabilities
- Model usage
- Model evaluation results

---

## 3.4 Operational Data

Examples:

- Tasks
- Workflows
- Tool calls
- Projects
- Deployments
- Approvals

---

## 3.5 Knowledge Data

Examples:

- Documents
- Knowledge sources
- Research results
- Embeddings
- RAG metadata
- Project knowledge

---

## 3.6 Security Data

Examples:

- Login events
- Security alerts
- Permission changes
- Agent isolation
- Security incidents
- Audit logs

---

# 4. Main Entities

The initial database should support the following entities:

- founders
- users
- sessions
- devices
- departments
- agents
- agent_versions
- ai_models
- model_providers
- tools
- permissions
- roles
- projects
- tasks
- task_steps
- workflows
- approvals
- tool_calls
- knowledge_sources
- documents
- document_chunks
- embeddings
- research_runs
- research_sources
- deployments
- deployment_versions
- security_events
- audit_logs
- notifications
- system_settings

The exact schema may evolve as OMPYR grows.

---

# 5. Founder Entity

The Founder record should contain only required information.

Example fields:

- id
- name
- email
- authentication reference
- status
- created_at
- updated_at
- last_login_at

Passwords must never be stored in plaintext.

Authentication secrets should be handled by a secure authentication system.

---

# 6. User Entity

Users may represent future OMPYR customers or internal users.

Possible fields:

- id
- name
- email
- phone
- status
- role_id
- created_at
- updated_at

Sensitive information should only be stored when required.

---

# 7. Session Entity

Session records may contain:

- id
- user_id
- device_id
- created_at
- expires_at
- revoked_at
- last_activity_at
- security_status

Session tokens should be securely managed.

---

# 8. Device Entity

Possible fields:

- id
- user_id
- device_identifier
- device_type
- first_seen_at
- last_seen_at
- status
- security_status

Device identifiers must be handled carefully to avoid unnecessary tracking.

---

# 9. Department Entity

Possible fields:

- id
- name
- description
- manager_agent_id
- status
- created_at
- updated_at

Examples:

- Research
- Engineering
- AI
- QA
- Security
- Product
- Growth
- Finance
- Legal
- DevOps

---

# 10. Agent Entity

Possible fields:

- id
- name
- department_id
- manager_agent_id
- role
- mission
- status
- permission_profile_id
- current_version_id
- created_at
- updated_at

Agent status examples:

ACTIVE
PAUSED
ISOLATED
DISABLED
RETIRED

---

# 11. Agent Version Entity

Every important agent configuration or code change should be versioned.

Possible fields:

- id
- agent_id
- version
- instructions_reference
- configuration_reference
- tools_reference
- security_status
- test_status
- created_at
- approved_at
- approved_by

This allows rollback to a previous stable agent version.

---

# 12. AI Model Entity

Possible fields:

- id
- provider_id
- model_name
- model_version
- capabilities
- context_limit
- availability_status
- cost_metadata
- security_notes
- created_at
- updated_at

Model availability and pricing should be treated as changeable information.

---

# 13. Model Provider Entity

Examples:

- OpenAI
- Google
- Anthropic
- xAI
- Other providers

Possible fields:

- id
- name
- status
- integration_reference
- security_status
- created_at

Provider credentials must not be stored directly in ordinary database records.

---

# 14. Tool Entity

Examples:

- Web Search
- Browser
- Git
- Code Runner
- File System
- Database
- Deployment
- Email
- API Connector

Possible fields:

- id
- name
- description
- tool_type
- permission_level
- status
- security_status
- created_at

---

# 15. Permission Entity

Permissions define what an agent, user, or service may do.

Possible fields:

- id
- name
- description
- permission_level
- resource
- action
- risk_level

Examples:

READ
CREATE
EXECUTE
EXTERNAL_ACTION
SENSITIVE_ACTION
FOUNDER_ONLY

---

# 16. Role Entity

Roles group permissions.

Examples:

Founder
CEO
Department Manager
Research Agent
Developer Agent
QA Agent
Security Agent
Read-only Monitoring

A role should never automatically receive unrestricted access.

---

# 17. Project Entity

Possible fields:

- id
- name
- description
- owner
- status
- priority
- repository_reference
- environment
- created_at
- updated_at

Project status examples:

PLANNED
ACTIVE
PAUSED
COMPLETED
ARCHIVED
CANCELLED

---

# 18. Task Entity

Possible fields:

- id
- project_id
- created_by
- assigned_agent_id
- department_id
- goal
- priority
- status
- progress
- created_at
- started_at
- completed_at
- error_reference

Task statuses:

DRAFT
PLANNED
RUNNING
WAITING_APPROVAL
RETRYING
COMPLETED
FAILED
CANCELLED

---

# 19. Task Step Entity

Each task may contain multiple steps.

Possible fields:

- id
- task_id
- step_number
- description
- assigned_agent_id
- status
- input_reference
- output_reference
- started_at
- completed_at
- error_reference

---

# 20. Workflow Entity

Workflows define repeatable processes.

Examples:

- Research workflow
- Agent creation workflow
- Product creation workflow
- Deployment workflow
- Security incident workflow

Possible fields:

- id
- name
- version
- definition_reference
- status
- created_at
- updated_at

---

# 21. Approval Entity

Possible fields:

- id
- requested_by
- action_type
- resource_type
- resource_id
- reason
- risk_level
- estimated_cost
- status
- requested_at
- reviewed_at
- reviewed_by
- decision_notes

Approval states:

PENDING
APPROVED
REJECTED
EXPIRED
CANCELLED
EXECUTED
FAILED

---

# 22. Tool Call Entity

Tool execution should be traceable.

Possible fields:

- id
- task_id
- agent_id
- tool_id
- action
- input_reference
- output_reference
- status
- started_at
- completed_at
- error_reference

Sensitive tool inputs should not be unnecessarily stored in plaintext.

---

# 23. Knowledge Source Entity

Knowledge sources may include:

- Internal documents
- Research documents
- Public web sources
- APIs
- Project files
- Database records
- Approved external sources

Possible fields:

- id
- source_type
- title
- location_reference
- trust_level
- owner
- created_at
- updated_at

---

# 24. Document Entity

Possible fields:

- id
- knowledge_source_id
- project_id
- title
- document_type
- storage_reference
- version
- checksum
- created_at
- updated_at

The database should store metadata while large files may be stored in appropriate object/file storage.

---

# 25. Document Chunk Entity

Documents used for RAG may be divided into chunks.

Possible fields:

- id
- document_id
- chunk_index
- content_reference
- token_count
- metadata
- created_at

Chunking strategy may vary by document type.

---

# 26. Embedding Entity

Possible fields:

- id
- chunk_id
- embedding_model
- vector_reference
- created_at

Embedding storage should use a suitable vector-search solution.

---

# 27. Research Run Entity

Possible fields:

- id
- task_id
- research_question
- status
- started_at
- completed_at
- summary_reference
- verification_status

---

# 28. Research Source Entity

Possible fields:

- id
- research_run_id
- source_url_reference
- title
- source_type
- credibility_notes
- extracted_information_reference
- verification_status

Research claims should remain traceable to their sources.

---

# 29. Deployment Entity

Possible fields:

- id
- project_id
- version
- environment
- commit_reference
- status
- started_at
- completed_at
- approved_by
- rollback_status

---

# 30. Deployment Version Entity

Possible fields:

- id
- project_id
- version
- commit_hash
- build_reference
- test_status
- security_status
- release_notes
- created_at

Stable versions should be retained long enough to support rollback.

---

# 31. Security Event Entity

Possible fields:

- id
- event_type
- severity
- actor
- resource
- description
- detection_time
- status
- resolution_reference

Severity examples:

LOW
MEDIUM
HIGH
CRITICAL

---

# 32. Audit Log Entity

Audit logs should record important system actions.

Possible fields:

- id
- timestamp
- actor_type
- actor_id
- action
- resource_type
- resource_id
- result
- request_id
- metadata_reference

Audit logs should be protected from unauthorized modification.

---

# 33. Notification Entity

Possible fields:

- id
- recipient_id
- type
- title
- message_reference
- priority
- status
- created_at
- read_at

Examples:

- Approval request
- Security alert
- Deployment failure
- Agent failure
- System incident

---

# 34. System Settings

System settings should be separated by sensitivity.

Examples:

- General configuration
- Feature flags
- Security policies
- Rate limits
- Model routing settings
- Deployment policies

Critical security settings must have stronger access controls.

---

# 35. Relationships

High-level relationships:

Founder
↓
Users / Organization
↓
Departments
↓
Agents
↓
Tasks
↓
Projects
↓
Workflows
↓
Tool Calls
↓
Results

Knowledge:

Sources
↓
Documents
↓
Chunks
↓
Embeddings
↓
RAG Retrieval
↓
AI Model

Security:

Users / Agents / Tools / Deployments
↓
Security Events
↓
Audit Logs

---

# 36. Access Control

Database access must follow:

AUTHENTICATION
↓
IDENTITY
↓
ROLE
↓
PERMISSION
↓
RESOURCE
↓
ACTION

A user or agent must not access data merely because it exists in the database.

---

# 37. Row-Level Security

Where supported, sensitive multi-user data should use row-level security.

Examples:

User A
→ User A's permitted records

User B
→ User B's permitted records

Founder
→ Founder-authorized organization data

Agent
→ Only permitted operational data

---

# 38. Agent Data Isolation

Agents should have limited access to data.

Example:

Research Agent:
- Research data
- Assigned tasks
- Approved knowledge

Coding Agent:
- Assigned project
- Relevant code
- Build/test information

Finance Agent:
- Authorized financial data only

Security Agent:
- Authorized security events

No agent receives unrestricted access by default.

---

# 39. Founder Data Protection

Founder-sensitive data must be isolated.

Examples:

- Founder authentication
- MFA configuration
- Private credentials
- Financial secrets
- Security recovery information

OMPYR OP must not have unrestricted access to Founder secrets.

---

# 40. Data Encryption

Sensitive data should be protected:

- In transit using secure transport
- At rest using appropriate encryption
- Through secure key management

Encryption keys must not be stored alongside protected data without appropriate controls.

---

# 41. Data Minimization

OMPYR should collect and store only data required for a legitimate purpose.

Avoid unnecessary:

- Personal data
- Device data
- Location data
- User activity
- Sensitive information

Data should have a defined purpose.

---

# 42. Data Retention

Different data types may require different retention periods.

Examples:

- Temporary task data
- Audit logs
- Security events
- User data
- Research data
- Project data
- Deployment records

Retention policies should be configurable.

---

# 43. Data Deletion

Deletion must respect:

- Authorization
- Business requirements
- Legal requirements
- Dependencies
- Audit requirements
- Backup policy

Critical destructive operations require stronger approval.

---

# 44. Soft Delete

Where appropriate, records may use soft deletion.

Example:

status = DELETED

This can allow:

- Recovery
- Audit
- Investigation

Permanent deletion should require additional controls when appropriate.

---

# 45. Database Backup

Important database data should be backed up according to risk.

Backup system should define:

- Frequency
- Retention
- Encryption
- Storage
- Recovery procedure
- Recovery testing

---

# 46. Database Recovery

Recovery process:

DETECT FAILURE
↓
ASSESS
↓
SELECT RECOVERY POINT
↓
RESTORE
↓
VERIFY
↓
RECONNECT SERVICES
↓
MONITOR

---

# 47. Database Migration

Schema changes must be version controlled.

Migration process:

DEVELOP
↓
TEST
↓
STAGING
↓
BACKUP IF REQUIRED
↓
APPROVAL IF REQUIRED
↓
PRODUCTION
↓
VERIFY

Destructive migrations require special review.

---

# 48. Database Performance

The database should use:

- Proper indexes
- Pagination
- Query optimization
- Connection pooling
- Caching where appropriate
- Background jobs for heavy operations

Optimization should be based on actual usage and measurements.

---

# 49. Scalability

OMPYR should begin simple and scale when required.

Initial architecture may use a managed relational database.

As OMPYR grows, additional systems may be introduced:

- Cache
- Queue
- Search engine
- Vector database
- Object storage
- Analytics database

Do not introduce unnecessary infrastructure before it is needed.

---

# 50. Database Monitoring

Monitor:

- Database availability
- Query latency
- Error rate
- Connection usage
- Storage
- CPU
- Memory
- Failed queries
- Replication where applicable
- Backup status

---

# 51. Database Security

Database security must include:

- Strong authentication
- Least privilege
- Network protection
- Encryption
- Secure credentials
- Access logging
- Backup protection
- Injection prevention
- Input validation
- Monitoring

Application queries should use safe parameterized methods.

---

# 52. SQL Injection Protection

User input must never be blindly concatenated into SQL queries.

Use:

- Parameterized queries
- Prepared statements
- ORM/query builders where appropriate
- Input validation

Security testing should include injection testing.

---

# 53. Database Transactions

Critical multi-step operations should use transactions where appropriate.

Example:

Create payment record
+
Update order status
+
Create audit event

These operations should remain consistent.

---

# 54. Idempotency

Important operations should support idempotency where appropriate.

This prevents duplicate execution caused by retries.

Examples:

- Payments
- Deployment actions
- External API operations
- Task creation
- Notifications

---

# 55. Data Integrity

The database should enforce appropriate:

- Primary keys
- Foreign keys
- Unique constraints
- Required fields
- Validation rules
- Status rules

Application-level validation should complement database constraints.

---

# 56. Database Environment Separation

Development, test, staging, and production databases should be separated.

Production data should not be copied into development without appropriate authorization and protection.

---

# 57. Database Access by AI Agents

AI agents should not receive unrestricted database credentials.

Preferred architecture:

Agent
↓
Approved API / Tool
↓
Authorization
↓
Validated Operation
↓
Database

Direct database access should be exceptional and tightly controlled.

---

# 58. AI Memory vs Database

Database is not the same as AI memory.

Database:

- Structured operational records
- Users
- Tasks
- Agents
- Projects
- Permissions
- Logs

AI memory/RAG:

- Relevant knowledge
- Documents
- Context
- Research information
- Historical information where appropriate

The two systems may work together.

---

# 59. RAG Data Flow

Example:

Document
↓
Parse
↓
Chunk
↓
Metadata
↓
Embedding
↓
Vector Store
↓
Semantic Retrieval
↓
Relevant Context
↓
AI Model
↓
Response

Retrieved information should remain traceable to its source.

---

# 60. Database + Event System

Important system events may be recorded through an event mechanism.

Examples:

AGENT_CREATED
TASK_CREATED
TASK_STARTED
TASK_COMPLETED
APPROVAL_REQUESTED
APPROVAL_GRANTED
DEPLOYMENT_STARTED
DEPLOYMENT_COMPLETED
SECURITY_ALERT
AGENT_ISOLATED

Events can support:

- Notifications
- Audit
- Automation
- Analytics
- Monitoring

---

# 61. Unique IDs

Entities should use unique identifiers.

Example:

user_id
agent_id
task_id
project_id
approval_id
deployment_id

IDs should not expose unnecessary personal information.

---

# 62. Timestamps

Important records should include timestamps.

Recommended fields:

created_at
updated_at
started_at
completed_at

Use a consistent time standard internally.

---

# 63. Database Naming

Database names should be:

- Consistent
- Clear
- Predictable
- Documented

Avoid ambiguous names.

---

# 64. Schema Versioning

Database schema changes should be tracked.

Each migration should have:

- Migration ID
- Description
- Author/actor
- Created time
- Applied time
- Rollback strategy where possible

---

# 65. Founder Visibility

Founder Control HQ should provide visibility into:

- Database health
- Storage
- Recent migrations
- Backup status
- Security events
- Active connections where appropriate
- Critical errors

Founder visibility does not mean exposing raw secrets.

---

# 66. Free-First Strategy

Initial database infrastructure should prefer:

FREE
↓
FREE TIER
↓
OPEN SOURCE
↓
LOW COST
↓
PAID

The architecture should avoid unnecessary paid infrastructure during the MVP stage.

---

# 67. Future Scaling

As OMPYR grows, the database architecture may evolve.

Possible future components:

- Read replicas
- Database clustering
- Distributed cache
- Message queues
- Vector databases
- Search systems
- Data warehouse
- Analytics systems

Any major architecture change should be tested before production use.

---

# 68. Self-Improvement

OMPYR OP may propose database improvements.

Process:

AUDIT
↓
IDENTIFY BOTTLENECK
↓
RESEARCH
↓
DESIGN
↓
TEST
↓
SECURITY REVIEW
↓
FOUNDER APPROVAL IF REQUIRED
↓
MIGRATION
↓
VERIFY
↓
MONITOR

The live database must never be modified recklessly.

---

# 69. Core Database Principle

OMPYR database architecture follows:

SECURE
+
MINIMAL
+
STRUCTURED
+
AUDITABLE
+
SCALABLE
+
RECOVERABLE

The database is a controlled system of record for OMPYR.

---

# 70. Final Rule

No AI agent, tool, application, or external service should receive more database access than necessary.

OMPYR follows:

AUTHENTICATE
↓
AUTHORIZE
↓
VALIDATE
↓
EXECUTE
↓
LOG
↓
MONITOR

Database access must always remain controlled by OMPYR's security and Founder governance systems.
