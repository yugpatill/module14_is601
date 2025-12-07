# Module 14 — Complete BREAD Functionality for Calculations

This project extends the FastAPI calculator application by implementing full **BREAD (Browse, Read, Edit, Add, Delete)** functionality for user-specific calculations. It includes backend APIs, a fully functional front-end interface, Playwright end-to-end tests, and a CI/CD pipeline deploying to Docker Hub.

## 🚀 Features Implemented

### ✔ Backend (FastAPI)
All BREAD endpoints required for Module 14 have been fully implemented:

- **Browse** — GET /calculations  
  Returns all calculations belonging to the authenticated user.

- **Read** — GET /calculations/{id}  
  Returns details for a specific calculation.

- **Add** — POST /calculations  
  Creates a new calculation and computes the result.

- **Edit** — PUT/PATCH /calculations/{id}  
  Updates existing calculations with input validation.

- **Delete** — DELETE /calculations/{id}  
  Removes a calculation without affecting other user data.

All routes enforce:
- JWT authentication  
- Pydantic validation  
- User-level ownership restrictions  

## 🖥️ Front-End Functionality

The front-end supports all BREAD operations:
- Add Calculation form  
- Edit Calculation modal/form  
- Delete confirmation  
- Browse list of calculations  
- View detailed calculation (Read)

Client-side validations include:
- Numeric field checks  
- Allowed operation types  
- Required field checks  

Screenshots of these features are included in the https://github.com/yugpatill/module14_is601/tree/main/Screenshots directory.

## 🧪 Playwright E2E Tests

### Positive Scenarios
- Register & login  
- Add calculation  
- Browse all calculations  
- Read calculation  
- Edit calculation  
- Delete calculation  

### Negative Scenarios
- Invalid operands  
- Invalid operation type  
- Missing authentication token  
- Attempt to access another user’s calculation  

## 🐳 Docker & CI/CD

GitHub Actions automatically:
1. Runs all tests (unit, integration, E2E)  
2. Builds Docker image  
3. Pushes image to Docker Hub if all tests pass  

### Docker Hub Repository  
https://hub.docker.com/repository/docker/yugpatil/601_module14

### Pull the image
docker pull yugpatil/601_module14:latest

### Run the container
docker run -p 8000:8000 yugpatil/601_module14

## 🧪 Running Tests Locally

1. Create and activate virtual environment  
python3 -m venv venv  
source venv/bin/activate  

2. Install dependencies  
pip install -r requirements.txt  

3. Start PostgreSQL  
docker compose up -d db  

4. Run all tests  
pytest  

## ▶️ Running the Application

docker compose up --build  


## 📝 Reflection

This module helped me understand how to implement full BREAD functionality in a real-world application. Although earlier modules covered authentication, models, and basic CRUD operations, this assignment required combining all pieces into a complete workflow that connects backend logic, frontend interaction, and automated tests.

A major insight was understanding how important user-specific calculation filtering is for security. Implementing proper ownership checks and validation strengthened my understanding of secure API design. Front-end validation also improved the usability and reduced server-side errors. One of the challenges I faced was resolving backend issues caused by unnecessary Redis imports. Removing that dependency fixed the failing tests and taught me how small architecture mistakes can create big problems.

Another significant learning moment came from integrating Playwright E2E tests. These tests showed how real users interact with the front end and identified areas that needed adjustments. The CI/CD pipeline brought everything together, ensuring automated builds and deployments to Docker Hub. Overall, this module enhanced my ability to build, test, and deploy a full-stack feature in a reliable and structured way.
