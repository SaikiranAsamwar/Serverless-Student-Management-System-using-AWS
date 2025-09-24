# Student Management System – AWS S3 + DynamoDB + Lambda + API Gateway

This project is a simple **Student Management System** that allows adding and retrieving student data.  
It uses an **HTML + JavaScript frontend** with a **Python backend** and integrates with **AWS S3** for static hosting and **AWS DynamoDB + Lambda + API Gateway** for data storage and retrieval.  

---

## 🚀 Features
- Add new student data via a form (`add_student.html`)  
- Retrieve and display all student records (`fetch_all_students.html`)  
- Backend scripts in Python for data management (`insertStudentData.py`, `getStudents.py`)  
- AWS S3 integration with **Bucket Policy** and **CORS Policy**  
- AWS DynamoDB for structured student storage  
- AWS Lambda functions for serverless backend  
- AWS API Gateway for exposing REST APIs  

---

## 🛠️ Tech Stack
- **Frontend**: HTML, CSS, JavaScript  
- **Backend**: Python + AWS Lambda  
- **Database**: AWS DynamoDB  
- **Storage**: AWS S3 (Static Hosting)  

---

## 📂 Project Structure
```
Student-Management/
│── index.html                 # Homepage
│── add_student.html           # Form to add students
│── fetch_all_students.html    # Fetch and display students
│── scripts.js                 # Frontend logic
│── Notes                      # Notes/documentation
│
│── Python/
│   ├── insertStudentData.py   # Script to insert student data
│   ├── getStudents.py         # Script to fetch student data
│   ├── BucketPolicy.txt       # AWS S3 Bucket policy
│   └── s3-CORS Policy.txt     # AWS CORS configuration
```

---

## ⚙️ Setup Instructions

### 1️⃣ Prerequisites
- Python ≥ 3.7  
- AWS Account with S3 access  
- AWS CLI configured (`aws configure`)  
- Boto3 installed:  
```bash
pip install boto3
```

### 2️⃣ Create DynamoDB Table
- Go to DynamoDB in AWS Console.
- Create a new table:
- Table name: studentData
- Partition Key: studentid (String)
- Leave other settings default and create the table.

### 3️⃣ Create IAM Role
- Go to IAM → Roles → Create Role
- Choose Lambda as trusted entity.
- Attach AmazonDynamoDBFullAccess policy.
- Name the role: LambdaDynamoDBRole
- Save and use this role for Lambda functions.

### 4️⃣ Create Lambda Functions
- We need 2 functions written in Python 3.x:
- Function 1: insertStudentData
- Inserts student data into DynamoDB.
- Function 2: getStudentData
- Retrieves all student records from DynamoDB.
- Steps:
- Go to AWS Lambda → Create Function.
- Runtime: Python 3.x
- Attach the role LambdaDynamoDBRole.
- Write/upload code for insertStudentData and getStudentData.
- Save and test each function.

### 5️⃣ Setup API Gateway
- Go to API Gateway → Create API.
- API Name: student
- Type: HTTP API or REST API
- Create methods:
- POST → insertStudentData Lambda
- GET → getStudentData Lambda
- Deploy API:
- Stage Name: prod
- Deployment at / root path.
- Configure CORS:
- Enable for GET and POST methods.
- Copy the Invoke URL of the deployed API.
- Update scripts.js with this URL.

### 6️⃣ Create S3 Bucket (Static Website Hosting)
- Go to S3 → Create Bucket.
- Upload files:
- index.html
- add_student.html
- fetch_all_students.html
- scripts.js
- Enable Static Website Hosting.
- Add Bucket Policy:
- Use Policy Generator →
- Policy Type: S3 Bucket Policy
- Effect: Allow
- Principal: "*"
- Action: "s3:GetObject"
- Resource: arn:aws:s3:::your-bucket-name/*
- Apply policy.
- Add CORS Policy from Python/s3-CORS Policy.txt.

### 7️⃣ Run Backend (Optional – Local Python)
- For local testing (before Lambda setup), you can run:
```bash
python Python/insertStudentData.py
python Python/getStudents.py
```

### 8️⃣ Run Frontend
- Open index.html in a browser.
- Use add_student.html to add student records.
- Use fetch_all_students.html to view stored records from DynamoDB via API Gateway.

---

## 📌 Future Enhancements
- Add authentication for secure data access  
- Integrate with AWS DynamoDB for structured storage  
- Deploy backend as an AWS Lambda function with API Gateway  
- Add validation and error handling on frontend  

---

## 👨‍💻 Author
Khushal Ravindra Bhavsar✨  
🔗 [LinkedIn Profile](https://www.linkedin.com/in/khushal-bhavsar-/)  
🐙 [GitHub](https://github.com/Khushal41)
- Full Stack MERN Developer | Python & Cloud Enthusiast  
Do you want me to now **append the ready-to-deploy Lambda Python code** for both `insertStudentData` and `getStudentData` directly inside this README so it’s a single reference file?
