# AHA SYSTEM - Employee Activity Tracker System

 **This System** is a real-time AI-powered monitoring solution developed in **Python** using **OpenCV**, **MediaPipe**, and **face_recognition**. It is designed for **corporate environments**, **academic institutions**, or **R&D labs** where employee or student behavior, presence, and engagement need to be tracked efficiently.

---

##  Overview

This system uses **live camera feeds** to:
- Recognize **human activities**
- Detect **authorized/unauthorized faces**
- Monitor **attendance**
- Trigger **real-time alerts**
- Generate **weekly performance reports**

It comes with a sleek **Tkinter GUI**, a role-based login system, and a robust **dashboard** for analytics.

---

##  How It Works

### ✅ Authorized Person Detected:
- Face is matched against known faces in the `images/` directory (under `ACADEMIC/`)
- If matched:
  - Attendance is marked with name, date, and time
  - The system starts analyzing their **activities**:
    - 🧍 Standing
    - 🪑 Sitting
    - 😴 Sleeping (with 3-second threshold detection)
    - 📱 Using Phone
    - 🙆 Hands Up
    - 🤐 Head Down
  - All activities are logged with **duration** and **date**
  - Alerts are raised if:
    - Person is **absent from frame**:
      - 1st time: Normal alert
      - 2nd time: Warning
      - 3rd time: Final Warning + Timer shown
    - Person is sleeping beyond threshold
    - Phone is being used excessively

### ❌ Unauthorized Person Detected:
- If the detected face is **not recognized**:
  - A large **"INTRUSION WARNING"** is displayed
  - An entry is logged in `Unauthorized_Log.csv` with:
    - Time
    - Date
    - Frame captured (optional)
  - This prevents access to attendance and analytics

##  Weekly Report (Automated)

A **weekly PDF report** is generated showing:
- Total activities performed (by category)
- Attendance summaries (present/absent days)
- Average durations of each activity
- Intrusion attempts
- Graphs and visual charts

Reports are saved with filenames like: `AHA_Weekly_Report_YYYY-MM-DD.pdf`


##  Dashboard Features

Accessible via **Main Menu > Analytics Dashboard**, you get:

-  **Activity Distribution Pie Chart**
-  **Accuracy Over Time Graph**
-  **Real-Time & Cumulative Accuracy Bar Charts**
-  **Confusion Matrix Heatmap**
-  **Activity Table**: With filters by Date, Duration, and Activity

All data is sourced from `activity_data.csv`, which is updated live.

## Security

- Admin login required (`admin/password`)
- "Remember Me" login option with local cache
- "Forgot Password" simulated email popup (can be extended with SMTP)
- Unauthorized access triggers logs and alerts

## GUI Navigation

- `welcome_page.py` → Welcome screen
- `login_page.py` → Admin login
- `main_menu.py` → Central menu to start modules
- `dashboard.py` → Dashboard and analytics
- `attendance.py` → Face-based attendance and intrusion detection
- `recognition_mode.py` → Activity detection engine
- `report_generator.py` → Weekly PDF reports

## Real-Time Logging & Detection

- Logs **every second** of activity (durations)
- Detects **total people** in camera view
- Auto-records **alerts** when:
  - Sleeping
  - Absent
  - Phone usage
  - Unauthorized entry

All logs are saved in:
- `activity_data.csv`
- `Unauthorized_Log.csv`

## Tech Stack

- Python 3.11+
- MediaPipe (pose, face mesh)
- OpenCV
- face_recognition
- Tkinter (GUI)
- pandas, seaborn, matplotlib
- fpdf (for PDF report)


## Run this project with run.py

