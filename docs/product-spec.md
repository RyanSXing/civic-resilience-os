# Civic Resilience OS
## Complete Product and Engineering Specification

> **Project type:** Independent research prototype and portfolio project  
> **Primary goal:** Demonstrate Forward Deployed Engineer-style problem solving through an operational decision-support system for emergency resource allocation  
> **Core scenario:** Allocate limited mobile generators and response teams to critical facilities during a prolonged regional power outage  
> **Status:** Specification  
> **Intended audience:** Builder, reviewer, recruiter, evaluator, or future contributor  

---

# 1. Executive Summary

Civic Resilience OS is a research prototype for managing emergency resource allocation during a major regional power outage.

The system combines:

- geospatial data;
- critical-facility information;
- public emergency-management doctrine;
- synthetic operational data;
- infrastructure dependency modeling;
- scenario simulation;
- constrained optimization;
- human approval workflows;
- policy enforcement;
- provenance tracking;
- audit logs;
- incident replay;
- AI-assisted report extraction;
- benchmark evaluation.

The software is designed around a single operational question:

> Given limited resources, uncertain information, changing conditions, and policy constraints, which facilities should receive generators and response teams, in what order, and why?

The system does not autonomously dispatch real resources. It is a portfolio-grade research prototype intended to demonstrate:

1. entering an unfamiliar operational domain;
2. translating doctrine into software;
3. integrating heterogeneous data;
4. building an ontology-like domain model;
5. producing actionable recommendations;
6. enforcing permissions and approval;
7. preserving provenance and uncertainty;
8. evaluating recommendations reproducibly;
9. handling changing conditions;
10. communicating technical and product tradeoffs clearly.

---

# 2. Product Thesis

Democratic societies often do not suffer from a lack of information. They suffer from an inability to transform fragmented, stale, conflicting, and incomplete information into timely, accountable action.

Civic Resilience OS explores how operational software can improve institutional response capacity by connecting:

- data;
- models;
- policy;
- people;
- actions;
- outcomes.

The product should never be framed as "an AI that manages emergencies."

It should be framed as:

> A human-in-the-loop operational decision system that helps users understand the current situation, compare feasible courses of action, approve missions, adapt to disruptions, and reconstruct why decisions were made.

---

# 3. Project Principles

## 3.1 Operational over analytical

The product must go beyond showing data. It must support a complete action loop:

```text
Event
→ Situation update
→ Impact analysis
→ Recommendation
→ Human review
→ Approval
→ Mission assignment
→ Execution update
→ Outcome
→ Audit and learning
```

## 3.2 Human authority

The system may recommend, summarize, classify, and optimize.

The system must not independently:

- dispatch a team;
- approve a mission;
- override a policy;
- conceal uncertainty;
- silently alter priorities;
- invent missing facts;
- rank lives without an explicit configurable policy.

## 3.3 Evidence before confidence

Every consequential recommendation should expose:

- source data;
- assumptions;
- confidence;
- freshness;
- constraints;
- tradeoffs;
- policy basis;
- unresolved conflicts.

## 3.4 Configurable policy

Priority rules should not be permanently hard-coded into an opaque scoring function.

Policies must be:

- named;
- versioned;
- editable;
- inspectable;
- testable;
- auditable.

## 3.5 Safe synthetic data

Real public data may be used for:

- roads;
- geography;
- public facilities;
- population summaries;
- historical weather;
- historical incident timing.

Synthetic data should be used for:

- precise infrastructure dependencies;
- generator inventories;
- team locations;
- fuel levels;
- facility vulnerabilities;
- staffing;
- response times;
- internal operational status.

## 3.6 Honest limitations

The project must state clearly:

- it was developed without practitioner access;
- it is not validated for real-world emergency operations;
- assumptions come from public doctrine and literature;
- sensitive operational values are synthetic;
- outputs are research demonstrations, not official guidance.

## 3.7 Reproducibility

Every scenario should be reproducible through:

- a fixed random seed;
- versioned scenario configuration;
- versioned policy configuration;
- versioned optimization parameters;
- immutable event logs.

---

# 4. Scope

## 4.1 Included in version 1

The first complete version should support:

- one fictional county or municipality;
- 20-30 facilities;
- five mobile generators;
- three response teams;
- one major power outage;
- road disruptions;
- weather deterioration;
- facility fuel depletion;
- inaccurate or conflicting field reports;
- recommendation generation;
- recommendation comparison;
- mission approval;
- simulated dispatch;
- replanning;
- incident replay;
- role-based access;
- append-only audit history;
- benchmark mode;
- AI-assisted report extraction.

## 4.2 Explicitly excluded from version 1

Do not build:

- real utility integrations;
- real emergency dispatch;
- classified-data handling;
- live personnel tracking;
- predictive policing;
- surveillance;
- weapons or targeting features;
- Kubernetes;
- a national-scale road graph;
- an autonomous multi-agent system;
- custom foundation models;
- mobile native applications;
- full disaster-management coverage;
- real-time voice command;
- direct SMS or radio integrations.

## 4.3 Primary scenario

A severe ice storm causes a regional power outage.

Initial conditions:

- two synthetic substations fail;
- 12 facilities lose grid power;
- five mobile generators are available;
- three response teams are available;
- some facilities have limited backup fuel;
- some roads are obstructed;
- weather is worsening;
- facility reports are incomplete;
- one report is incorrect;
- demand changes during the incident.

The user must determine:

- which facilities require immediate support;
- which generator is compatible with each facility;
- whether routes are open;
- whether a response team is available;
- whether the resource can arrive before backup fuel expires;
- which recommendation should be approved;
- how to replan after conditions change.

---

# 5. Users and Roles

The system uses synthetic personas derived from public emergency-management workflows.

## 5.1 Incident Commander

### Responsibilities

- understand overall incident status;
- compare courses of action;
- approve or reject missions;
- adjust strategic priorities;
- authorize exceptions;
- review major risks.

### Required capabilities

- read all operational data;
- view recommendations;
- inspect evidence;
- approve missions;
- reject missions;
- request revision;
- modify policy weights;
- record override rationale;
- review audit history.

## 5.2 Logistics Coordinator

### Responsibilities

- manage resources;
- monitor generator status;
- assign teams;
- create recommendations;
- resolve resource conflicts;
- track availability.

### Required capabilities

- view resource inventory;
- propose allocations;
- reserve resources;
- inspect routes;
- view compatibility;
- monitor mission status;
- request approval.

### Restrictions

- cannot approve their own high-risk mission;
- cannot edit audit history;
- cannot alter role permissions.

## 5.3 Situation Analyst

### Responsibilities

- review incoming reports;
- resolve entity matches;
- flag conflicting information;
- track stale data;
- assess cascading consequences.

### Required capabilities

- ingest field reports;
- confirm or reject extracted facts;
- merge duplicate incidents;
- mark reports as conflicting;
- change confidence ratings;
- inspect dependency graphs.

## 5.4 Field Responder

### Responsibilities

- receive mission assignments;
- acknowledge dispatch;
- report arrival;
- report obstruction;
- update mission status;
- submit field observations.

### Required capabilities

- read assigned missions;
- update own mission status;
- submit reports;
- flag inability to complete.

### Restrictions

- cannot view all system data;
- cannot approve missions;
- cannot edit policy.

## 5.5 Auditor

### Responsibilities

- reconstruct decisions;
- inspect model involvement;
- verify approval history;
- review policy compliance;
- examine overrides.

### Required capabilities

- read all historical data;
- inspect event logs;
- inspect policy versions;
- export audit reports.

### Restrictions

- read-only access.

## 5.6 System Administrator

### Responsibilities

- manage users;
- manage roles;
- load scenarios;
- configure integrations;
- maintain infrastructure.

### Restrictions

Administrative access does not imply operational approval authority.

---

# 6. Product Modes

## 6.1 Guided Demo Mode

A curated six-minute experience intended for recruiters and reviewers.

The demo should:

1. load a known scenario;
2. show a clear initial incident;
3. present affected facilities;
4. ingest a field report;
5. update urgency;
6. generate three plans;
7. compare tradeoffs;
8. approve one plan;
9. inject a disruption;
10. replan;
11. show the audit trail.

## 6.2 Sandbox Mode

Users may modify:

- number of generators;
- number of teams;
- facility priorities;
- fuel levels;
- road closures;
- policy weights;
- event timing;
- model confidence thresholds.

## 6.3 Benchmark Mode

A headless mode for running large numbers of scenarios.

Example:

```bash
python -m benchmark.run \
  --scenarios 500 \
  --strategies greedy,nearest,constraint_solver \
  --seed-start 1000 \
  --output results/benchmark.csv
```

## 6.4 Incident Replay Mode

The system replays a scenario at a selected speed.

Capabilities:

- play;
- pause;
- step forward;
- reset;
- jump to timestamp;
- inspect state at time;
- reveal only information available at that time;
- compare actual chosen actions with alternative recommendations.

---

# 7. Core Product Features

# 7.1 Authentication and Session Management

Required features:

- login;
- logout;
- session expiry;
- password hashing;
- seeded demo accounts;
- role-based authorization;
- protected routes;
- API authorization checks.

Optional:

- OAuth;
- multi-factor authentication;
- passkeys.

Acceptance criteria:

- users cannot access unauthorized screens;
- API endpoints reject unauthorized requests;
- role changes are logged;
- session expiration is enforced.

---

# 7.2 Operational Map

The map is the primary situational-awareness interface.

## Map layers

- county or municipal boundary;
- road network;
- road closures;
- facilities;
- generators;
- response teams;
- synthetic substations;
- service areas;
- weather alert polygon;
- mission routes;
- outage area;
- dependency links.

## Facility marker states

- normal;
- on backup power;
- urgent;
- critical;
- generator assigned;
- generator en route;
- unsupported;
- report conflict;
- stale data.

## Map interactions

- click facility;
- inspect current status;
- inspect fuel remaining;
- inspect population served;
- inspect dependencies;
- inspect reports;
- inspect recommendation impact;
- toggle layers;
- filter by facility type;
- filter by priority;
- filter by mission status;
- center map on active incident.

## Acceptance criteria

- map updates when scenario events occur;
- road closures change route feasibility;
- assigned mission routes display;
- stale or conflicting facilities are visually distinct;
- map data corresponds to current simulation time.

---

# 7.3 Facility Detail Panel

Each facility should display:

- name;
- type;
- location;
- population served;
- criticality;
- current power state;
- backup system status;
- estimated fuel remaining;
- estimated time to failure;
- generator compatibility;
- service dependencies;
- active reports;
- source provenance;
- confidence;
- freshness;
- assigned mission;
- recommendation rank;
- unresolved conflicts.

Actions:

- mark report reviewed;
- override facility status;
- request recommendation recalculation;
- open dependency graph;
- propose mission;
- add analyst note.

---

# 7.4 Resource Inventory

Resource types:

- mobile generator;
- response team;
- transport vehicle;
- fuel support unit;
- optional spare parts.

Generator fields:

- identifier;
- capacity;
- fuel level;
- fuel burn rate;
- connection type;
- voltage compatibility;
- current location;
- availability;
- assigned mission;
- estimated ready time;
- maintenance state.

Response team fields:

- identifier;
- skills;
- shift start;
- shift end;
- current location;
- travel readiness;
- vehicle;
- availability;
- active mission.

Features:

- filter by availability;
- filter by compatibility;
- reserve resource;
- release resource;
- inspect assignment history;
- flag resource failure;
- mark maintenance required.

---

# 7.5 Report Ingestion

Reports may be:

- manually entered;
- generated by scenario events;
- imported from JSON;
- submitted by field responders;
- parsed from free text.

Report fields:

- report ID;
- source;
- source role;
- source type;
- observed time;
- received time;
- content;
- geographic reference;
- candidate facility;
- confidence;
- status;
- extracted facts;
- evidence links;
- conflict state.

Report statuses:

```text
RECEIVED
PARSED
NEEDS_REVIEW
CONFIRMED
REJECTED
CONFLICTING
SUPERSEDED
```

Required functionality:

- preserve raw report;
- extract structured facts;
- allow analyst confirmation;
- retain rejected extraction values;
- link reports to entities;
- compare conflicting reports;
- never silently overwrite previous reports.

---

# 7.6 AI-Assisted Structured Extraction

The AI component converts free text into structured candidate facts.

Example input:

```text
Northbridge Care Centre reports approximately four hours of generator fuel remaining. Main entrance is inaccessible due to fallen trees. Staff requests replacement power before noon.
```

Expected candidate extraction:

```json
{
  "facility_name": "Northbridge Care Centre",
  "fuel_hours_remaining": 4,
  "access_issue": "main entrance inaccessible",
  "obstruction_type": "fallen trees",
  "requested_deadline": "12:00",
  "urgency": "high",
  "uncertainties": [
    "fuel estimate is approximate",
    "alternative entrance status unknown"
  ]
}
```

Requirements:

- use schema-constrained output;
- record prompt version;
- record model name;
- record latency;
- record token usage;
- record cost;
- record confidence;
- cite original report;
- require analyst confirmation before operational state changes;
- reject unsupported values;
- detect prompt-injection attempts;
- support deterministic fallback parsing.

The AI must never directly:

- dispatch;
- approve;
- modify policy;
- delete evidence;
- confirm its own extraction.

---

# 7.7 Data Freshness and Provenance

Every consequential property should include provenance metadata.

Required metadata:

```text
source_id
source_type
observed_at
received_at
valid_from
valid_until
confidence
ingestion_method
last_verified_at
verified_by
```

Source types:

```text
OFFICIAL_PUBLIC_DATA
OPEN_SOURCE
SCENARIO_SYNTHETIC
FIELD_REPORT
MODEL_INFERENCE
OPERATOR_OVERRIDE
DERIVED_CALCULATION
```

Freshness classifications:

```text
CURRENT
AGING
STALE
EXPIRED
UNKNOWN
```

Features:

- show source badge;
- show age;
- show confidence;
- show conflicting values;
- show derivation chain;
- show operator override history;
- block recommendations when critical fields are expired, if policy requires.

---

# 7.8 Dependency Graph

The graph models cascading failure.

Example:

```text
Substation A
→ Water Pumping Station 2
→ North District Water Pressure
→ Regional Hospital Sterilization Capacity
→ Patient Transfer Demand
```

Node types:

- infrastructure asset;
- facility;
- service;
- population area;
- resource;
- mission.

Edge types:

- depends on;
- supplies;
- serves;
- located in;
- requires;
- connected to;
- assigned to;
- affected by.

Features:

- visualize upstream dependencies;
- visualize downstream impacts;
- simulate asset failure;
- calculate affected facilities;
- calculate dependency depth;
- show confidence for each edge;
- distinguish real public geography from synthetic dependency assumptions.

---

# 7.9 Impact Analysis

When an event occurs, the system should calculate:

- directly affected facilities;
- indirectly affected facilities;
- affected populations;
- critical services at risk;
- resources potentially required;
- time-to-service-loss;
- route accessibility;
- existing mission conflicts.

Impact output should include:

- impact summary;
- affected object list;
- severity;
- uncertainty;
- evidence;
- recommended analyst review.

---

# 7.10 Recommendation Engine

The system generates multiple courses of action.

Strategies:

1. priority-first greedy;
2. nearest-resource;
3. weighted heuristic;
4. constrained optimizer;
5. operator-customized plan.

Each recommendation should include:

- plan ID;
- strategy;
- assignments;
- unserved facilities;
- objective score;
- expected benefit;
- travel time;
- missed deadlines;
- policy violations;
- assumptions;
- uncertainty;
- resource utilization;
- sensitivity;
- generation timestamp;
- solver version.

The interface should compare plans side by side.

---

# 7.11 Constraint Optimization

Use OR-Tools CP-SAT, mixed-integer programming, or another justified solver.

## Decision variables

Example:

```text
x[g,f] = 1 if generator g is assigned to facility f
y[t,m] = 1 if team t is assigned to mission m
```

## Constraints

- each generator has at most one active assignment;
- each facility receives at most one generator unless explicitly supported;
- generator capacity must meet facility minimum demand;
- electrical compatibility must be satisfied;
- team must be available;
- team skill requirements must be satisfied;
- route must be traversable;
- arrival must occur before facility deadline;
- resource cannot be assigned during maintenance;
- mission must fit within operational period;
- approval requirements must be satisfied before dispatch;
- conflicting assignments are prohibited.

## Objective components

Possible weighted objective:

```text
maximize:
  critical_service_preserved
+ vulnerable_population_supported
+ deadlines_met
+ coverage_equity
- travel_time
- reassignment_cost
- uncertainty_penalty
- policy_violation_penalty
```

Weights must be configurable and versioned.

## Infeasibility explanation

If no feasible plan exists, return:

- unsatisfied constraints;
- bottleneck resources;
- impossible deadlines;
- incompatible facilities;
- minimum additional resources needed;
- suggested policy relaxations;
- risks of each relaxation.

---

# 7.12 Recommendation Comparison

The user should be able to compare:

- facilities served;
- facilities unserved;
- population covered;
- total travel time;
- number of urgent deadlines met;
- critical services preserved;
- number of reassignments;
- uncertainty score;
- policy violations;
- resource utilization;
- worst-case outcome;
- sensitivity to assumptions.

The interface should never reduce the decision to one unexplained score.

---

# 7.13 Policy Engine

Policies should be represented explicitly.

Example policies:

- hospitals receive minimum criticality tier;
- long-term care facilities receive vulnerability multiplier;
- no resource may be dispatched without team assignment;
- high-risk missions require incident commander approval;
- facilities with unverified locations cannot receive automated route recommendations;
- stale fuel reports trigger uncertainty penalty;
- logistics coordinators cannot approve their own high-risk proposals.

Policy fields:

- policy ID;
- name;
- description;
- type;
- severity;
- condition;
- action;
- version;
- effective date;
- author;
- source;
- validation status.

Policy result statuses:

```text
PASS
WARN
FAIL
NOT_APPLICABLE
```

Features:

- run policy check;
- show violated policy;
- allow authorized override;
- require override reason;
- log policy version;
- rerun checks after plan changes.

---

# 7.14 Mission Workflow

Mission states:

```text
DRAFT
PROPOSED
UNDER_REVIEW
APPROVED
REJECTED
DISPATCHED
ACKNOWLEDGED
EN_ROUTE
ARRIVED
IN_PROGRESS
COMPLETED
FAILED
CANCELLED
```

Required transitions:

```text
DRAFT → PROPOSED
PROPOSED → UNDER_REVIEW
UNDER_REVIEW → APPROVED
UNDER_REVIEW → REJECTED
APPROVED → DISPATCHED
DISPATCHED → ACKNOWLEDGED
ACKNOWLEDGED → EN_ROUTE
EN_ROUTE → ARRIVED
ARRIVED → IN_PROGRESS
IN_PROGRESS → COMPLETED
Any active state → FAILED
Any pre-completion state → CANCELLED
```

Each transition must enforce:

- actor role;
- required fields;
- state validity;
- policy checks;
- resource availability;
- audit logging;
- event emission.

---

# 7.15 Human Approval

Approval screen must show:

- mission objective;
- assigned resources;
- affected facility;
- expected arrival;
- deadline;
- route;
- policy results;
- recommendation rationale;
- supporting evidence;
- uncertainty;
- alternatives;
- possible consequences;
- conflict-of-interest checks.

Approval actions:

- approve;
- reject;
- request revision;
- approve with override;
- delegate review.

Every decision requires:

- actor;
- timestamp;
- reason;
- policy version;
- recommendation version;
- evidence snapshot.

---

# 7.16 Replanning

Replanning triggers:

- road closure;
- generator failure;
- team unavailability;
- corrected fuel estimate;
- facility escalation;
- facility de-escalation;
- weather deterioration;
- delayed mission;
- shelter overcapacity;
- new critical incident.

The system should:

1. preserve the prior plan;
2. identify affected missions;
3. calculate current committed resources;
4. generate revised plans;
5. show differences;
6. quantify switching cost;
7. require approval for changed missions;
8. preserve full decision lineage.

---

# 7.17 Audit Log

The audit log must be append-only at the application layer.

Audit event fields:

```text
event_id
timestamp
actor_id
actor_role
action_type
object_type
object_id
previous_state
new_state
reason
evidence_ids
policy_results
model_involvement
request_id
correlation_id
scenario_time
real_time
```

Audit event examples:

- report received;
- AI extraction created;
- extraction confirmed;
- facility status changed;
- recommendation generated;
- policy failed;
- override approved;
- mission dispatched;
- mission updated;
- scenario event injected;
- resource failed;
- user role changed.

Features:

- filter by actor;
- filter by object;
- filter by event type;
- inspect state diff;
- export JSON or CSV;
- replay state from events;
- verify integrity checksum.

---

# 7.18 Incident Timeline

Timeline displays:

- scenario events;
- reports;
- decisions;
- mission transitions;
- policy overrides;
- resource failures;
- recommendation versions;
- weather updates.

Capabilities:

- jump to event;
- inspect historical state;
- compare state before and after event;
- filter by event type;
- identify major decision points.

---

# 7.19 Assumption Register

Every prototype-only assumption should be stored.

Fields:

- assumption ID;
- description;
- category;
- source;
- evidence strength;
- confidence;
- user configurability;
- sensitivity;
- affected components;
- validation status.

Categories:

```text
DOCTRINE_BACKED
RESEARCH_INFORMED
PROTOTYPE_ONLY
```

Example:

```text
Assumption:
Long-term care facilities receive a higher vulnerability multiplier than general shelters.

Category:
RESEARCH_INFORMED

Status:
Not validated for a specific jurisdiction

Configurable:
Yes

Sensitivity:
Changing multiplier from 1.3 to 1.0 alters 14% of baseline assignments
```

---

# 7.20 Sensitivity Analysis

The system should measure how recommendations change when:

- priority weights change;
- fuel estimates vary;
- travel times vary;
- road closures change;
- generator capacity changes;
- confidence thresholds change;
- facility population estimates change.

Output:

- changed assignments;
- rank instability;
- objective variation;
- affected facilities;
- policy impact;
- robustness score.

---

# 7.21 Data Health Dashboard

Metrics:

- stale critical fields;
- reports needing review;
- unresolved conflicts;
- missing facility coordinates;
- resources with unknown status;
- dependency edges with low confidence;
- model extraction failures;
- API ingestion failures;
- outdated policies.

Features:

- drill down;
- assign review;
- mark resolved;
- inspect trend over scenario time.

---

# 7.22 Observability

Track:

- API latency;
- API errors;
- optimization latency;
- optimization failures;
- database query latency;
- report ingestion throughput;
- AI request latency;
- AI cost;
- extraction failure rate;
- mission transition failures;
- policy evaluation failures.

Recommended tools:

- OpenTelemetry;
- Prometheus-compatible metrics;
- structured JSON logs;
- local Grafana optional;
- Sentry optional.

Every request should include:

- request ID;
- correlation ID;
- user ID;
- scenario ID;
- simulation timestamp.

---

# 8. Domain Model

# 8.1 Core Entities

## Incident

Fields:

- id;
- name;
- incident type;
- status;
- geographic area;
- start time;
- end time;
- severity;
- operational period;
- scenario ID.

## Facility

Fields:

- id;
- name;
- facility type;
- latitude;
- longitude;
- capacity;
- population served;
- criticality tier;
- minimum power demand;
- normal power state;
- backup power state;
- fuel hours remaining;
- deadline;
- access status;
- status confidence.

## InfrastructureAsset

Fields:

- id;
- asset type;
- synthetic flag;
- status;
- capacity;
- location;
- criticality;
- source;
- confidence.

## PopulationArea

Fields:

- id;
- geometry;
- population;
- vulnerability index;
- service dependencies.

## Resource

Fields:

- id;
- resource type;
- capacity;
- compatibility;
- location;
- availability;
- status;
- maintenance state.

## ResponseTeam

Fields:

- id;
- skills;
- current location;
- availability;
- shift;
- active mission;
- assigned vehicle.

## RoadSegment

Fields:

- id;
- geometry;
- travel time;
- status;
- closure reason;
- valid interval.

## Report

Fields:

- id;
- raw content;
- source;
- observed time;
- received time;
- status;
- confidence;
- linked entities.

## Recommendation

Fields:

- id;
- strategy;
- assignments;
- metrics;
- assumptions;
- solver metadata;
- generated time;
- scenario state version.

## Mission

Fields:

- id;
- objective;
- facility;
- resource;
- team;
- route;
- deadline;
- state;
- approval state.

## Decision

Fields:

- id;
- actor;
- decision type;
- target object;
- rationale;
- timestamp;
- evidence;
- policy results.

## Evidence

Fields:

- id;
- source type;
- source reference;
- excerpt;
- created time;
- confidence;
- linked claims.

## Policy

Fields:

- id;
- name;
- version;
- condition;
- consequence;
- source;
- effective time.

## Outcome

Fields:

- id;
- mission;
- completion status;
- completion time;
- service restored;
- delay;
- failure reason;
- measured effect.

## ScenarioEvent

Fields:

- id;
- scenario time;
- event type;
- payload;
- applied status;
- seed;
- source.

---

# 8.2 Relationships

```text
Incident AFFECTS Facility
Incident AFFECTS InfrastructureAsset
Facility SERVES PopulationArea
Facility DEPENDS_ON InfrastructureAsset
InfrastructureAsset SUPPLIES Facility
Mission TARGETS Facility
Mission REQUIRES Resource
Mission ASSIGNED_TO ResponseTeam
Recommendation PROPOSES Mission
Decision APPROVES Mission
Decision REJECTS Recommendation
Report REFERENCES Facility
Report PROVIDES Evidence
Evidence SUPPORTS Recommendation
Policy GOVERNS Decision
Outcome RESULTS_FROM Mission
RoadSegment ENABLES Route
ScenarioEvent CHANGES Object
```

---

# 9. State Management and Event Sourcing

The system should use a hybrid approach:

- relational tables for current state;
- append-only event log for history;
- immutable recommendation snapshots;
- scenario event stream for replay.

Recommended pattern:

```text
Command
→ Validation
→ Policy check
→ Database transaction
→ Current-state update
→ Audit event append
→ Domain event emit
```

Events should be replayable enough to reconstruct:

- mission history;
- resource assignments;
- facility status;
- recommendation lineage;
- approval decisions.

---

# 10. Database Design

Recommended database:

- PostgreSQL;
- PostGIS extension;
- Alembic migrations.

Suggested schemas:

```text
auth
domain
geo
operations
policy
audit
simulation
evaluation
ai
```

Core tables:

```text
users
roles
user_roles
incidents
facilities
infrastructure_assets
population_areas
resources
response_teams
road_segments
dependencies
reports
report_extractions
evidence
recommendations
recommendation_assignments
missions
mission_transitions
decisions
policies
policy_versions
policy_results
scenario_definitions
scenario_events
audit_events
assumptions
benchmark_runs
benchmark_results
model_calls
```

Indexes:

- geometry indexes using GiST;
- incident ID;
- scenario ID;
- mission status;
- event timestamp;
- facility type;
- resource availability;
- report review status;
- audit object reference.

---

# 11. API Specification

Base path:

```text
/api/v1
```

## Authentication

```text
POST /auth/login
POST /auth/logout
GET  /auth/me
```

## Incidents

```text
GET  /incidents
POST /incidents
GET  /incidents/{id}
PATCH /incidents/{id}
POST /incidents/{id}/activate
POST /incidents/{id}/close
```

## Facilities

```text
GET  /facilities
GET  /facilities/{id}
PATCH /facilities/{id}
GET  /facilities/{id}/dependencies
GET  /facilities/{id}/reports
GET  /facilities/{id}/history
```

## Resources

```text
GET  /resources
GET  /resources/{id}
PATCH /resources/{id}
POST /resources/{id}/reserve
POST /resources/{id}/release
POST /resources/{id}/fail
```

## Reports

```text
POST /reports
GET  /reports
GET  /reports/{id}
POST /reports/{id}/extract
POST /reports/{id}/confirm
POST /reports/{id}/reject
POST /reports/{id}/mark-conflict
```

## Recommendations

```text
POST /recommendations/generate
GET  /recommendations
GET  /recommendations/{id}
POST /recommendations/{id}/compare
POST /recommendations/{id}/propose-missions
```

## Missions

```text
POST /missions
GET  /missions
GET  /missions/{id}
POST /missions/{id}/submit
POST /missions/{id}/approve
POST /missions/{id}/reject
POST /missions/{id}/dispatch
POST /missions/{id}/acknowledge
POST /missions/{id}/start
POST /missions/{id}/complete
POST /missions/{id}/fail
POST /missions/{id}/cancel
```

## Policies

```text
GET  /policies
POST /policies
GET  /policies/{id}
POST /policies/evaluate
POST /policies/{id}/new-version
```

## Simulation

```text
POST /simulations/load
POST /simulations/start
POST /simulations/pause
POST /simulations/resume
POST /simulations/step
POST /simulations/reset
POST /simulations/inject
GET  /simulations/state
GET  /simulations/timeline
```

## Audit

```text
GET /audit/events
GET /audit/events/{id}
GET /audit/objects/{type}/{id}
GET /audit/export
```

## Evaluation

```text
POST /evaluation/benchmark
GET  /evaluation/runs
GET  /evaluation/runs/{id}
GET  /evaluation/runs/{id}/results
```

---

# 12. Frontend Information Architecture

Primary navigation:

```text
Overview
Map
Facilities
Resources
Reports
Plans
Missions
Timeline
Data Health
Assumptions
Benchmarks
Audit
Settings
```

## Overview

Show:

- incident status;
- active facilities at risk;
- active missions;
- available generators;
- unresolved conflicts;
- urgent deadlines;
- latest events;
- current policy version.

## Plans

Show:

- generated recommendations;
- strategy labels;
- plan metrics;
- assignment table;
- difference comparison;
- policy results;
- approval readiness.

## Timeline

Show:

- scenario events;
- decisions;
- mission changes;
- state snapshots.

## Benchmarks

Show:

- strategy comparison;
- success rate;
- average objective;
- deadline misses;
- policy violations;
- robustness results.

---

# 13. Scenario Engine

# 13.1 Scenario Definition

A scenario file should contain:

```yaml
scenario:
  id: northbridge-ice-storm-v1
  name: Northbridge Ice Storm
  seed: 42
  start_time: 2026-01-15T08:00:00
  duration_hours: 24

resources:
  generators: 5
  teams: 3

events:
  - at: "00:00"
    type: GRID_OUTAGE
  - at: "00:35"
    type: ROAD_CLOSURE
  - at: "01:20"
    type: FACILITY_REPORT
  - at: "02:15"
    type: GENERATOR_FAILURE
```

## 13.2 Event Types

```text
GRID_OUTAGE
ASSET_FAILURE
ROAD_CLOSURE
ROAD_REOPENED
FACILITY_REPORT
FACILITY_ESCALATION
FACILITY_DEESCALATION
RESOURCE_FAILURE
RESOURCE_RESTORED
TEAM_UNAVAILABLE
WEATHER_UPDATE
SHELTER_CAPACITY_EXCEEDED
REPORT_CORRECTION
MISSION_DELAY
MISSION_FAILURE
```

## 13.3 Simulation Controls

- play;
- pause;
- resume;
- step one event;
- jump to time;
- set speed;
- reset;
- branch scenario;
- inject manual event.

## 13.4 Determinism

A fixed scenario seed should determine:

- facility values;
- event order;
- resource failures;
- travel delays;
- report uncertainty.

---

# 14. Synthetic Data Generator

Command:

```bash
python scripts/generate_scenario.py \
  --seed 42 \
  --facilities 25 \
  --generators 5 \
  --teams 3 \
  --duration-hours 24 \
  --output data/scenarios/northbridge-v1
```

Generated data:

- facilities;
- capacities;
- backup fuel;
- deadlines;
- generator compatibility;
- teams;
- road disruption candidates;
- dependency graph;
- incident events;
- expected benchmark outcomes.

Generator requirements:

- reproducible;
- configurable;
- validation checks;
- no impossible baseline unless requested;
- optional stress scenarios;
- metadata describing synthetic status.

---

# 15. Evaluation Framework

# 15.1 Strategy Benchmarks

Compare:

- static facility priority;
- nearest compatible resource;
- greedy urgency;
- constrained optimization;
- operator-modified optimization.

Metrics:

- critical facilities served;
- vulnerable population supported;
- deadlines met;
- total travel time;
- average response time;
- policy violations;
- unserved demand;
- resource utilization;
- reassignment count;
- mission failures;
- worst-case service loss.

## 15.2 Robustness Tests

Inject:

- +/-20% travel time;
- +/-2 hours fuel estimate;
- random road closure;
- one generator failure;
- one team failure;
- incorrect report;
- delayed report;
- policy weight change.

Measure:

- assignment stability;
- objective degradation;
- missed deadlines;
- changed priority order;
- infeasible plan frequency.

## 15.3 AI Extraction Evaluation

Create at least 100 labeled reports.

Categories:

- normal;
- incomplete;
- contradictory;
- ambiguous facility;
- outdated;
- duplicate;
- incorrect measurement;
- prompt injection;
- irrelevant text;
- multiple facilities.

Metrics:

- entity identification accuracy;
- field extraction precision;
- field extraction recall;
- unsupported fact rate;
- uncertainty preservation;
- prompt-injection success rate;
- analyst correction rate;
- latency;
- cost.

## 15.4 Policy Evaluation

Test:

- unauthorized approval;
- self-approval conflict;
- stale critical data;
- incompatible generator assignment;
- blocked route;
- unavailable team;
- missing rationale;
- override without permission.

---

# 16. Testing Strategy

## Unit tests

Cover:

- scoring;
- policy evaluation;
- state transitions;
- compatibility;
- time calculations;
- freshness calculations;
- entity matching;
- graph propagation;
- objective functions.

## Integration tests

Cover:

- report ingestion to facility update;
- recommendation to mission creation;
- mission approval to dispatch;
- scenario event to replanning;
- policy override to audit entry.

## End-to-end tests

Use Playwright or Cypress.

Flows:

- login;
- load scenario;
- inspect facility;
- create recommendation;
- compare plans;
- approve mission;
- inject failure;
- replan;
- inspect timeline.

## Property-based tests

Useful for:

- no duplicate resource assignments;
- no impossible mission transitions;
- event replay consistency;
- benchmark reproducibility.

## Load tests

Basic targets:

- 100 concurrent read requests;
- 25 simultaneous scenario users;
- 1,000 scenario events;
- 500 benchmark runs.

---

# 17. Security Model

## 17.1 Authentication

- secure password hashing;
- HTTP-only cookies or secure tokens;
- session expiry;
- rate limiting;
- demo user separation.

## 17.2 Authorization

All authorization must be enforced server-side.

Permissions examples:

```text
incident.read
incident.manage
report.submit
report.review
recommendation.generate
mission.propose
mission.approve
mission.dispatch
policy.edit
audit.read
user.manage
```

## 17.3 Threat Model

Threats:

- stolen credentials;
- unauthorized mission approval;
- malicious report content;
- prompt injection;
- stale data;
- forged status update;
- audit tampering;
- data leakage;
- model hallucination;
- replay mismatch;
- denial of service.

Mitigations:

- RBAC;
- immutable audit;
- input validation;
- schema-constrained AI output;
- analyst confirmation;
- policy checks;
- request signing optional;
- structured logs;
- backups;
- rate limits;
- integrity hashes.

## 17.4 Data Markings

```text
PUBLIC
SYNTHETIC_OPERATIONAL
INTERNAL_DEMO
RESTRICTED_ROLE
```

---

# 18. Observability and Reliability

Reliability requirements:

- scenario state should survive process restart;
- failed optimization should not corrupt state;
- AI failure should not block manual report entry;
- external map or weather failure should degrade gracefully;
- audit events should persist in the same transaction as state changes;
- failed event injection should be retryable.

Health endpoints:

```text
GET /health/live
GET /health/ready
GET /health/dependencies
```

---

# 19. Technology Stack

## Backend

- Python 3.12;
- FastAPI;
- Pydantic;
- SQLAlchemy;
- Alembic;
- psycopg;
- Polars or Pandas;
- GeoPandas;
- Shapely;
- NetworkX;
- OR-Tools;
- HTTPX;
- Pytest.

## Frontend

- React;
- TypeScript;
- Vite or Next.js;
- TanStack Query;
- MapLibre GL;
- Zod;
- React Hook Form;
- lightweight component system;
- Playwright.

## Database

- PostgreSQL;
- PostGIS.

## Infrastructure

- Docker Compose;
- GitHub Actions;
- managed PostgreSQL;
- container hosting;
- Vercel or equivalent for frontend.

## Observability

- OpenTelemetry;
- structured JSON logging;
- Prometheus-compatible metrics;
- Sentry optional.

---

# 20. Repository Structure

```text
civic-resilience-os/
├── README.md
├── LICENSE
├── CONTRIBUTING.md
├── SECURITY.md
├── docker-compose.yml
├── Makefile
├── .env.example
├── docs/
│   ├── product-spec.md
│   ├── architecture.md
│   ├── domain-model.md
│   ├── domain-model-sources.md
│   ├── assumptions.md
│   ├── threat-model.md
│   ├── evaluation-plan.md
│   ├── demo-script.md
│   └── adr/
├── backend/
│   ├── app/
│   │   ├── api/
│   │   ├── auth/
│   │   ├── domain/
│   │   ├── geo/
│   │   ├── ingestion/
│   │   ├── reports/
│   │   ├── optimization/
│   │   ├── policies/
│   │   ├── missions/
│   │   ├── simulation/
│   │   ├── audit/
│   │   ├── evaluation/
│   │   ├── ai/
│   │   └── observability/
│   ├── migrations/
│   └── tests/
├── frontend/
│   ├── src/
│   │   ├── app/
│   │   ├── components/
│   │   ├── features/
│   │   ├── maps/
│   │   ├── api/
│   │   └── tests/
├── data/
│   ├── raw/
│   ├── processed/
│   ├── scenarios/
│   └── fixtures/
├── scripts/
│   ├── generate_scenario.py
│   ├── import_osm.py
│   ├── seed_demo.py
│   └── run_benchmarks.py
├── benchmark/
│   ├── strategies/
│   ├── scenarios/
│   └── reports/
└── infra/
    ├── docker/
    ├── terraform/
    └── github-actions/
```

---

# 21. Development Milestones

## Milestone 1: Domain and Research Foundation

Deliverables:

- project thesis;
- scope;
- public-source research library;
- evidence matrix;
- assumption register;
- ontology draft;
- scenario specification.

Exit criteria:

- every major object has a reason to exist;
- every key workflow is source-backed or clearly labeled as an assumption;
- fictional jurisdiction is defined.

## Milestone 2: Data Foundation

Deliverables:

- database schema;
- migrations;
- synthetic data generator;
- facility import;
- road import;
- resource inventory;
- provenance model.

Exit criteria:

- scenario loads successfully;
- facilities appear on map;
- every key value has source metadata.

## Milestone 3: Simulation

Deliverables:

- event stream;
- play/pause/step;
- deterministic replay;
- scenario state;
- timeline.

Exit criteria:

- same seed produces same event sequence;
- reset restores baseline;
- state at time can be reconstructed.

## Milestone 4: Optimization

Deliverables:

- baseline strategies;
- constrained solver;
- plan metrics;
- infeasibility explanation;
- plan comparison UI.

Exit criteria:

- solver never double-assigns resources;
- incompatible assignments are rejected;
- multiple plans can be compared.

## Milestone 5: Operational Workflow

Deliverables:

- mission lifecycle;
- approval;
- dispatch simulation;
- role checks;
- audit log.

Exit criteria:

- no mission can dispatch without approval;
- every transition creates an audit event;
- unauthorized actions fail.

## Milestone 6: Disruption and Replanning

Deliverables:

- road closure injection;
- resource failure;
- corrected report;
- plan diff;
- revised approval.

Exit criteria:

- active missions are re-evaluated;
- prior plan remains preserved;
- changed assignments are explainable.

## Milestone 7: AI and Data Quality

Deliverables:

- report extraction;
- analyst review;
- conflict handling;
- AI evaluation set;
- prompt injection tests.

Exit criteria:

- AI output cannot directly modify operational state;
- raw report is preserved;
- extraction quality is measured.

## Milestone 8: Benchmarking and Portfolio

Deliverables:

- 100+ scenarios;
- strategy comparison;
- charts;
- case study;
- architecture diagram;
- demo video;
- hosted deployment.

Exit criteria:

- benchmark results are reproducible;
- limitations are explicit;
- demo can be completed in six minutes.

---

# 22. Acceptance Criteria for Complete Project

The project is considered complete when a reviewer can:

1. launch the project locally with documented commands;
2. log in with seeded roles;
3. load a scenario;
4. view facilities and resources on a map;
5. play incident events;
6. inspect data provenance;
7. submit or receive a field report;
8. run AI-assisted extraction;
9. confirm or reject extracted facts;
10. generate at least three plans;
11. compare their tradeoffs;
12. inspect policy results;
13. approve a mission;
14. dispatch the mission;
15. inject a road closure or generator failure;
16. generate a revised plan;
17. inspect the complete audit history;
18. replay the incident;
19. run benchmark mode;
20. reproduce benchmark results.

---

# 23. Demo Script

## Scene 1: Initial situation

- severe ice storm;
- regional outage;
- 12 facilities affected;
- five generators available;
- three teams available.

## Scene 2: Data uncertainty

- long-term care facility has an approximate fuel estimate;
- report is parsed;
- analyst confirms extracted values;
- provenance and uncertainty remain visible.

## Scene 3: Plan generation

Generate:

- nearest-resource plan;
- priority-first plan;
- constrained optimized plan.

Compare:

- facilities served;
- deadlines met;
- travel time;
- policy warnings;
- unsupported facilities.

## Scene 4: Approval

- open optimized plan;
- inspect evidence;
- approve one mission;
- show audit event;
- dispatch team.

## Scene 5: Disruption

- inject road closure;
- current route becomes invalid;
- one generator becomes unavailable;
- system identifies affected missions.

## Scene 6: Replanning

- generate revised plan;
- compare old and new;
- approve revised mission;
- inspect decision lineage.

## Scene 7: Replay

- jump back to the decision point;
- show information available at that time;
- show why prior decision was reasonable;
- show later information that changed the plan.

---

# 24. Documentation Requirements

The repository should include:

## README

Must explain:

- project purpose;
- demo screenshots;
- architecture summary;
- setup;
- limitations;
- benchmark highlights.

## Product specification

This document.

## Architecture document

Must include:

- system context;
- service boundaries;
- data flow;
- event flow;
- deployment diagram.

## Domain source document

For each workflow and object:

- public source;
- relevant section;
- interpretation;
- prototype deviation.

## Assumption register

Must list all non-validated policies and values.

## Threat model

Must document threats and mitigations.

## Evaluation report

Must include:

- scenario count;
- strategies;
- metrics;
- results;
- failure cases;
- limitations.

## Architecture Decision Records

Suggested ADRs:

- why PostgreSQL instead of Neo4j;
- why modular monolith;
- why AI cannot directly dispatch;
- why synthetic infrastructure dependencies;
- why event log plus relational current state;
- why multiple plan strategies;
- why configurable policy weights.

---

# 25. Portfolio Narrative

The project narrative should be:

> I lacked access to emergency-management practitioners and proprietary operational data, so I treated those limitations as engineering constraints. I reconstructed a narrow workflow from public doctrine and after-action materials, separated public context from synthetic sensitive data, made assumptions explicit, built a reproducible simulator, implemented human approval and policy enforcement, and evaluated several allocation strategies across many scenarios.

The project should demonstrate:

- ambiguity reduction;
- systems thinking;
- data engineering;
- full-stack development;
- optimization;
- AI evaluation;
- security awareness;
- operational workflow design;
- product judgment;
- honest communication.

---

# 26. Known Limitations

The project must explicitly state:

- no practitioner validation;
- simplified command structure;
- simplified electrical compatibility;
- synthetic infrastructure dependencies;
- synthetic resource inventory;
- simplified travel-time model;
- no real dispatch integration;
- no real-time utility data;
- no production certification;
- no claim of operational readiness;
- no guarantee that objective weights reflect real policy.

---

# 27. Future Extensions

Possible future work:

- practitioner interviews;
- tabletop exercise with volunteers;
- offline-first field interface;
- weather forecast uncertainty;
- fuel resupply missions;
- multi-day operational periods;
- mutual-aid resource requests;
- real-time public alert ingestion;
- richer infrastructure dependency models;
- route uncertainty;
- fairness analysis;
- policy simulation;
- collaborative planning;
- incident briefing generation;
- after-action report generation;
- scenario authoring UI.

---

# 28. Build Order

Recommended implementation order:

1. repository and Docker setup;
2. database and migrations;
3. scenario generator;
4. facility and resource map;
5. scenario clock and events;
6. resource inventory;
7. basic greedy recommendation;
8. constrained optimizer;
9. plan comparison;
10. mission state machine;
11. approval and RBAC;
12. audit log;
13. road closure and replanning;
14. report ingestion;
15. AI extraction;
16. dependency graph;
17. data health;
18. sensitivity analysis;
19. benchmark mode;
20. polish and documentation.

---

# 29. First 30 Development Tickets

1. Initialize monorepo.
2. Create Docker Compose stack.
3. Configure PostgreSQL/PostGIS.
4. Create Alembic migrations.
5. Implement users and roles.
6. Seed demo users.
7. Create incident model.
8. Create facility model.
9. Create resource model.
10. Create response team model.
11. Create road segment model.
12. Create dependency model.
13. Build scenario YAML parser.
14. Build deterministic scenario generator.
15. Import road geometry.
16. Build map endpoint.
17. Build operational map UI.
18. Build facility detail panel.
19. Build resource inventory UI.
20. Implement scenario clock.
21. Implement event injection.
22. Implement audit event table.
23. Implement greedy assignment.
24. Implement nearest-resource assignment.
25. Implement OR-Tools optimization.
26. Build plan comparison API.
27. Build plan comparison UI.
28. Implement mission state machine.
29. Implement approval policy.
30. Implement dispatch simulation.

---

# 30. Final Success Standard

A strong final project does not need to prove that it can run a real emergency.

It must prove that the builder can:

- enter a difficult domain;
- structure fragmented information;
- distinguish facts from assumptions;
- model entities and relationships;
- produce feasible actions;
- preserve human authority;
- explain tradeoffs;
- evaluate system behavior;
- respond to changing conditions;
- ship a coherent end-to-end product.

That is the standard for Civic Resilience OS.
