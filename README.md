# 🏫 SOS — School of Skills

<p align="center">
  <img src="logo.png" alt="SOS — School of Skills" width="240">
</p>

<h3 align="center">Enterprise Academic Governance & Vocational Management System</h3>

<p align="center">
  A modern educational management dashboard for vocational academies, technology skill hubs, and training institutes.
</p>

<p align="center">
  <a href="https://www.python.org/">
    <img src="https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white" alt="Python">
  </a>
  <a href="https://streamlit.io/">
    <img src="https://img.shields.io/badge/Streamlit-1.30%2B-FF4B4B?logo=streamlit&logoColor=white" alt="Streamlit">
  </a>
  <a href="https://pandas.pydata.org/">
    <img src="https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white" alt="Pandas">
  </a>
  <img src="https://img.shields.io/badge/Architecture-Clean%20OOP-success" alt="Architecture">
  <img src="https://img.shields.io/badge/UI-Red%20%26%20White-DC2626" alt="UI Theme">
</p>

---

## 📌 Overview

**SOS — School of Skills** is an educational management web application designed to centralize the academic and operational workflows of a vocational training institute.

The system brings together:

- Student admissions and learner records
- Academic programs and batches
- Faculty and staff management
- Student and staff attendance
- Fee collection and payment history
- Digital payment receipts
- Campus announcements
- Financial and academic analytics
- Recycle-bin based soft deletion

The application follows a **Separation of Concerns (SoC)** architecture. The Streamlit interface is handled by `app.py`, while the core school entities, business rules, validation, and operations are implemented separately in `sos.py`.

---

## ✨ Core Features

### 📊 1. Centralized Dashboard

The home dashboard provides a high-level view of the institution's current operational data.

**Includes:**

- Branded SOS application header
- `2026 SESSION LIVE` status indicator
- KPI cards for:
  - Total enrolled students
  - Faculty & staff
  - Active programs
  - Fees collected
- Active program cards
- Campus notice board
- Event, urgent, general, and exam notice categories

---

### 🎓 2. Academic Programs & Curriculum

Manage the institute's academic programs from a centralized program catalog.

**Program information includes:**

- Program ID
- Program name
- Category / department
- Duration
- Course fees
- Assigned teacher / mentor
- Current enrollment count

### Current Programs

| Program | Duration | Fee | Mentor |
|---|---:|---:|---|
| **DSA — Data Scientist And Analyst** | 6 months | ₹70,000 | Vyshak |
| **HR — Human Resource** | 4 months | ₹50,000 | Diya |
| **FAD — Fashion Design** | 6 months | ₹80,000 | Shahma C.P |
| **AI — Agent K** | 6 months | ₹80,000 | Rinshin |
| **Spoken English** | 3 months | ₹25,000 | Ashraf |

> Program information above reflects the current project data documented in the original project README.

---

### 👥 3. Faculty & Operations Directory

The staff management module supports multiple operational roles:

- Teachers
- Student Coordinators
- Media Team
- Accountants

**Capabilities include:**

- Staff registration
- Staff search
- Role-based staff classification
- Department information
- Contact information
- Joining-date tracking
- Staff attendance
- Staff detail inspection
- Soft deletion and restoration

**Current staff data includes:**

`Vyshak · Shahma C.P · Rinshin · Ashraf · Diya · Soniya · Rahul Nair · Fathima K · Suresh Babu`

---

### 👨‍🎓 4. Student Admissions & Management

The student module provides a centralized learner registry.

**Features:**

- Student registration
- Student profile management
- Program enrollment
- Batch assignment
- Student search
- Active / Not Enrolled status
- Contact information
- Academic information
- Attendance history
- Fee ledger
- Payment history

Students can be filtered by:

- Program
- Batch / cohort
- Enrollment status

---

### 📅 5. Attendance Management

The attendance hub is designed for quick daily attendance operations.

#### Class Attendance

- Select a program
- Select a batch
- Load the class roster
- Mark students present or absent
- Save attendance records

#### Individual Attendance

Attendance can also be recorded for individual students and staff.

#### Attendance Analytics

The system calculates:

- Total attendance records
- Present days
- Absent days
- Attendance percentage

The application also uses attendance indicators to identify students at or above and below the documented **75%** threshold.

---

### 💳 6. Fee Management & Digital Receipts

The fee module tracks student tuition and payment activity.

**Features:**

- Total contracted course fee
- Amount paid
- Outstanding balance
- Payment history
- Payment status
- Payment validation
- Multiple payment methods

Supported payment modes include:

- `UPI / GPay`
- `Cash`
- `Net Banking`
- `Debit / Credit Card`

### 🧾 Digital Receipts

The application can generate invoice-style digital payment receipts containing:

- Unique receipt ID
- Transaction timestamp
- Student information
- Payment amount
- Payment method
- Remaining balance

Example receipt ID format:

```text
REC-2026-XXXX
```

---

### 📈 7. Analytics & Visual Insights

The analytics section provides visual summaries of academic and financial data.

**Includes:**

#### Financial Realization
- Collected fees
- Pending dues
- Program-wise fee comparison

#### Attendance Comparison
- Average attendance
- Batch/section comparison

#### Curriculum Density
- Student enrollment distribution
- Program-wise student density

---

### ♻️ 8. Recycle Bin & Soft Deletion

Important records are not immediately destroyed when removed.

The system uses a **soft-delete** workflow:

```text
Active Record
     │
     ▼
Move to Recycle Bin
     │
     ├── Restore
     │
     └── Delete Permanently
```

Supported entities include:

- Students
- Staff
- Programs

This allows accidental removals to be restored before permanent deletion.

---

# 🏗️ System Architecture

The application is divided into two primary layers.

```text
┌─────────────────────────────────────────────────────────────┐
│                    STREAMLIT WEB UI                         │
│                         app.py                              │
│                                                             │
│  • Dashboard                                                │
│  • Navigation                                               │
│  • Forms                                                    │
│  • Tables                                                   │
│  • Charts                                                   │
│  • Digital receipts                                         │
│  • Custom CSS / branding                                    │
│  • User interaction & session state                         │
└──────────────────────────────┬──────────────────────────────┘
                               │
                               │ Uses domain models
                               ▼
┌─────────────────────────────────────────────────────────────┐
│                  OOP BUSINESS DOMAIN LAYER                  │
│                         sos.py                              │
│                                                             │
│  • SOS                                                       │
│  • Staff                                                    │
│  • Teacher                                                  │
│  • StudentCoordinator                                       │
│  • MediaTeam                                                │
│  • Accountant                                               │
│  • Program                                                  │
│  • Student                                                  │
│  • Notice                                                   │
│  • SOSActivities                                            │
│  • Validation & business rules                              │
└─────────────────────────────────────────────────────────────┘
```

### Design Principle

`app.py` is responsible for the presentation and interaction layer, while `sos.py` contains the school's business/domain logic. This keeps the core models independent from Streamlit.

---

# 🧠 Object-Oriented Design

The project demonstrates practical Python OOP concepts.

### Base Class

```python
class SOS(ABC):
    ...
```

The base `SOS` class stores common school-level information.

### Staff Hierarchy

```text
SOS
 │
 └── Staff
      ├── Teacher
      ├── StudentCoordinator
      ├── MediaTeam
      └── Accountant
```

### Domain Entities

```text
SOS
├── Staff
├── Program
├── Student
├── Notice
└── SOSActivities
```

The project makes use of:

- Classes and objects
- Inheritance
- Encapsulation
- Class variables
- Instance variables
- Class methods
- Instance methods
- Private attributes
- Validation logic
- Soft deletion
- Attendance calculations
- Fee calculations

---

# 🎨 Design System & Brand Identity

The application follows the official **SOS Red & White** visual direction.

### Brand Colors

| Element | Color |
|---|---|
| Primary Crimson | `#DC2626` |
| Dark Crimson | `#B91C1C` |
| Ruby Red | `#E11D48` |
| Pure White | `#FFFFFF` |
| Deep Crimson Slate | `#170707` |

### UI Characteristics

- Modern SaaS-style dashboard
- Dark crimson sidebar
- Red navigation states
- Custom circular navigation indicators
- Gradient action buttons
- Floating KPI cards
- Rounded containers
- Status badges
- Responsive wide layout
- Plus Jakarta Sans typography
- Material Symbols icon support

---

# 📁 Repository Structure

```text
SOS-School-of-Skills/
│
├── .streamlit/
│   └── config.toml
│
├── app.py
│   └── Streamlit UI, routing, styling and interaction
│
├── sos.py
│   └── OOP domain models and business logic
│
├── logo.png
│   └── Official SOS logo
│
├── requirements.txt
│   └── Python dependencies
│
├── DOCUMENTATION.md
│   └── Extended technical documentation
│
└── README.md
    └── Project documentation
```

---

# 🛠️ Technology Stack

| Technology | Role |
|---|---|
| **Python 3.10+** | Core programming language |
| **Streamlit** | Web application and dashboard |
| **Pandas** | Data analysis and tabular data |
| **Python OOP** | Domain and business logic |
| **HTML/CSS** | Custom UI styling |
| **Git** | Version control |
| **GitHub** | Repository and collaboration |

The current project dependency file contains:

```text
streamlit
pandas
```

---

# 🚀 Getting Started

## Prerequisites

Make sure you have:

- Python **3.10 or newer**
- `pip`
- Git

---

## 1. Clone the Repository

```bash
git clone https://github.com/<your-username>/<your-repository>.git
cd <your-repository>
```

---

## 2. Create a Virtual Environment

### Windows PowerShell

```powershell
python -m venv venv
.\venv\Scripts\Activate.ps1
```

### macOS / Linux

```bash
python3 -m venv venv
source venv/bin/activate
```

---

## 3. Install Dependencies

```bash
pip install -r requirements.txt
```

---

## 4. Verify the Python Files

```bash
python -m py_compile app.py sos.py
```

If there is no output, the Python files passed the compilation check.

---

## 5. Run the Application

```bash
streamlit run app.py
```

The application will normally be available at:

```text
http://localhost:8501
```

---

# 🔄 Application Flow

```text
                    ┌──────────────┐
                    │    Admin     │
                    └──────┬───────┘
                           │
                           ▼
                  ┌─────────────────┐
                  │ Streamlit UI    │
                  │    app.py       │
                  └────────┬────────┘
                           │
          ┌────────────────┼────────────────┐
          ▼                ▼                ▼
     Students          Programs          Staff
          │                │                │
          └────────────────┼────────────────┘
                           ▼
                    Attendance & Fees
                           │
                           ▼
                       Analytics
                           │
                           ▼
                  Dashboard Insights
```

---

# 💾 Data Model

The current application uses Python objects and in-memory state for its core data model.

This makes the project suitable for:

- Academic demonstration
- Prototype development
- OOP learning
- Internal workflow demonstration
- Streamlit experimentation

### Production Expansion

A future production implementation could replace the in-memory state with a persistent database such as:

- PostgreSQL
- MySQL

while keeping the presentation and domain layers conceptually separated.

---

# 📖 Code Transparency

The project code is intentionally heavily documented.

`app.py` contains detailed comments explaining:

1. **What** each major instruction does
2. **Why** it is used
3. **How** it affects application state

This makes the project easier to:

- Learn from
- Review
- Debug
- Maintain
- Extend
- Explain during academic/project presentations

---

# 🔒 Validation & Business Rules

The application includes validation-oriented workflows such as:

- Preventing invalid fee values
- Preventing fee overpayment
- Attendance date validation
- Duplicate attendance-date prevention
- Enrollment status handling
- Soft-delete and restoration workflows
- Program enrollment tracking

---

# 📊 Current Application Modules

The Streamlit navigation includes:

```text
🏠 Home
🏫 School Details
👥 Staff
🎓 Programs
👨‍🎓 Students
✅ Attendance
💰 Fees
📊 Analytics
```

These modules provide the main operational interface for the management system.

---

# 🔮 Future Roadmap

The current architecture can be extended into a larger production-ready platform.

### Phase 1 — Data Persistence
- [ ] PostgreSQL / MySQL integration
- [ ] Database migrations
- [ ] Persistent attendance records
- [ ] Persistent fee transactions
- [ ] Automated backups

### Phase 2 — Authentication
- [ ] Admin authentication
- [ ] Staff accounts
- [ ] Role-based permissions
- [ ] Secure password management
- [ ] Session management

### Phase 3 — Student Portal
- [ ] Student login
- [ ] Personal dashboard
- [ ] Attendance history
- [ ] Fee status
- [ ] Announcements
- [ ] Course information

### Phase 4 — Communication
- [ ] Email notifications
- [ ] WhatsApp notifications
- [ ] Fee reminders
- [ ] Attendance alerts
- [ ] Announcement broadcasts

### Phase 5 — Documents
- [ ] Student ID card generation
- [ ] Certificate generation
- [ ] PDF receipts
- [ ] Attendance reports
- [ ] Excel exports

### Phase 6 — Platform Expansion
- [ ] REST API
- [ ] Mobile application
- [ ] Cloud deployment
- [ ] Advanced reporting
- [ ] Audit logs
- [ ] Automated database backups

---

# 🎯 Project Goals

The project aims to demonstrate how a traditional educational administration workflow can be converted into a centralized digital management platform.

The major goals are:

- Reduce manual administrative work
- Centralize student and staff information
- Simplify attendance management
- Track fees and outstanding balances
- Provide useful academic and financial insights
- Maintain a clean and understandable Python architecture
- Provide a modern interface for day-to-day operations

---

# 🏫 About SOS — School of Skills

**School of Skills (SOS)** is represented in this project as a skill-development and vocational training institution.

The application is designed around the operational needs of an institute offering multiple professional and technical programs.

**Location:** Calicut, Kerala  
**Application:** SOS Management System  
**Session:** 2026

---

# 👨‍💻 Development

Built with:

```text
Python
   +
Object-Oriented Programming
   +
Streamlit
   +
Pandas
   +
HTML/CSS
   =
SOS Management System
```

---

# 📄 License & Attribution

This project is developed for **School of Skills (SOS), Calicut Campus**.

The original project documentation identifies the project as licensed under the **MIT License**. If this repository is intended for public distribution, make sure a corresponding `LICENSE` file is included in the repository.

---

<p align="center">
  <img src="logo.png" alt="SOS Logo" width="120">
</p>

<p align="center">
  <strong>SOS — School of Skills</strong><br>
  <sub>Learn • Build • Grow</sub>
</p>
