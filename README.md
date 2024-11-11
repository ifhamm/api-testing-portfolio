# API Testing Portfolio

## 📑 Overview
API Testing portfolio menggunakan Postman dan Newman untuk ReqRes API (https://reqres.in)

## 🚀 Features Tested
- User Management
  - Get Users List
  - Get Single User
  - Create User
  - Update User
  - Delete User
- Authentication
  - Login
  - Register

## 🛠️ Tools & Tech Stack
- Postman v10.x
- Newman
- Newman HTML Reporter
- Git for Windows
- Node.js

## 💻 Prerequisites (Windows)
1. Install Node.js
   - Download dari https://nodejs.org/
   - Install dengan opsi default
   - Buka Command Prompt, ketik: `node --version`

2. Install Newman
   ```cmd
   npm install -g newman
   npm install -g newman-reporter-htmlextra
   ```

3. Install Git for Windows
   - Download dari https://git-scm.com/download/windows
   - Install dengan opsi default

## 🚀 How to Run (Windows)
1. Clone repository
   ```cmd
   git clone https://github.com/[username]/api-testing-portfolio.git
   cd api-testing-portfolio
   ```

2. Run tests
   ```cmd
   newman run collection/ReqRes.postman_collection.json -e collection/ReqRes.postman_environment.json -r htmlextra
   ```

## 📈 Test Reports
- Reports akan dibuat di folder `newman/` setelah test dijalankan
- Buka file HTML di browser untuk melihat hasil detail

## 📱 Screenshots
![API Test Results](screenshots/test-results.png)

## 🔍 Test Cases Detail
1. Get Users
   - Verify status code 200
   - Verify response time < 1s
   - Verify data structure
   
2. Create User
   - Verify status code 201
   - Verify user data created
   
3. Update User
   - Verify status code 200
   - Verify data updated

4. Delete User
   - Verify status code 204
