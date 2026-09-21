# Practical Development Setup Assignment

**Name:** Nancy Tenai
**Date:** September 21, 2026
**Course:** ILO Software Engeenering

---

## Task 1: Flutter & Dart Setup

### 1. Flutter Doctor Output

```

nanci@DESKTOP-2134LHN MINGW64 ~ (main)
$    flutter doctor
Doctor summary (to see all details, run flutter doctor -v):
[√] Flutter (Channel stable, 3.47.5, on Microsoft Windows [Version 10.0.26200.9457], locale en-US)
[√] Windows Version (Windows 11 or higher, 25H2, 2009)
[X] Android toolchain - develop for Android devices
    X Unable to locate Android SDK.
      Install Android Studio from: https://developer.android.com/studio/index.html
      On first launch it will assist you in installing the Android SDK components.
      (or visit https://flutter.dev/to/windows-android-setup for detailed instructions).
      If the Android SDK has been installed to a custom location, please use
      `flutter config --android-sdk` to update to that location.

[√] Chrome - develop for the web
[X] Visual Studio - develop Windows apps
    X Visual Studio not installed; this is necessary to develop Windows apps.
      Download at https://visualstudio.microsoft.com/downloads/.
      Please install the "Desktop development with C++" workload, including all of its default
      components
[√] Connected device (3 available)
[√] Network resources

! Doctor found issues in 2 categories.

```

### 2. Project Initialization

**Commands used:**
```bash
flutter create my_first_app
cd my_first_app
flutter devices
```

**Output:**
```
nanci@DESKTOP-2134LHN MINGW64 ~ (main)
$ flutter create my_first_app
cd my_first_app
flutter devices
Creating project my_first_app...
Resolving dependencies in `my_first_app`... (1.8s)
Downloading packages...
Got dependencies in `my_first_app`.
Wrote 131 files.

All done!
You can find general documentation for Flutter at: https://docs.flutter.dev/
Detailed API documentation is available at: https://api.flutter.dev/
If you prefer video documentation, consider: https://www.youtube.com/c/flutterdev

In order to run your application, type:

  $ cd my_first_app
  $ flutter run

Your application code is in my_first_app\lib\main.dart.

Found 3 connected devices:
  Windows (desktop) • windows • windows-x64    • Microsoft Windows [Version 10.0.26200.9457]
  Chrome (web)      • chrome  • web-javascript • Google Chrome 153.0.8010.48
  Edge (web)        • edge    • web-javascript • Microsoft Edge 153.0.4234.32

Run "flutter emulators" to list and start any available device emulators.

If you expected another device to be detected, please run "flutter doctor" to diagnose potential
issues. You may also try increasing the time to wait for connected devices with the
"--device-timeout" flag. Visit https://flutter.dev/setup/ for troubleshooting tips.

nanci@DESKTOP-2134LHN MINGW64 ~/my_first_app (main)
$

```

### 3. Hot Reload vs Hot Restart

- **Hot Reload:** Updates the code while keeping the app state (like text in forms). Use it for quick UI changes.

- **Hot Restart:** Restarts the app completely, losing all state. Use it when changing global variables or app initialization.

---

## Task 2: MySQL Database Management

### 1. SQL Script

```sql
CREATE DATABASE school;
USE school;

CREATE TABLE students (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(150) UNIQUE NOT NULL,
    enrolled_on DATE
);

INSERT INTO students (name, email, enrolled_on)
VALUES
('Alice Johnson', 'alice@example.com', '2023-09-01'),
('Bob Smith', 'bob@example.com', '2023-09-05');

SELECT * FROM students;
```

### 2. Query Results

![MySQL Output](mysql-output.png)

### 3. Security Reflection

Using `root` for applications is bad because it has full access to everything. If hacked, the attacker can delete all databases.

**Better approach - create a limited user:**
```sql
CREATE USER 'app_user'@'localhost' IDENTIFIED BY 'StrongPassword123!';
GRANT SELECT, INSERT, UPDATE, DELETE ON school.* TO 'app_user'@'localhost';
FLUSH PRIVILEGES;
```

---

## Task 3: Python Virtual Environment

### Commands Used

```bash
mkdir python_setup_lab
cd python_setup_lab
python -m venv venv
venv\Scripts\activate
pip install requests
pip list
pip freeze > requirements.txt
```

---

## Task 4: VS Code Workspace

![VS Code Screenshot](vscode-screenshot.png)

The screenshot shows:
- Extensions panel with Flutter, Dart, Python, Pylance, MySQL
- Terminal with (venv) active
- Python interpreter selected in status bar
