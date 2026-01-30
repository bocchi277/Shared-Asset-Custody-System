# 📦 Shared Asset Custody System

> A web-based system to track ownership, transfer history, and availability of shared organizational assets (laptops, cameras, tools, devices, etc.).

This project focuses on the **clarity**, **accountability**, and **auditability** of shared assets, replacing manual spreadsheets with a robust database-backed application.

---

## 📂 Project Structure

```text
DigiProject/
│
├── app.py                # Application entry point
├── config.py             # Configuration settings
├── extensions.py         # DB and Migration extensions
├── seed.py               # Script to populate dummy data
│
├── models/               # Database models (User, Asset, Assignment)
├── services/             # Business logic layer
├── routes/               # API and UI routes
├── templates/            # HTML templates
└── static/               # CSS and assets
```

Setup Instructions (Run Locally)
1. Clone the Repository
#USE THIS CODE
git clone <repo-link>
cd DigiProject

3. Create Virtual Environment
python -m venv venv

3. Install Dependencies
pip install flask flask-sqlalchemy flask-migrate


4. Initialize Database (First Time Only)
flask db init
flask db migrate -m "initial schema"
flask db upgrade

5. Seed Dummy Data
python seed.py

7. Run the Application
flask run

Open in browser:
Available Pages and Page	Description
/	Dashboard with asset list + inventory summary
/assign-page	Assign an asset
/asset/<id>/history	View asset history

-- API Endpoints --
Method	Route	Description
GET	/assets	List all assets
GET	/users	List users
POST	/assign	Assign asset
POST	/return/<id>	Return asset
Design Decisions

Used Assignment table for audit trail instead of storing owner on Asset
Derived state prevents data inconsistency
Fixed N+1 query problem using selectin loading
Added inventory summary as aggregation view
Kept UI simple to focus on system design


What Was Intentionally NOT Built
Notifications
Predictive maintenance
Advanced search/filtering
Authentication

These were excluded to keep focus on custody tracking and accountability.

-- End Note By Author --
Built as part of a Product Engineering assignment focused on system design and real-world modeling of shared resources.
