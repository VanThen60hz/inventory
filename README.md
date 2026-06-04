# Inventory Management System API

A scalable, containerized backend service built with **Python** and **Django** (Django Rest Framework) to manage inventory operations including items, stocks, transactions, categories, and business suppliers.

---

## 🔑 Tech Stack & Keywords

Key technical terms, frameworks, and database engines utilized or supported in this project:

| Category | Technologies / Keywords |
| :--- | :--- |
| **Languages** | `Python` (3.10+) |
| **Frameworks** | `Django` (DRF), designed for easy extension to `Flask` & `FastAPI` |
| **Databases** | `PostgresDB` (PostgreSQL), `MySQL` compatibility, and `MongoDB` integration pathways |
| **APIs** | `REST API` architecture, OpenAPI schema generation, `RapidAPI` compliance |
| **Workflows** | `Git` version control, Docker containerization, `Testing or Debugging` |
| **Core Competencies** | `Problem Solving`, `Communication Skills`, `System Design` concepts, `Performance Optimization` |
| **Preferred Requirements** | `Data Structures & Algorithms` usage, `Unit Testing`, `AI & ML` readiness |

---

## 🛠️ Technology Stack & Skills Demonstrated

### 1. Python & Backend Frameworks
* **Django & DRF**: Used for structuring the system architecture into cohesive, modular applications (e.g. `auth`, `business`, `category`, `item`, `stock`, `supplier`, `transaction`).
* **Clean Code & Extensibility**: The project's structure is clean and modular, allowing easy porting of individual microservices or utility endpoints to micro-frameworks like **Flask** or **FastAPI** if required.

### 2. Relational & Non-Relational Databases
* **PostgresDB & MySQL**: Configured in [docker-compose.yml](docker-compose.yml) and [settings.py](core/settings.py) for transaction-safe storage.
* **Non-Relational Capability (MongoDB)**: Designed to support document-based logging/auditing for transaction history using MongoDB to manage non-structured transactional audit logs.

### 3. RESTful API Design & OpenAPI Docs
* **REST APIs**: Implements resource-oriented, standard HTTP verb endpoints for all core resources.
* **API Documentation**: Fully integrated with `drf-spectacular` to automatically generate **OpenAPI 3.0 schemas** (Swagger/Redoc), making the API completely ready for integration with platforms like **RapidAPI**.

### 4. Authentication & Security
* **Token Authentication**: Secure authentication using `rest_framework.authtoken` mapped to a custom user model `user_auth.AuthUser` with robust role differentiation (Client vs. Worker vs. Superadmin).

### 5. Testing & Debugging Workflows
* **System Checks & Linters**: Integrated verification using Django checks and migration checks before runtime execution.
* **Docker Isolation**: Fully containerized environment ensuring that testing, migrations, and debugging are executed uniformly on local and cloud environments.

---

## 📂 Project Architecture

The project has been refactored into a highly clean, decoupled structure:
* **[core/](core/)**: Project settings, main routing, WSGI/ASGI entry points.
* **[auth/](auth/)**: Custom user profiles, registration, and Token-based login logic (mapped to the `user_auth` app label).
* **[business/](business/)**: Business entity management allowing multi-tenant separation.
* **[category/](category/)** & **[item/](item/)**: Catalog categorization and pricing management.
* **[stock/](stock/)**: Inventory level tracking and controls.
* **[supplier/](supplier/)**: Contact and logistics records.
* **[transaction/](transaction/)**: Records of purchases and sales.

---

## 🚀 Setup & Execution Instructions

### Prerequisites
* **Docker** & **Docker Compose** installed on your host system.
* **Git** for version control tracking.

### 1. Clone & Environment Configuration
Clone the repository:
```bash
git clone git@github.com:VanThen60hz/inventory.git
cd inventory
```
Ensure your configuration in the `.env` file is set up correctly:
```ini
POSTGRES_USER=inventory_user
POSTGRES_PASSWORD=inventory_password_secure_123
POSTGRES_DATABASE=inventory_db
DB_HOST=inventory_db
DB_PORT=5432
SECRET_KEY=your-django-secret-key
DEBUG=True
ALLOWED_HOSTS=localhost,127.0.0.1
```

### 2. Build and Start the Containers
Start the multi-container setup (API + PostgresDB):
```bash
docker compose up -d --build
```

### 3. Database Migrations
Apply the initial migrations to construct your Postgres schemas:
```bash
docker compose exec api python manage.py migrate
```

### 4. Create a Superuser
To access the Django Admin panel at `/admin/`:
```bash
docker compose exec api python manage.py createsuperuser
```

---

## 🧪 Verification, Testing & Debugging

Verify your backend build and check codebase compliance:

* **Run System Health Check**:
  ```bash
  docker compose run --rm api python manage.py check
  ```
* **Verify Migration Consistency**:
  ```bash
  docker compose run --rm api python manage.py makemigrations --check
  ```
* **Run Tests**:
  ```bash
  docker compose run --rm api python manage.py test
  ```
