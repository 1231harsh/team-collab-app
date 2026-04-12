# Database Schema – Task Collaboration App

## User
- id (PK)
- name
- email (unique)
- username (unique)     
- password
- created_at

---

## Workspace
- id (PK)
- name
- created_by (FK → User.id)
- created_at

---

## Workspace_Members
- id (PK)
- user_id (FK → User.id)
- workspace_id (FK → Workspace.id)
- role (admin/member)
- joined_at

---

## Project
- id (PK)
- name
- workspace_id (FK → Workspace.id)
- created_by (FK → User.id)
- created_at

---

## Task
- id (PK)
- title
- description
- project_id (FK → Project.id)
- created_by (FK → User.id)
- status (todo / in_progress / done)
- priority (low / medium / high)
- due_date
- created_at

---

## Task_Assignees
- id (PK)
- task_id (FK → Task.id)
- user_id (FK → User.id)

---

## Comment
- id (PK)
- task_id (FK → Task.id)
- user_id (FK → User.id)
- content
- created_at

---

## Message
- id (PK)
- workspace_id (FK → Workspace.id)
- sender_id (FK → User.id)
- content
- created_at

---


# Relationships 

- User ↔ Workspace → many-to-many (Workspace_Members)
      one user can belong to many workspace 
      and
      one workspace can have many users 

- Workspace → Project → one-to-many
      one workspace can have many projects
      and
      one project belongs to exactly one workspace

- Project → Task → one-to-many
      one project can have many tasks
      and
      one task belongs to exactly one project

- Task ↔ User → many-to-many (Task_Assignees)
      one task can be assigned to many users
      and
      one user can be assigned many tasks

- Task → Comment → one-to-many
      one task can have many comments
      and 
      one comment belongs to exactly one task

- Workspace → Message → one-to-many
      one workspace can have many messages
      and
      one message belongs to exactly one workspace

- User → Comment → one-to-many
      one user can have write many comments
      and
      one comment belongs to exactly one user

- User → Message → one-to-many
      one user have many messages
      and 
      one message belongs to exactly one user

---