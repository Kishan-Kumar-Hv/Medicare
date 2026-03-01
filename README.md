# MedCareGuardianApp

Premium guardian-patient medication care platform with reminders, escalation workflow, caretaker notification, health news, and Karnataka medical directory.

## Overview

MedCareGuardianApp is a full-stack web app where:
- A **Guardian** creates medicine schedules for a patient.
- A **Patient** sees assigned schedules and marks doses as taken.
- If a dose is missed, the system escalates with SMS/call flow (Twilio-ready).
- Both users get dashboard visibility with logs, charts, and notification history.
- Public health data modules include:
- Hassan pharmacies (open status style display)
- Karnataka district medical directory (pharmacies + hospitals)
- Health news feed (News API + fallback)

## Core Features

- Role-based authentication (`guardian`, `patient`)
- Guardian dashboard:
- Create/delete medication plans
- Assign plans to registered patient accounts
- Adherence metrics and weekly charts
- Notification event panel
- Karnataka directory panel
- Hassan open-now medical panel
- Health news panel
- Patient dashboard:
- View only linked medication plans
- Mark doses as taken
- Trigger escalation manually
- Alarm sound + browser notification toggles
- Due/overdue/escalated status chips
- Backend escalation engine:
- Periodic sweep checks due/missed doses
- Creates log entries (`taken`, `escalated`)
- Sends caretaker/patient SMS notifications (Twilio or mock fallback)
- Optional caretaker call escalation
- Public/home website pages with premium-style landing + login/register

## Tech Stack

- Frontend: React + Vite
- Backend: Node.js (native `http` server)
- Database: SQLite (`node:sqlite`, file-based persistent storage)
- Hosting: Render Web Service
- External APIs:
- Twilio Voice/SMS (optional, real-time provider)
- News API (optional, health headlines)
- Overpass/OpenStreetMap (directory lookups, with fallback)

## Project Structure

```text
MedCareGuardianApp/
├── src/
│   ├── App.jsx                # Main app UI + role portals + dashboard logic
│   ├── api.js                 # Frontend API client wrappers
│   ├── styles.css             # Application styling
│   ├── main.jsx               # React entry point
│   ├── countryCodes.js        # Global phone country code list
│   └── game/logic.js          # Extra logic module (not core flow)
├── server/
│   └── index.js               # Backend API, auth, DB schema, sweeps, Twilio integration
├── dist/                      # Production frontend build output
├── .env.example               # Environment variable template
├── render.yaml                # Render deployment blueprint
├── package.json               # Scripts + dependencies
├── vite.config.js             # Vite dev server + API proxy
├── CLASS_PPT_MEDASSIST.md     # Class explanation notes
└── MedAssist_Class_Presentation.pptx
