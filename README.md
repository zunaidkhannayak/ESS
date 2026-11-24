# MOIL ESS – Employee Self-Service (Prototype)

A functional prototype of an Employee Self-Service (ESS) application for **MOIL Limited**. It runs as a single, dependency-free HTML file on mobile and desktop screens.

> **Sample data only.** Every employee, salary slip, leave record, punch and circular in this repository is invented for testing. Nothing here is verified live data from any MOIL system, and no MOIL system is accessed.

## Features

**Employee**
- Login with Employee ID and password, logout, password reset
- Dashboard with My Profile, Salary Slip, Leave, Biometric Attendance, History, Notifications, Orders and Circulars
- Salary slips by financial year and month, with history and PDF (via the browser print dialog)
- Leave balances, applications with optional document, status tracking (Pending, Approved, Rejected), history
- Daily IN/OUT punches, missing punches, late arrivals, early departures, monthly summary, correction requests
- Leave and attendance history with a printable report
- Notifications for slips, leave decisions, balance changes, missing punches and new circulars
- Searchable repository of orders and circulars (Head Office, Mines, Units)

**Reporting officer**
- Approve or reject leave applications of their team

**HR administrator**
- Manage accounts, roles and access
- Upload salary slips, set leave policy and balances
- Review attendance corrections
- Upload circulars and send notifications
- View the activity log of admin actions

## Run it

Open `index.html` in any modern browser. No build step and no installation.

To host it free, enable **GitHub Pages** (Settings → Pages → deploy from the `main` branch, root folder).

## Test accounts

Password for all: `Demo@123`

| ID | Name | Role |
|---|---|---|
| E1001 | Zunaid Khan Nayak | Employee |
| E1002 | Sunita Deshmukh | Reporting officer |
| E1003 | Mohan Lal Yadav | Employee |
| HR01 | Priya Nair | HR administrator |

Password reset uses the sample date of birth, for example E1001 is `1988-03-14`.

## How it is built

- Single file: HTML, CSS and vanilla JavaScript
- Data is kept in the browser's `localStorage` (key `moil_ess_sample_v2`), so each browser has its own private copy
- The admin Activity Log page has a "Reset sample data" button

The script is organised in sections: data layer, UI helpers, authentication, employee views, admin views.

## Integrating with MOIL systems

The data layer at the top of the script (seed data, `D`, `save`, `notify`, `attDay`, `mkSlip`) is the only place that holds data. To go live, replace it with calls to authorised APIs or secure data connections for:

| Module | Source system |
|---|---|
| Profile, leave balances and policy | HRMS |
| Salary slips | Payroll |
| Punch records | Biometric attendance |
| Orders and circulars (PDF) | Document management system |
| Login | Central authentication (for example SSO) |

## Security – read before deploying

This is a front-end prototype. Logins, roles and audit logs run in the browser and **are not real security**. Before any real use, a server must provide:

- Secure authentication with hashed passwords or SSO
- Server-side role-based access control, so employees can only reach their own records
- Encrypted transport (HTTPS) and secure database connections
- Tamper-proof audit logs for administrative actions

Never load real employee data into this prototype.

## Known limitations

- PDF download uses the browser print dialog ("Save as PDF")
- Attachments store only the file name; circulars are text, not uploaded PDFs
- Leave types, entitlements and salary formulas are sample values, not MOIL policy
- Interface is English only

## License

Add a license before sharing publicly.
