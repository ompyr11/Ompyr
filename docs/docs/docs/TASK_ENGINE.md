# OMPYR — TASK ENGINE

## Purpose

The Task Engine converts Founder commands into structured, trackable and secure tasks.

Founder
→ OMPYR OP
→ Task Engine
→ Plan
→ Agents
→ Tools
→ Execution
→ QA
→ Security
→ Approval
→ Completion
→ Founder Report


## 1. Founder Command

The Founder may give commands using natural language.

Examples:

"OP, research the Indian healthcare market."

"OP, create a premium AI SaaS product."

"OP, create a new research agent."

"OP, improve yourself."

"OP, analyze this business problem."

OMPYR OP must understand the command before execution.


## 2. Command Understanding

Every command should be converted into:

- Objective
- Expected Result
- Priority
- Required Departments
- Required Agents
- Required Tools
- Required AI Models
- Required Permissions
- Approval Requirements
- Security Requirements


## 3. Task Creation

Each task should have:

- Task ID
- Command
- Objective
- Created By
- Created At
- Priority
- Department
- Assigned Agent
- Steps
- Tools
- AI Models
- Permissions
- Status
- Progress
- Approvals
- Errors
- Output
- Final Report


## 4. Task Status

DRAFT

→ PLANNED

→ RUNNING

→ WAITING_APPROVAL

→ RETRYING

→ COMPLETED


Possible terminal states:

FAILED

CANCELLED


## 5. Task Planning

OMPYR OP should:

1. Understand the goal
2. Break the goal into smaller tasks
3. Identify required departments
4. Identify required agents
5. Select suitable AI models
6. Select approved tools
7. Check permissions
8. Identify security risks
9. Create an execution plan


## 6. Agent Assignment

OMPYR OP assigns tasks according to:

- Agent role
- Skills
- Department
- Availability
- Permissions
- Security level
- Current workload


## 7. Parallel Execution

Independent tasks may run in parallel.

Example:

Research Agent
+
Market Analysis Agent
+
Technology Research Agent
+
Competitor Research Agent

Results are then combined by OMPYR OP.


## 8. Sequential Execution

Tasks with dependencies must run in order.

Example:

Research
→ Requirements
→ Architecture
→ Development
→ Testing
→ Security
→ Deployment


## 9. Tool Execution

Agents may use approved tools.

Before tool execution:

Task
→ Permission Check
→ Tool Check
→ Input Validation
→ Execute
→ Result Validation
→ Audit Log


## 10. AI Model Selection

OMPYR OP should select AI models according to the task.

Examples:

Research
→ Research-capable model

Coding
→ Coding-capable model

Image generation
→ Approved image model

Reasoning
→ Reasoning-capable model

The system may use multiple models for independent review when useful.


## 11. Multi-Model Verification

For important tasks:

Model A
+
Model B
+
Model C

↓

Compare Results

↓

Identify Agreement and Disagreement

↓

Verify Important Claims

↓

Final Result


AI outputs must not automatically be treated as facts.


## 12. Error Handling

OMPYR OP must not retry forever.

Failure flow:

ERROR
→ RETRY 1
→ RETRY 2
→ ALTERNATIVE METHOD
→ FOUNDER NOTIFICATION


## 13. Approval System

Founder approval may be required for:

- Spending money
- New powerful agents
- New powerful departments
- New external integrations
- Sensitive APIs
- Production deployment
- Public release
- Major architecture changes
- Critical security changes


## 14. Autonomous Actions

Routine low-risk actions may be performed automatically.

Examples:

- Research
- Planning
- Internal task creation
- Documentation
- Routine coding
- Testing
- Bug fixing
- Internal analysis


## 15. Progress Tracking

The Founder should be able to see:

- Current task
- Current agent
- Current department
- Current step
- Progress
- Tools being used
- Errors
- Approvals
- Security status


## 16. Task Events

Important events include:

- TASK_CREATED
- TASK_STARTED
- TASK_UPDATED
- TASK_COMPLETED
- TASK_FAILED
- TASK_CANCELLED
- APPROVAL_REQUESTED
- APPROVAL_GRANTED
- APPROVAL_REJECTED
- SECURITY_ALERT
- AGENT_CREATED
- AGENT_UPDATED
- BUG_DETECTED
- FIX_STARTED
- FIX_COMPLETED


## 17. Audit Log

Each important action should record:

- Timestamp
- Actor
- Task ID
- Action
- Tool
- Result
- Permission
- Approval
- Error if any


## 18. Task Completion

Before marking a major task complete:

Execution
→ Output Validation
→ QA
→ Security Check
→ Required Approval
→ Final Result


## 19. Founder Report

After completion OMPYR OP should report:

### Objective
What was requested.

### Work Completed
What was done.

### Agents Used
Which agents participated.

### AI Models Used
Which models were used.

### Tools Used
Which tools were used.

### Testing
What was tested.

### Security
Security status.

### Problems
Errors or limitations.

### Final Result
Final outcome.

### Founder Decision
Any remaining decision required from the Founder.


## 20. Example

Founder:

"OP, create a premium AI SaaS for a real-world problem."

OMPYR OP:

1. Understand command
2. Create task
3. Research problems
4. Analyze market
5. Identify customer pain
6. Research competitors
7. Research technology
8. Prepare solution options
9. Select architecture
10. Create required agents
11. Build MVP
12. Run tests
13. Run security checks
14. Fix issues
15. Prepare preview
16. Request Founder approval
17. Deploy
18. Monitor
19. Report results


## Core Principle

Every important OMPYR operation must be:

TRACEABLE

PERMISSION-CONTROLLED

TESTABLE

SECURE

REVERSIBLE WHERE PRACTICAL

AND UNDER FOUNDER AUTHORITY.
