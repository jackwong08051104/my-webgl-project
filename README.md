# Student Attendance Management System

## 1. Project Info

- **Project Name**: Vattend
- **Group**: Group 6
- **Students**:
  - Ha Howard (SID: 14151126)
  - Yau Yin Hei Donald (SID: 13179623)
  - Wong Shi Yuen (SID: 1415872)
  - Cheung Pak Lam (SID: 14196119)
  - Lai Yuk Leung (SID: 14110156)

---

## 2. Project File Introduction

### server.js

This is the main server file. It does:
- Uses Express to create a web server on port 8099
- Connects to MongoDB Atlas (database name: serverDB, collection: data)
- Handles login/logout with sessions
- Lets users register (can be Teacher or Student)
- Shows different pages for teachers and students
- Teachers can see all students, update/delete student info
- Students can view their own info and mark attendance
- Has a search function to find students by gender or course ID
- Can reset attendance records

### package.json

Dependencies used:
- express - for the web server
- ejs - for rendering HTML pages
- body-parser - to read form data
- cookie-session - for login sessions
- mongodb (version 6.9.0) - to connect to database

### views folder

EJS files:
- login.ejs - the login page
- register.ejs - registration page
- teacher.ejs - teacher's main page with student list
- student.ejs - student's main page with their info
- studentdata.ejs - shows one student's details (for teachers)
- search.ejs - page to search for students

---

## 3. Cloud-based Server URL

https://comp3810sef-group6.onrender.com/

---

## 4. Operation Guides

### 4.1 Login/Logout

Test accounts:

Teacher:
- Username: s1
- Password: 1

Student:
- Username: s1317555
- Password: 1317555

How to login:
1. Go to the URL above
2. Enter username and password
3. Click Login
4. You'll see different pages depending on if you're a teacher or student
5. Click Logout when you want to exit

### 4.2 CRUD Web Pages

**Create:**
- Teachers can click "Register" to add new users

**Read:**
- Teachers see all students on the main page, click on a student to see details
- Students see their own info on their page
- Teachers can use "Search for Students" to find students by gender or course ID

**Update:**
- Teachers can click "Update Course ID" to change a student's course
- Students click "Attend" button to mark attendance
- Teachers can click "Reset Attendance Records" to clear all attendance

**Delete:**
- Teachers can click "Delete Student" to remove a student account

### 4.3 RESTful CRUD Services

CURL commands to test:

```bash
# Login
curl -i -L -c cookies.txt -b cookies.txt \
  -H "Content-Type: application/x-www-form-urlencoded" \
  -d "name=s1&password=1" \
  https://comp3810sef-group6.onrender.com/login

# View student data
curl -i -L -b cookies.txt https://comp3810sef-group6.onrender.com/studentdata/s1011165

# Update student course ID
curl -i -X PUT https://comp3810sef-group6.onrender.com/studentdata/s1011165 \
  -H "Content-Type: application/json" \
  -d '{"courseID":"COURSE_ID"}'

# Delete student
curl -i -X DELETE https://comp3810sef-group6.onrender.com/studentdata/USERNAME

# Record attendance
curl -i -X POST https://comp3810sef-group6.onrender.com/attendance/s5555557
```
