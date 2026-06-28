# Smart Campus Security AI System

## Quick Overview

এই প্রজেক্টটি একটি AI-based Smart Campus Security, Face Authentication এবং Attendance Management System. সিস্টেমটি student/person database, face recognition AI server, web dashboard, access logging, security alert, photo update review, role-based user management এবং live attendance একসাথে পরিচালনা করতে পারে।

মূল লক্ষ্য হলো campus/lab/classroom access বা attendance process-কে দ্রুত, automated, searchable এবং auditable করা।

---

## 1. System at a Glance

| Area | System Capability |
|---|---|
| Authentication | Username/password based secure login |
| AI Face Recognition | Captured face কে database photo/embedding এর সাথে match করে |
| Access Decision | Match হলে Granted, না হলে Denied/No Match |
| Banned Person Detection | Banned user detect হলে red alert দেখায় |
| Live Camera Detection | Camera/video feed থেকে multiple face detect ও identify করতে পারে |
| Student Management | Student add, edit, delete, search, photo, department, banned status manage করা যায় |
| Bulk Management | CSV/JSON দিয়ে bulk upload এবং embeddings recalculate করা যায় |
| Photo Update Workflow | Staff photo update request দিতে পারে, admin approve/reject করতে পারে |
| Access Logs | কে কখন কোন source থেকে access attempt করেছে, success/denied সহ দেখা যায় |
| Analytics | Total students, embeddings, access source, department-wise access chart |
| Attendance | Course/session based live attendance, manual present, export Excel/PDF |
| User Management | Admin/Manager/Staff/Security Guard/Registration Desk role support |
| API/Mobile Support | Flutter/API login, face check endpoint, photo update API support |

---

## 2. Main Users and Roles

| Role | What They Can Do |
|---|---|
| Admin | Full system control, user management, review/approve actions |
| Manager | Dashboard, analytics, students, logs, attendance, security monitoring |
| Registration Desk | Student registration and photo management |
| Security Guard | Face check / access verification |
| Staff | App/API based face check and assisted photo update |
| Especial | Live detection and live attendance features |

The system uses role-based access control, so every user does not see every feature. This makes the project more secure and suitable for real institutional use.

---

## 3. AI Face Recognition Workflow

1. User opens Face Check or Live Detection.
2. System captures image from camera/upload.
3. Image is sent to AI recognition service.
4. AI extracts face embedding and compares with stored student embeddings.
5. If match is found, system returns student details, confidence, department, database photo, and access status.
6. Every attempt is saved in Access Log.
7. If the matched person is banned or suspicious activity is detected, the system creates a security alert.

### Evidence Screenshot

![Face check granted result](Screenshot%202026-06-28%20220036.png)

This screen shows a successful face match: captured image vs database image, student name, ID, department, confidence score, and Granted status.

---

## 4. Live AI Camera Detection

The system can detect multiple faces from a live camera/video frame. It identifies known persons with green boxes and highlights banned persons with red warning labels.

### Evidence Screenshot

![Live AI face recognition](Screenshot%202026-06-28%20220740.png)

Important points shown here:

- Multiple faces are detected in one frame.
- Known students are labelled by name.
- Unknown faces are marked separately.
- Banned person is highlighted clearly in red.

---

## 5. Dashboard and Analytics

The dashboard/analytics section gives management-level insight:

- Total registered students
- Total generated face embeddings
- Today's access count
- Pending photo requests
- Department-wise access chart
- Access source distribution, such as Web Staff or Live AI Camera
- Advanced management options like bulk upload and embedding recalculation

### Evidence Screenshot

![Analytics and system management](Screenshot%202026-06-28%20215622.png)

This helps the supervisor quickly understand system scale and current activity.

---

## 6. Access History and Audit Log

Every access attempt is stored with:

- Student name and ID
- Success or denied status
- Source/location, such as Web Staff or Live AI Camera
- Date and time
- Search/filter support
- Print PDF and cleanup option

### Evidence Screenshot

![Access history log](Screenshot%202026-06-28%20215641.png)

This makes the system auditable. If someone enters or attempts to enter, the admin can later review the record.

---

## 7. Student Management

The system has a full student management module:

- View all students with photo, ID, name, department, and status
- Search by student ID or name
- Add new student
- Edit student data
- Delete student
- Mark a student active/banned
- Generate and store face embeddings for recognition

### Evidence Screenshot

![Student management](Screenshot%202026-06-28%20215706.png)

This proves the system is not only an AI demo; it includes database management needed for real use.

---

## 8. Photo Update Review Workflow

A practical problem in face recognition systems is outdated student photos. This project solves that with a review workflow:

1. Staff enters student ID.
2. System shows current student data/photo.
3. Staff submits new photo request.
4. Admin reviews old photo vs new photo.
5. Admin approves or rejects.
6. If approved, student photo and embedding can be updated.

### Evidence Screenshots

![Photo update start](Screenshot%202026-06-28%20215744.png)

![Pending photo requests](Screenshot%202026-06-28%20215757.png)

This keeps the database accurate while preventing unauthorized photo replacement.

---

## 9. Attendance Management

The attendance module supports course and session based attendance:

- Select course code and session
- Start/stop attendance
- Mark attendance using AI face recognition
- Upload multiple photos or video file
- Manual "Mark Present" by student ID
- View present/absent sheet by date
- Calculate attendance percentage
- Export attendance as Excel `.xlsx`
- Export attendance as PDF `.pdf`

### Evidence Screenshots

![Attendance export](Screenshot%202026-06-28%20220910.png)

![Live attendance running](Screenshot%202026-06-28%20221011.png)

This makes the system useful for classroom/lab attendance, not only campus security.

---

## 10. User Management

The system includes internal user management:

- Add new system user
- Edit/delete users
- Assign roles
- Active/inactive status
- Current user and admin indicator

### Evidence Screenshot

![System user management](Screenshot%202026-06-28%20215814.png)

This is important for institutional deployment because staff responsibilities can be separated by role.

---

## 11. Navigation and Modules

The top navigation groups the system into understandable modules:

- Dashboard
- Analytics
- AI & Camera
  - Face Check
  - Live Detection
  - Live Attendance
- Students
- User Management

### Evidence Screenshots

![Login screen](Screenshot%202026-06-28%20215320.png)

![AI camera menu](Screenshot%202026-06-28%20215832.png)

---

## 12. Technical Implementation Summary

| Layer | Implementation |
|---|---|
| Backend | Django |
| AI Service | Separate AI server client integration |
| Face Recognition | Face embeddings, model files, cache/FAISS-style fast lookup |
| Frontend | Django templates, Bootstrap, JavaScript camera features |
| Database Models | Person, AccessLog, FailedAttemptLog, PhotoUpdateRequest, SecurityAlert, Course, Attendance |
| Real-time Alert | Django Channels/WebSocket style alert push |
| Notification | Firebase Cloud Messaging support for banned person alerts |
| Export | OpenPyXL for Excel, ReportLab for PDF |
| API | Flutter login, face detection/check, staff photo update |

---

## 13. Important Work Completed

- Built a complete Django web system for Smart Campus Security.
- Implemented student/person database with photo and face embedding storage.
- Integrated AI face recognition service with web/API workflow.
- Added successful and failed access logging.
- Added banned person detection and alert system.
- Created analytics dashboard with charts and key metrics.
- Built student CRUD and bulk management features.
- Built staff-assisted photo update request and admin review workflow.
- Added user roles and permission-based page access.
- Developed live detection and live attendance modules.
- Added course/session attendance sheet with Excel/PDF download.
- Added Flutter/API endpoints for mobile or external app integration.

---

## 14. Suggested Demo Flow for Supervisor

1. Login to the system.
2. Show Analytics page to explain total students, embeddings, and charts.
3. Open Student Management to show the database.
4. Open Face Check and show Granted result.
5. Open Live Detection and explain multiple face/banned detection.
6. Open Access History Log to show audit trail.
7. Open Photo Update Request to show admin review.
8. Open Live Attendance to show course/session attendance and export.
9. Open User Management to explain role-based access.

This order will help the supervisor understand the whole system within a few minutes.

---

## 15. One-Line Project Summary

This project is an AI-powered Smart Campus Security and Attendance Management System that can recognize faces, manage students, detect banned persons, log every access attempt, generate analytics, process photo updates, manage users by role, and create course-wise attendance reports.
