---
description: Guide for writing an API specification for a new backend feature
globs:
alwaysApply: false
---

# Rule: Writing an API Specification for a New Feature

## Goal

To guide an AI assistant in creating a clear and thorough **API specification** in Markdown format for a new backend feature. This spec should detail all new or changed API endpoints, including request and response formats, so that front-end developers or external integrators know exactly how to use the API, and back-end developers understand what to implement. It serves as a contract for how the front-end and back-end communicate.

## Process

1. **Understand the Feature:** Start by reviewing the feature description or PRD to understand what functionality the API needs to provide. Clarify the feature’s requirements in terms of data input/output and operations. If any aspect of the feature’s API usage is unclear, ask clarifying questions (e.g., “Will this feature require creating new data or just reading data?”, “Do we need multiple endpoints for different user roles?”).
2. **Determine API Style:** Identify whether the API is RESTful, GraphQL, gRPC, etc., as this will affect how you document it. (Assume RESTful JSON over HTTP if not specified, since that’s common.)
3. **List Endpoints:** Enumerate all API endpoints that need to be defined for this feature. This includes new endpoints and any existing endpoints that might be modified. For REST, define each by the HTTP method and path (e.g., **GET /users/{id}/profile**).
4. **Specify Each Endpoint:** For each endpoint, document the following details:
   - **Endpoint Name/Description:** e.g., “**GET /profiles/{id}** – Retrieve user profile details.”
   - **Purpose:** A brief description of what the endpoint does and in what scenario it’s used.
   - **Request Format:** 
     - HTTP Method (GET, POST, PUT, PATCH, DELETE, etc.).
     - URL Path with parameters (if any). Document any path params (e.g., `{id}`) and query parameters.
     - Headers required (e.g., auth tokens, content type if not JSON).
     - Request Body (if applicable): Show the JSON (or other format) schema or an example of the request payload. Include field names, types, which are required vs optional, and meaning of each.
   - **Response Format:** 
     - For success (usually HTTP 200/201/204 depending on operation): Show an example JSON response body (if any) with explanation of each field, or describe what happens (e.g., “returns 204 No Content on success”).
     - For errors: List possible error status codes and what they mean (e.g., “400 Bad Request if X is invalid, 404 Not Found if ID not exists, 401 Unauthorized if auth fails”). Include example error response bodies if the API uses a standard error format.
   - **Authentication/Authorization:** Note if this endpoint requires authentication (e.g., a token) or certain user roles/permissions.
   - **Idempotency or Side Effects:** If applicable, mention any idempotency guarantees (e.g., safe to retry) or important side effects (e.g., “this call sends an email verification”).
5. **Organize the Specification:** Structure the document so that each endpoint is a subsection (### or #### heading). Group related endpoints under a higher-level section if appropriate (for example, group all “Profile” related endpoints together).
6. **Include Examples:** Provide example requests (with curl or HTTP examples) and responses for clarity. E.g., a small code block showing a sample JSON request body and a sample JSON response body for a typical case. This greatly helps understanding.
7. **Review for Completeness:** Check that every requirement of the feature is covered by an endpoint in the spec. Ensure there are no undefined aspects (like “somehow this data gets to the server” – each such scenario should have an endpoint).
8. **Conform to Standards:** Ensure that naming conventions for endpoints, fields, and error handling match the project’s existing API style (if there is one). For instance, consistent snake_case vs camelCase in JSON keys, singular vs plural nouns in endpoints, etc.
9. **Finalize:** Once all endpoints are documented, read through the entire spec as if you were a developer trying to use the API. See if anything is confusing or missing and adjust accordingly.

## API Spec Structure

Here’s a suggested structure for the API spec document:

- **Introduction:** (Optional) One-liner about the feature and the API’s role (e.g., “This document describes the API endpoints for the Profile Editing feature.”) Include any general prerequisites, like “All endpoints require Authentication token in header” if that’s the case globally.
- **Authentication:** (Optional) If not already obvious, state how auth is done (e.g., “All endpoints require a valid JWT token in the `Authorization` header: `Bearer <token>`.”). If each endpoint has different auth, you can specify per endpoint instead.
- **Endpoints:** For each endpoint, use a third-level heading. For example:  
  **`### GET /api/v1/profiles/{id}`**  
  Then under that heading, include sub-sections or a consistent format covering Description, Request, Response, etc. For example:
    - **Description:** One sentence on what it does.
    - **Request:** (Method/Path, Query Params, Body, Headers as needed.)
    - **Response:** (Status codes and bodies.)
    - **Errors:** Possible errors and what they mean.
    - **Example:** (You can embed a short code block of a sample request/response.)
- Repeat for each endpoint.
- **Data Models:** (Optional) If it helps, you can define the data model schemas separately (e.g., “Profile object schema” with its fields) to avoid repetition if multiple endpoints use the same object. This can also be done inline in each endpoint.
- **Pagination or Other Details:** (Optional) If the endpoints involve pagination, filtering, or other standardized mechanisms, document how those work (e.g., “This list endpoint supports `?page=` and `?pageSize=` query parameters. Response will include `totalCount`,” etc.).
- **Change Log:** (Optional) If updating existing endpoints, note what changed compared to previous version.

## Target Audience

The API spec will be read by other developers (front-end engineers, mobile developers, third-party developers) and by back-end developers implementing or maintaining the API. Therefore:
- It should be **precise and unambiguous** so that anyone reading knows exactly what to send and what to expect.
- Use consistent terminology (if the PRD calls something "Profile", use that term in the API, etc.).
- Assume the reader has technical knowledge but not necessarily familiarity with this specific system, so provide context where needed (like what a “profile” means in our application domain).
- The tone can be straightforward and factual, focusing on the technical details.

## Output

- **Format:** Markdown (`.md`) document with clearly marked sections and examples. Use backticks and code blocks for illustrating example JSON or HTTP exchanges.
- **Location:** Save in a documentation area of the repo, e.g., `/docs/api-[feature-name].md` or in the tasks directory if that's where design docs are kept.
- **Filename:** `api-spec-[feature-name].md` or similar (e.g., `api-profile-editing.md` for a feature about profile editing).
- If the project has an OpenAPI/Swagger specification, note that this Markdown is a human-friendly summary; it’s not a replacement for an OpenAPI JSON/YAML (though it could be derived from one).

## Final Instructions

1. **No Actual Code Implementation:** This is a specification document. Do not write any source code or function implementations here. Focus only on the interface (the API contract).
2. **Consistency is crucial:** Ensure that field names, endpoint URLs, and behavior described are consistent throughout the document and with any existing API conventions. If the project uses British English vs American (colour vs color), or certain phrasing (“create” vs “add”), stick to it.
3. **Seek Confirmation:** If you (the AI) are unsure about a particular API detail (for example, whether an endpoint should be split into two), ask the user rather than making an assumption. The spec must reflect what the product should do.
4. **Examples must be realistic:** When giving example requests and responses, use realistic sample data (e.g., a plausible user name, IDs that look like real IDs, etc.) to avoid confusion.
5. **Review and Revise:** After drafting, double-check each endpoint spec against the feature requirements one by one to ensure nothing was missed. It can help to imagine a developer trying to implement the front-end: would they have all the info they need from this doc? If not, add the missing details.
