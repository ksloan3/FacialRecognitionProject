##UniPass User Manual

#1. Overview UniPass is our custom-built alternative to Duo Push, offering secure face-based multi-factor authentication and a student database management interface. It supports two roles: Student: Log in with face recognition to view personal academic details.

Admin: Authenticate via face presence detection to search, review, and manage student records.

#2. Prerequisites

System Requirements Operating System: Windows, macOS, or Linux

1)Python 3.7 or higher

2)Webcam for facial recognition

3)Required Python packages:

4)OpenCV (opencv-python and opencv-contrib-python)

5)Pillow

6)NumPy

#3. Files & Directory Structure project_root/ ├── unipass.db # SQLite database (auto-created at first launch) ├── faces/ # Directory for storing face images │ ├── [student_id].png # Student face images (e.g., "S12345.png") │ └── admin_[admin_id].png # Admin face images (e.g., "admin_A101.png") ├── gui.py # Main application file (GUI + business logic) └── requirements.txt # Python dependencies (optional but recommended)

#4. Launching the Application

Open a terminal and navigate to the project root: cd /path/to/project_root
Run the script: python3 gui.py
The UniPass window will appear.
#5. Mock Website Testing

Start the mock website server on localhost:8000.
In your browser, go to http://localhost:8000.
On the page, click Student Login or Admin Login.
A UniPass window pops up for facial recognition (2FA).
After successful validation, the mock site grants access.
Click Logout on the site to end the session.
#6. Using UniPass Student Features

A. Student Sign-Up (First-Time Users) 1.Click "Student Sign Up" on the Login tab. 2.Fill in your details: 3.ID (e.g., S1001), Name, Year(e.g., "Freshman"), Major, GPA 4.Click "Capture & Create" to register your face: 5.Position yourself in front of the camera. 6.Press 'c' to capture when your face is detected. 7.Press 'q' to cancel. ->Your account will be created, and you can now log in.

B. Student Login 1.Click "Student Face Login" on the Login tab. 2.Look into the camera and press 'c' to authenticate. ->If successful, you’ll be taken to the Student Dashboard.

C. Student Dashboard Features 1.View Personal Info: Displays your ID, name, year, major, and GPA. 2.View Classes: 3.Click "View Classes" to see your registered courses. a.Tuition Payment: 1.Click "View Tuition" to check your balance. 2.If unpaid, click "Pay Now" to mark tuition as paid. 3.Logout: Click "🔙 Logout" to return to the login screen.

D. Admin Features a.Admin Sign-Up (First-Time Admins) 1.Click "Admin Sign Up" on the Login tab. 2.Fill in: 2.1.Admin ID (e.g., A101) 2.2.Name 2.3.Admin Password (Default: admin123) b.Click "Capture & Create" to register your face. ->Your admin account will be created.

E. Admin Login 1.Click "Admin Face Login" on the Login tab. 2.Look into the camera and press 'c' to authenticate. ->If successful, you’ll see the Admin Panel.

F. Admin Panel Features 1.View All Students: 2.Click "👥 View All Students" to see a full list. 3.Edit/Delete students by selecting them. 4.Register New Admin: 4.1.Click "➕ Register New Admin" to add another admin. 5.Add Classes to a Student: 5.1.Click "➕ Add Classes to Student". 5.2.Enter the Student ID and course details. 6.Update Tuition: 6.1.Click "💰 Update Tuition". 6.2.Enter the Student ID and new amount. 7.Logout: Click "🔙 Logout" to exit.

#8. CSV Import / Export Export: File → Export CSV → saves all records to a .csv.

Import: File → Import CSV → loads records; existing IDs are skipped.

#9. Database & Repository

Database: unipass.db contains tables:
students (ID, name, graduation year, major, GPA, face_image)
tuition (student_id, amount_due, paid)
classes (student_id, course_code, course_name)
admin (admin_id, name,face_image)
All files are up to date on the GitHub repo:https://github.com/ksloan3/FacialRecognitionProject.git
#10. Troubleshooting

Library Error: Run pip install opencv-contrib-python.
Webcam Issue: Close other apps using the camera.
Recognition Fails: Delete faces/.png and re-sign up
