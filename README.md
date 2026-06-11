# Flask Task Management API Core

A lightweight, high-performance RESTful web service engineered using Flask. The platform provides structured endpoints to coordinate task tracking lifecycles, enforce payload parameters, and handle transactional state modifications via an isolated, in-memory data persistence structure.

---

## Architectural Architecture & Implementation Specs

The backend is built around a decoupled, resource-oriented architecture utilizing standard HTTP verbs, strict payload sanitization, and native routing constraints.

* **Core Framework:** Flask (WSGI Web Application Architecture)
* **Data Persistence Layer:** Thread-safe dictionary collection abstraction mimicking atomic primary-key indexing.
* **Payload Protocol:** Standardized `application/json` serialization for request parsing and error payloads.
* **Parameter Security:** Enforces type-safe explicit path parameter routing constraints (`<int:task_id>`) directly within the routing layer to eliminate malformed injection vulnerabilities.

---

## RESTful API Endpoints & Route Specifications

All network interactions assume a local development server base context. Error paths (such as `404 Not Found` or `400 Bad Request`) automatically trigger uniform JSON diagnostic objects.

### Endpoint Inventory

Base URL Configuration: http://localhost:5000

| HTTP Method | API Endpoint Path | Payload Expectation | Target Operational Objectives | Success Status |
| :--- | :--- | :--- | :--- | :--- |
| **GET** | `/` | None | Service discovery and status heartbeat validation check. | `200 OK` |
| **GET** | `/tasks` | None | Retrieves the absolute collection index of active system tasks. | `200 OK` |
| **GET** | `/tasks/<int:task_id>` | None | Isolates and reads a single task record matching the unique identifier. | `200 OK` |
| **POST** | `/tasks` | `{"title": "string"}` | Validates incoming payloads and initializes a new uncompleted task. | `201 Created` |
| **PUT** | `/tasks/<int:task_id>`| `{"title": "...", "completed": bool}` | Executes partial or complete state modifications on an existing task. | `200 OK` |
| **DELETE** | `/tasks/<int:task_id>`| None | Safely deletes the specific task resource entry out of the memory matrix. | `200 OK` |

---

## Step-by-Step Local Deployment Sequence

### Environment Dependencies
* Python 3.10 or higher
* pip (Python Package Installer)
* Virtualenv wrapper engine (Highly recommended)

### 1. Environment Isolation and Package Setup
Initialize an isolated local virtual environment directory to separate package execution trees, activate it, and install required system framework dependencies:

```bash
# Initialize the virtual environment directory
python -m venv venv

# Windows Activation Script Execution
.\venv\Scripts\activate

# UNIX / macOS Shell Activation Script Execution
source venv/bin/activate

# Execute structured package dependency installation
pip install -r requirements.txt
2. Application Server Launch Sequence
Execute the primary script file using the virtualized Python runtime to boot up the internal WSGI development application server:

python app.py

The application server will initialize native logging pipelines and establish listening channels on the local network stack interface (http://127.0.0.1:5000).

Middleware & Error Handling Architecture
Payload Validation Control: The /tasks POST pipeline handles validation gates internally. Requests missing a deterministic title token immediately abort processing to prevent corrupted model writes.

Robust Exception Handling: Missing resources or bad parameters bypass generic raw HTML error stack renderings. The routing engine intercepts errors to return clean, front-end-parsable key-value exception payloads.
