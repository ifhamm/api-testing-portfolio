# API Testing Portfolio

## 📑 Overview
This API Testing portfolio utilizes Postman and Newman for testing the ReqRes API (https://reqres.in)

## 🚀 Features Tested
### User Management
- Get Users List
- Get Single User
- Create User
- Update User
- Delete User

### Authentication
- Register User (Unsuccessful)
- Register User
- Login User
- Login User (Unsuccessful)

## 🛠️ Tools & Tech Stack
- Postman v10.x
- Newman
- Newman HTML Reporter
- Git for Windows
- Node.js

## 💻 Prerequisites (Windows)

### 1. Install Node.js
- Download from https://nodejs.org/
- Install with default options
- Open Command Prompt, verify with: `node --version`

### 2. Install Newman
```bash
npm install -g newman
npm install -g newman-reporter-htmlextra
```

### 3. Install Git for Windows
- Download from https://git-scm.com/download/windows
- Install with default options

## 🚀 How to Run (Windows)
1. Clone the repository
```bash
git clone https://github.com/ifhamm/api-testing-portfolio.git
cd api-testing-portfolio
```

2. Run tests
```bash
newman run collection/ReqRes.postman_collection.json -e collection/ReqRes.postman_environment.json -r htmlextra
```

## 📈 Test Reports
- Reports are generated in the `newman/` folder after test execution
- Open HTML files in a browser to view detailed results

# API Testing Portfolio - Detailed Test Cases

## 🔍 Test Cases Detail

### User Management

#### 1. Get All Users
- **Endpoint**: `GET /api/users`
- **Description**: Retrieves a list of users with pagination
- **Tests**:
  - ✅ Status code is `200`
  - ⚡ Response time is less than `1000ms`
  - 📋 Response has correct structure (`page`, `per_page`, `total`, `data`)
  - 📊 `data` is an array
  - 🔍 Each user object contains:
    - `id` (number)
    - `email` (string)
    - `first_name` (string)
    - `last_name` (string)
    - `avatar` (string URL)

#### 2. Get Single User
- **Endpoint**: `GET /api/users/{id}`
- **Description**: Retrieves details of a specific user
- **Tests**:
  - ✅ Status code is `200`
  - ⚡ Response time is less than `1000ms`
  - 🔍 User properties validation:
    - `id` matches request parameter
    - `email` is valid format
    - `first_name` is non-empty string
    - `last_name` is non-empty string
    - `avatar` is valid URL format
  - 📋 Response structure is consistent

#### 3. Create User
- **Endpoint**: `POST /api/users`
- **Description**: Creates a new user
- **Request Body**:
  ```json
  {
    "name": "morpheus",
    "job": "leader"
  }
  ```
- **Tests**:
  - ✅ Status code is `201`
  - ⚡ Response time is less than `1000ms`
  - 🔍 Response validation:
    - Contains `id` and `createdAt`
    - `name` matches request
    - `job` matches request
  - 📋 Content-Type is `application/json`

#### 4. Update User
- **Endpoint**: `PUT /api/users/{id}`
- **Description**: Updates existing user information
- **Request Body**:
  ```json
  {
    "name": "morpheus",
    "job": "zion resident"
  }
  ```
- **Tests**:
  - ✅ Status code is `200`
  - 🔍 Response contains:
    - `name` (string)
    - `job` (string)
    - `updatedAt` (ISO datetime)
  - 📋 Content-Type is `application/json`

#### 5. Delete User
- **Endpoint**: `DELETE /api/users/{id}`
- **Description**: Removes a user from the system
- **Tests**:
  - ✅ Status code is `204`
  - ⚡ Response time is less than `1000ms`
  - 📋 Response body is empty

### Authentication

#### 1. Register User (Successful)
- **Endpoint**: `POST /api/register`
- **Request Body**:
  ```json
  {
    "email": "eve.holt@reqres.in",
    "password": "pistol"
  }
  ```
- **Tests**:
  - ✅ Status code is `201`
  - 🔑 Response contains token
  - 📋 Token format validation
  - ⚡ Response time validation

#### 2. Register User (Unsuccessful)
- **Endpoint**: `POST /api/register`
- **Request Body**:
  ```json
  {
    "email": "sydney@fife"
  }
  ```
- **Tests**:
  - ❌ Status code is `400`
  - 🔍 Error message contains "Missing password"
  - 📋 Error response structure validation

#### 3. Login User (Successful)
- **Endpoint**: `POST /api/login`
- **Request Body**:
  ```json
  {
    "email": "eve.holt@reqres.in",
    "password": "cityslicka"
  }
  ```
- **Tests**:
  - ✅ Status code is `200`
  - 🔑 Token presence and format
  - 📋 Response structure validation

#### 4. Login User (Unsuccessful)
- **Endpoint**: `POST /api/login`
- **Request Body**:
  ```json
  {
    "email": "peter@klaven"
  }
  ```
- **Tests**:
  - ❌ Status code is `400`
  - 🔍 Error message validation
  - 📋 Error response structure

### Resources

#### 1. List Resources
- **Endpoint**: `GET /api/unknown`
- **Description**: Retrieves list of available resources
- **Tests**:
  - ✅ Status code is `200`
  - 📊 Response contains array of resources
  - 🔍 Resource object validation:
    - `id` (number)
    - `name` (string)
    - `year` (number)
    - `color` (string)
    - `pantone_value` (string)
  - 📋 Pagination support verification

#### 2. Single Resource
- **Endpoint**: `GET /api/unknown/{id}`
- **Description**: Retrieves specific resource details
- **Tests**:
  - ✅ Status code is `200`
  - 🔍 Resource data validation
  - 📋 Content-Type verification
  - ⚡ Response time validation

## 📈 Test Coverage Summary
- Total Endpoints Tested: 10
- Total Test Cases: 40+
- Types of Testing:
  - ✅ Functional Testing
  - ⚡ Performance Testing
  - 🔑 Security Testing
  - 📋 Data Validation
  - ❌ Negative Testing

## 🔄 Automation Execution
Tests are automated using Postman/Newman and run daily via GitHub Actions pipeline.
