# HCM Lite — AI-Assisted Human Capital Management System

> **Saylani Hackathon — 24 October 2026**  
> **Venue**: Zaitoon Ashraf IT Park, Karachi  
> **Evaluation Time**: Designed to be evaluated and verified in **under 10 minutes**.

---

## 🛠️ Tech Stack & Architecture

- **Framework**: Next.js 16 (App Router + React Server Components + Turbopack)
- **Language**: TypeScript 5 (Strict Mode, End-to-End Type Safety)
- **Database ORM**: Prisma 6.4 with zero-dependency SQLite (`file:./dev.db`)
- **Styling**: Tailwind CSS & Lucide Icons (Dark Glassmorphic Enterprise UI)
- **Authentication**: JWT in HTTP-Only Cookies (via `jose`) & `bcryptjs` Password Hashing
- **AI Engine**: Dual-Mode AI Engine (Google Gemini 1.5 Flash API + Intelligent Deterministic Offline Synthesizer)
- **Biometrics & Geolocation**: Canvas Face/Presence Detection + Browser Geolocation + Haversine 150m Office Perimeter Verification

---

## ⚡ Quick Start Guide (Ready in < 2 Minutes)

```bash
# 1. Clone the repository
git clone <repo-url>
cd Hackathon

# 2. Install dependencies
npm install

# 3. Initialize SQLite Database (starts completely clean, 0 users)
npx prisma db push

# 4. Run Development Server (or Production Build: npm run build && npm start)
npm run dev
```

Open your browser at **[http://localhost:3000](http://localhost:3000)**.

---

## ⚙️ Environment Variables Setup (`.env`)

A `.env.example` file is included in the project root:

```env
# Database Connection (Zero-dependency SQLite for immediate local execution)
DATABASE_URL="file:./dev.db"

# JWT Authentication Secret (32+ characters)
JWT_SECRET="saylani-hackathon-2026-hcm-lite-secret-key-32-chars-long"

# Hosted LLM API Key (Optional)
# If provided, Google Gemini 1.5 Flash generates dynamic conversational text.
# If omitted, HCM Lite's built-in intelligent engine handles all tools, Roman Urdu, and formulas offline!
AI_API_KEY=""

# Application Base URL
NEXT_PUBLIC_APP_URL="http://localhost:3000"
```

---

## ⏱️ 5-Minute Live Demo Script for Judges

Follow these 5 exact steps for a flawless 5-minute hackathon evaluation:

### Step 1: Fresh Install & First-Run Wizard (`/setup`)
1. Open `http://localhost:3000`.
2. Because the database starts completely fresh with **Zero Dummy Data**, the system automatically detects that no Admin exists and redirects to `/setup`.
3. Fill in:
   - **Company**: *TechCorp Global*
   - **Office Coordinates**: `24.8607`, `67.0011`, **Radius**: `150m`, **Work Start**: `09:00 AM`, **Grace**: `15 min`.
   - **Admin Account**: Email `admin@techcorp.com`, Password `Admin@12345`.
4. Click **Initialize Enterprise Workspace**.
   - Core departments (*IT, HR, Sales, Finance*) and official leave categories (*Annual 14, Sick 8, Casual 10, Unpaid*) are automatically provisioned.
   - The setup wizard permanently locks (`/setup` returns 403 / redirects).

---

### Step 2: HR Onboarding & Bulk CSV Import (`/admin/hr-management` & `/hr/employees`)
1. In the **Admin Dashboard**, click **HR Logins** (`/admin/hr-management`).
2. Create an HR Account:
   - Email: `hr@techcorp.com`, Temporary Password: `TempHR@12345`.
3. Sign out and log in as `hr@techcorp.com`.
4. Navigate to **Employees Directory** (`/hr/employees`):
   - **Option A (Manual Form)**: Click *Register Employee* to add an employee (*Ali Khan*, Basic Salary: `₨ 100,000`, Gross: `₨ 150,000`).
   - **Option B (Bulk CSV Import)**: Click *Import CSV* and paste or upload CSV lines. The system displays an interactive dry-run table with error validation before committing.
   - Click *Export CSV* to verify instant export.

---

### Step 3: Employee Self-Service, Camera Check-In & Smart Leave
1. Log in with the newly created Employee credentials using their temporary password.
2. **Mandatory First-Login Password Change**: The system detects `mustChangePassword: true` and blocks dashboard access until a new password is set.
3. **Attendance Self-Service** (`/employee/attendance`):
   - **Camera Face Check-In (+10 Bonus Points)**:
     - Click **Camera Check-In (+10 Pts Bonus)**.
     - Live camera preview displays face target crosshairs and real-time detection badge.
     - Click *Simulate Face In/Out* or use real webcam to test both validation states.
     - GPS coords are captured and verified against the 150m Haversine perimeter.
     - Click *Verify & Punch Attendance* -> Marks check-in stamped by server timestamp.
4. **Smart Leave Application** (`/employee/leave`):
   - Click *Apply for Leave*.
   - In the **Smart Apply with AI** input box, type natural language or Roman Urdu:
     - *"Need next Monday and Tuesday off for sister's wedding"* OR *"Kal bukhar ki wajah se chutti chahiye"*.
   - Click **Auto-Fill**: AI parses dates, matches the leave type (*CASUAL* / *SICK*), and populates the form automatically!
   - Submit request -> System validates that Sat-Sun weekends & holidays are excluded from deduction.

---

### Step 4: Payroll Run & Permanent Admin Lock (`/hr/payroll` & `/admin/payroll`)
1. Log in as **HR** (`hr@techcorp.com`) and open **Payroll Engine** (`/hr/payroll`).
2. Click **Generate Draft Payroll** for the current month:
   - System calculates working days, per-day rates, attendance deductions (including late penalties: 3 lates = 0.5 day deduction), and tax slabs (0% to 35%).
   - Status is marked **DRAFT**.
3. Log in as **Admin** (`admin@techcorp.com`) and open **Finalize Payroll** (`/admin/payroll`).
4. Click **Finalize & Lock Payroll**:
   - Status changes to **FINALIZED**.
   - Record is permanently locked. Any subsequent edit attempts return **403 Forbidden / 422 Unprocessable Entity**.
5. Switch to Employee account to view personal printable **Payslip** (`/employee/payslips`).

---

### Step 5: AI Privacy Guardrail, Roman Urdu & Audit Logs
1. Open the floating **AI Assistant** (bottom-right sparkles icon on any screen).
2. **Test Critical Privacy Guardrail (Section 3 Rule)**:
   - As an Employee, ask: *"What is Ali's salary?"* or *"Tell me Sarah's pay"*.
   - **Result**: AI strictly refuses:
     > *"Access Denied: You do not have permission to view other employees' salary details. [AI-generated]"*
3. **Test Roman Urdu Understanding (+10 Bonus Points)**:
   - Ask: *"Aaj kitne log chutti par hain?"* -> Returns real-time database leave summary.
   - Ask: *"Der se aane wale employees ki list dikhao"* -> Returns top late comers this month.
4. **Test Executive AI Dashboard Summary**:
   - On Admin or HR dashboard, click **Generate AI Summary** -> AI distills current KPI numbers into 3–5 actionable bullet insights.
5. **Review Immutable Audit Logs** (`/admin/audit-logs`):
   - View complete security trail with before/after state diffing for all setup, attendance, payroll, and user actions.

---

## 🎯 Completed 25 Functionalities Checklist (M1 – M9)

| # | Module | Functionality / Business Rule | Status |
| :---: | :--- | :--- | :---: |
| 1 | **M1: Auth & Setup** | First-Run setup check: Redirect to `/setup` if no admin exists | ✅ Verified |
| 2 | **M1: Auth & Setup** | First-Run wizard permanent lock after initial admin initialization | ✅ Verified |
| 3 | **M1: Auth & Setup** | Temporary password generation & mandatory first-login password change | ✅ Verified |
| 4 | **M1: Auth & Setup** | Server-side role guard middleware (`ADMIN`, `HR`, `EMPLOYEE` scoping) | ✅ Verified |
| 5 | **M2: Org Setup** | Organization settings: Geofence radius, office start time & grace minutes | ✅ Verified |
| 6 | **M2: Org Setup** | Department CRUD, Designations, and Public Holidays calendar setup | ✅ Verified |
| 7 | **M3: Employee Mgmt** | Admin HR account management with temporary passwords | ✅ Verified |
| 8 | **M3: Employee Mgmt** | HR manual employee registration form with full profile fields | ✅ Verified |
| 9 | **M3: Employee Mgmt** | Bulk CSV Import with dry-run error diagnostics report & CSV Export | ✅ Verified |
| 10 | **M4: Attendance** | Server-stamped attendance timing (client clocks bypassed) | ✅ Verified |
| 11 | **M4: Attendance** | 1 check-in per employee per day enforcement (duplicate = 409 Conflict) | ✅ Verified |
| 12 | **M4: Attendance** | Late arrival cutoff (after 09:15 AM = LATE) & Half-Day rule (< 5.0h) | ✅ Verified |
| 13 | **M4: Attendance** | Attendance correction request submission & HR Approval Inbox | ✅ Verified |
| 14 | **M4: Attendance** | **Bonus (+10 Pts)**: Camera Check-In with face detection & 150m Haversine GPS | ✅ Verified |
| 15 | **M5: Leave Mgmt** | Quotas: Annual = 14, Sick = 8, Casual = 10, Unpaid = Unlimited | ✅ Verified |
| 16 | **M5: Leave Mgmt** | Working days deduction skipping official weekends (Sat-Sun) & holidays | ✅ Verified |
| 17 | **M5: Leave Mgmt** | Overlap check & balance exhaustion check returning 422 Unprocessable | ✅ Verified |
| 18 | **M5: Leave Mgmt** | Employee self-service apply modal & HR Review/Approval Inbox | ✅ Verified |
| 19 | **M6: Payroll Lite** | Salary formula: Gross = 1.5 × Basic (Basic 100%, HRA 40%, Medical 10%) | ✅ Verified |
| 20 | **M6: Payroll Lite** | Per-day rate, late penalty (3 lates = 0.5 day deduction), tax slabs (0%–35%) | ✅ Verified |
| 21 | **M6: Payroll Lite** | HR drafts payroll (`DRAFT`) & Admin locks payroll permanently (`FINALIZED`) | ✅ Verified |
| 22 | **M6: Payroll Lite** | Printable personal payslips with employee ownership security check | ✅ Verified |
| 23 | **M7: Analytics** | Pure server-side formula calculations (Attendance %, Late %, Absenteeism) | ✅ Verified |
| 24 | **M8: AI Assistant** | Role-scoped tools, salary privacy guardrail, Smart Leave, and **Roman Urdu (+10 Pts)** | ✅ Verified |
| 25 | **M9: Comms & Audit** | Company announcement broadcasts, in-app notifications, & JSON audit diffs | ✅ Verified |

---

## 🧮 Section 3 & 7 Mathematical Formulae

| Calculation | Formula |
| :--- | :--- |
| **Gross Salary** | $\text{Gross} = 1.5 \times \text{Basic}$ |
| **Per Day Rate** | $\text{Per Day Rate} = \text{Gross} \div \text{Total Working Days in Month}$ |
| **Monthly Deductions** | $(\text{Absent} + \text{Unpaid} + 0.5 \times \text{HalfDay} + \text{LatePenalty}) \times \text{Per Day Rate}$ |
| **Late Penalty** | Every 3 late arrivals = $0.5 \times \text{Per Day Rate}$ deduction |
| **Tax Slabs (Annual)** | 0–600k (0%), 600k–1.2M (5%), 1.2M–2.4M (₨ 30k + 15%), 2.4M–3.6M (₨ 210k + 25%), > 3.6M (₨ 510k + 35%) |
| **Attendance Rate** | $\frac{\text{Present} + \text{Late} + \text{Missing Checkout} + 0.5 \times \text{Half Day}}{\text{Total Active} - \text{On Leave}} \times 100\%$ |
| **Late Arrival %** | $\frac{\text{Late}}{\text{Present} + \text{Late}} \times 100\%$ |
| **Absenteeism %** | $\frac{\text{Absent Days}}{\text{Expected Working Days}} \times 100\%$ (department-wise) |

---

## 🛡️ Security & Privacy Guardrails

1. **Colleague Salary Privacy**: When role `EMPLOYEE` asks about any other employee's salary, the AI Assistant immediately triggers a hard stop: *"Access Denied: You do not have permission to view other employees' salary details."*
2. **Zero Pre-Loaded Data**: Database starts 100% empty (`User count: 0`), requiring the judge to experience the setup wizard and test real workflows.
3. **Immutable Audit Logs**: Every administrative and security action records actor ID, role, action, IP address, and before/after JSON diffs.
4. **Server Timestamp Enforcement**: Client device clocks can never spoof attendance or payroll calculation times.

---

*Saylani Hackathon 2026 — HCM Lite is fully verified with 0 errors on Next.js 16 production build.*
