# FastAPI_MCP_ToDoList_API


A backend service implemented with FastAPI and SQLAlchemy that exposes a RESTful CRUD API
and a Model Context Protocol (MCP) interface, enabling deterministic invocation of backend
operations by LLM clients.

The project demonstrates how an existing HTTP API can be augmented with MCP without
altering its REST contract, frontend behavior, or deployment model.

---

## Overview

This application is a complete backend service built with FastAPI and SQLAlchemy.
It persists data using SQLite and exposes a structured CRUD API over HTTP.

In addition to the standard REST interface, the service integrates **Model Context Protocol (MCP)**.
MCP allows Large Language Model (LLM) clients (e.g. VS Code Copilot Chat, Cursor) to invoke backend
operations as typed tools derived from explicit OpenAPI `operation_id`s.

The MCP layer is strictly additive and does not modify or replace the HTTP API.

---

## Key Characteristics

- Fully implemented REST API
- Persistent storage using SQLite
- SQLAlchemy ORM with explicit schema mapping
- Pydantic-based request and response validation
- Explicit OpenAPI `operation_id`s for all endpoints
- MCP endpoint exposed via HTTP
- Strict allowlist of MCP-exposed operations
- Deterministic tool contracts for LLM clients

---

## Technology Stack

- Python 3.10+
- FastAPI
- SQLAlchemy
- SQLite
- Pydantic
- Uvicorn
- fastapi-mcp

---

## Data Model

The application manages a single persistent resource.

| Field      | Type    | Description                  |
|-----------|---------|------------------------------|
| id        | integer | Primary key                  |
| content   | string  | Resource payload             |
| completed | boolean | Resource state flag          |

The simplicity of the model is intentional and isolates architectural and integration concerns.

---

## REST API

### Endpoints

- `GET /resources`  
  Retrieve all resources.

- `GET /resources/{id}`  
  Retrieve a single resource.

- `POST /resources`  
  Create a new resource.

- `PUT /resources/{id}`  
  Update an existing resource.

- `DELETE /resources/{id}`  
  Delete a resource.

### Example Request

```json
{
  "content": "example payload",
  "completed": false
}
