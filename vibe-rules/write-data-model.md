---
description: Guide for documenting a database schema or data model changes
globs:
alwaysApply: false
---

# Rule: Writing a Data Model / Database Schema Document

## Goal

To guide an AI assistant in creating a clear description of the database schema for a new feature or an update to the existing data model. This documentation should detail the structure of the data (tables/collections, fields, relationships) in Markdown format so that developers and database administrators can understand and implement the necessary changes. It should cover what new data entities are introduced or how existing ones are modified, and why those changes are made, all in an organized manner.

## Process

1. **Understand Feature Data Requirements:** Begin by reviewing the feature or change that prompts this schema update. Identify what data needs to be stored or modified. For example, a “profile editing” feature might require adding new fields to a User table like `bio` or `avatar_url`. If unclear, ask questions to clarify data needs (e.g., “Will we need to store multiple addresses per user?”).
2. **Identify New vs Existing Schema Elements:** Determine if the feature will introduce new database entities (tables/collections) or just changes to existing ones. List all the entities that will be involved or affected.
3. **Outline the Document Structure:** Plan sections for each entity. A common structure is to have a section per table (or collection), listing its fields and any related constraints or indexes. Also include sections for relationships between entities. (See **Schema Document Structure** below.)
4. **Document Each Entity (Table):** For each relevant table or collection:
   - Provide a heading with the entity name (e.g., **Users Table** or **Order Collection**).
   - If it’s new, label it clearly as “(New)” next to the name.
   - If it’s an existing table being modified, list only the changes first (like new fields, changed data types) for quick reference, then provide the full updated schema.
   - List all fields/columns with:
     - **Name** – The column/field name.
     - **Type** – Data type (e.g., INT, VARCHAR(255), TEXT, DATE, JSON, etc., or for NoSQL describe the data structure).
     - **Constraints/Attributes** – Note if it’s Primary Key, Foreign Key (and references which table), Not Null, Unique, Indexed, Default value, Auto-increment, etc.
     - **Description** – A short note on what the field represents or any important details (e.g., units for a numeric field, format for a date, etc.).
   - Example (in Markdown table form or list):
     ```
     | Field Name    | Type          | Constraints        | Description                         |
     |--------------|---------------|--------------------|-------------------------------------|
     | user_id      | INT           | PK, auto-increment | Unique identifier for each user.    |
     | name         | VARCHAR(100)  | NOT NULL           | User’s full name.                   |
     | bio          | TEXT          | NULL allowed       | User’s biography or profile info.   |
     | created_at   | DATETIME      | DEFAULT now()      | Timestamp of account creation.      |
     ```
   - Alternatively, you can use bullet points or sub-bullets for each field if tables are not desired.
5. **Document Relationships:** After listing individual tables, describe how they relate:
   - Identify foreign keys and what they link to. E.g., “In the **Orders** table, `user_id` is a foreign key referencing `Users(user_id)` establishing a many-to-one relationship (many orders per user).”
   - Mention any many-to-many relationships and the join tables that implement them.
   - If using a NoSQL schema, describe the nested structures or reference patterns.
6. **Include ER Diagram (Optional):** If the schema is complex or if a visual aid would help, include a simple Entity-Relationship diagram. This can be done via a Mermaid diagram in the markdown:
   ```mermaid
   erDiagram
      USERS ||--o{ ORDERS : places
      USERS {
         int user_id PK
         string name
         ...
      }
      ORDERS {
         int order_id PK
         int user_id FK
         ...
      }
    ```
(The above mermaid block is just an illustration of syntax; include the actual schema details.)
7. **Migration or Change Details:** If this is an update to an existing schema, clearly state what changes are needed:
- New tables to create.
- New columns to add (and default values or whether they can be null initially).
- Columns to modify (type changes, making null -> not null, etc.).
- Columns or tables to drop (if any).
- Provide the migration strategy if relevant (e.g., “Backfill existing users’ bio with empty string to satisfy NOT NULL before applying constraint”).
- If using an ORM or migration tool, you might outline what steps that migration would take.
8. **Review for Consistency:** Ensure naming conventions are consistent with the existing database (e.g., use snake_case if that’s the project standard, singular vs plural table names consistently, etc.). Ensure that all new fields have appropriate types and sizes (e.g., don’t use an INT if you might need big integers, or use TEXT vs VARCHAR appropriately).
9. **Finalize the Documentation:** Double-check all field details, constraints, and relationships. The document should allow a developer or DBA to implement the schema without confusion. It should also serve as a reference for future when others need to understand the data model.

## Schema Document Structure

A suggested layout for the markdown document might be:

- **Introduction:** Brief summary of the change: “This document describes the database schema changes for the XYZ feature. It introduces a new table ABC and adds two columns to the existing DEF table…”
- **New/Updated Entities:** For each table/collection:
- **Table: XYZ** (New or Updated) – then either a table of fields or a list.
- Fields and their types/constraints (as detailed above).
- **Relationships:** Explain foreign keys and relationships between tables.
- **Example Records (Optional):** Sometimes useful, provide an example of what a sample record might look like for the new/updated table, especially if JSON or complex structure.
- **Migration Strategy:** Steps or notes on applying these changes to an existing database. E.g., “Add column with default, migrate data, then apply NOT NULL constraint.”
- **Conclusion:** (Optional) Any additional notes, such as implications for performance (e.g., “Index on email was added to ensure lookup speed”) or future considerations.

## Target Audience

Assume the readers are developers (and possibly DBAs) who will implement these changes or need to understand the data model. The language can be technical, using standard database terminology. Be explicit about constraints and data types to avoid any ambiguity.

- Use consistent naming (if the app uses American spelling, stick to it; if abbreviations are used in schema, define them if not obvious).
- If this project uses a particular database (MySQL, PostgreSQL, MongoDB, etc.), use the appropriate data type conventions for that DB (e.g., PostgreSQL uses TEXT, MySQL might use VARCHAR, etc.).
- If any decision might be non-obvious, provide a short rationale (e.g., “Using a separate table for user preferences to keep the Users table slim; this allows optional data without null columns”).

## Output

- **Format:** Markdown (`.md`) file with sections and (ideally) Markdown tables for field listings for readability.
- **Location:** Likely in a `/docs/` directory or in the repository’s documentation area. Perhaps name it under a `schema/` or `design/` folder. For example, `docs/data-model-[feature].md` or `tasks/[feature]-data-model.md`.
- **Filename:** Descriptive, e.g., `data-model-profile-feature.md` or `schema-update-2025-08.md` (if tied to a date or sprint).
- **Diagrams:** If using Mermaid ER diagrams or similar, ensure they are included as fenced code blocks. If not using diagrams, ensure textual relationship descriptions are clear.

## Final Instructions

1. **Accuracy over Guessing:** If any detail about the data model is uncertain, do not fill it with an assumption. Mark it as an open question or confirm with the user. (E.g., “The length of the `name` field is assumed to be 100 characters; please confirm if a different length is needed.”)
2. **No Code Changes:** This is a design/documentation task. Do not alter actual database or code in this step. We are only writing the documentation of what needs to be done.
3. **Keep Future in Mind:** If this feature might evolve, ensure the data model is scalable (you can mention considerations like “We use a separate table for X anticipating future expansion”). However, do not overdesign; stick to what’s needed now and clearly label speculative sections if any.
4. **Review by Example:** It can be helpful to walk through a use case with the new schema mentally. For instance, imagine creating a new record for the feature: does every necessary piece of data have a place in the schema? If not, the schema might be missing something.
5. **Clarity:** Someone else should be able to read this document and implement the exact same database changes. Aim for that level of clarity. Use bullet points, tables, and examples to make it digestible.
