# DOMAIN_MODEL.md

# PMOS AI Domain Model

## Purpose

This document defines the conceptual model used by PMOS AI to represent, understand and reason about projects.

It is intentionally independent of any database technology or implementation details.

This model represents the business language of PMOS AI.

---

# Fundamental Principle

PMOS AI does not manage documents.

PMOS AI manages **knowledge**.

Knowledge is represented through entities and relationships that evolve during the lifecycle of a project.

---

# Everything is an Event

Every relevant action inside a project generates an Event.

Examples:

* Meeting held
* Requirement created
* Decision approved
* Agreement reached
* Task assigned
* Risk detected
* Budget updated
* Document uploaded

Events are immutable historical facts.

The current state of the project is the accumulation of those events.

---

# Core Entities

## Tenant

Represents an organization using PMOS AI.

Examples:

* Company
* Government agency
* University
* Consulting firm

A Tenant owns one or more Projects.

---

## Project

Represents a temporary effort executed to achieve specific objectives.

A Project contains:

* Objectives
* Scope
* Stakeholders
* Teams
* Requirements
* Tasks
* Decisions
* Risks
* Artifacts
* Events

Project is the primary aggregation entity.

---

## Person

Represents an individual participating in the project.

Examples:

* Sponsor
* Project Manager
* Developer
* Customer
* Architect
* Vendor

A Person may participate in multiple Projects.

---

## Organization

Represents a legal or functional entity.

Examples:

* Customer
* Supplier
* Internal department

A Person belongs to an Organization.

---

## Role

Represents a responsibility within a Project.

Examples:

* Sponsor
* Product Owner
* Project Manager
* Technical Lead
* QA Lead

A Role is independent from the Person occupying it.

---

## Capability

Represents a professional competency.

Examples:

* Java
* Kubernetes
* Procurement
* Risk Analysis
* Finance

Capabilities belong to Roles or Persons.

---

## Team

Represents a logical group inside the project.

Examples:

* Development
* QA
* Infrastructure
* Business
* Security

Teams contain Roles and Persons.

---

# Governance Entities

## Responsibility

Defines responsibilities assigned to Roles.

---

## Authority

Defines what decisions a Role or Person is authorized to make.

Examples:

* Approve budget
* Approve scope changes
* Accept deliverables

---

## RACI Assignment

Represents participation over an activity.

Possible values:

* Responsible
* Accountable
* Consulted
* Informed

---

# Knowledge Entities

## Requirement

Represents a business or technical need.

Attributes:

* Identifier
* Description
* Source
* Priority
* Status

Relationships:

* Decisions
* Tasks
* Risks
* Artifacts

---

## Decision

Represents an approved or proposed resolution.

Attributes:

* Identifier
* Description
* Date
* Decision maker
* Status

Relationships:

* Requirements
* Risks
* Tasks
* Evidence

Every Decision should be explainable.

---

## Agreement

Represents a commitment reached among participants.

Attributes:

* Description
* Responsible
* Due date
* Status

An Agreement may generate one or more Tasks.

---

## Task

Represents a unit of work.

Attributes:

* Description
* Owner
* Due date
* Status
* Priority

Tasks should always reference their origin whenever possible.

---

## Risk

Represents an uncertain event that may impact project objectives.

Attributes:

* Description
* Probability
* Impact
* Owner
* Mitigation
* Status

Risks may originate from:

* Decisions
* Requirements
* Meetings
* External events

---

## Issue

Represents a problem that has already occurred.

Unlike a Risk, an Issue is an actual event.

---

## Assumption

Represents something considered true without complete validation.

Assumptions should be explicitly documented.

---

## Constraint

Represents a limitation affecting the project.

Examples:

* Budget
* Schedule
* Technology
* Regulation

---

# Artifact Entities

## Artifact

Represents any project deliverable or document.

Examples:

* Charter
* Proposal
* Contract
* Architecture
* WBS
* Test Plan
* Minutes

Attributes:

* Version
* Owner
* Status
* Creation date

Artifacts generate knowledge.

---

## Evidence

Represents the source supporting a fact.

Examples:

* Meeting transcript
* Email
* PDF
* Chat message
* Audio
* Video

Every important conclusion should be linked to Evidence.

---

# Communication Entities

## Meeting

Represents a formal interaction.

Contains:

* Participants
* Agenda
* Transcript
* Recording
* Decisions
* Agreements

---

## Conversation

Represents informal communication.

Examples:

* Chat
* Email thread
* Phone summary

---

# Memory Entities

## Event

The atomic unit of Project Memory.

Examples:

* MeetingHeld
* DecisionCreated
* TaskAssigned
* RiskDetected
* ArtifactUploaded

Events are immutable.

---

## Timeline

Chronological representation of Events.

The Timeline reconstructs project history.

---

# Relationships

Projects contain:

* People
* Teams
* Roles
* Requirements
* Decisions
* Agreements
* Tasks
* Risks
* Artifacts
* Events

Requirements may generate:

* Decisions
* Tasks
* Risks

Decisions may affect:

* Scope
* Budget
* Timeline
* Risks

Agreements may generate:

* Tasks
* Decisions

Artifacts may provide:

* Evidence
* Requirements
* Decisions

Meetings may generate:

* Agreements
* Decisions
* Risks
* Tasks

Events update the Timeline.

The Timeline builds the Project Memory.

---

# Digital Twin Concept

PMOS AI maintains a continuously evolving Digital Twin of every Project.

The Digital Twin is not a document.

It is a structured representation of project reality.

Its purpose is to preserve organizational knowledge and enable intelligent reasoning.

---

# Design Principles

1. Memory before automation.
2. Every fact should have evidence.
3. Roles are independent from people.
4. Events are immutable.
5. State is derived from events.
6. Human approval is required for high-impact decisions.
7. Knowledge should be captured once and reused forever.

---

# Future Extensions

The domain model is expected to evolve with additional entities, including:

* Budget
* Cost
* Change Request
* Milestone
* Dependency
* Deliverable
* Lesson Learned
* Policy
* Approval Workflow
* AI Observation
* Confidence Score

without changing the fundamental philosophy of PMOS AI.

---

# Guiding Statement

PMOS AI does not aim to become a task manager.

PMOS AI aims to become the **system of record for project knowledge and decision intelligence**.
