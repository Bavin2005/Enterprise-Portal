# Enterprise Portal – Current Summary

## Overview
A role-based internal enterprise portal for Employees, IT, and Admins. Built with React + Vite, Tailwind CSS, Node.js/Express, MongoDB.

---

## Features Currently Included

### 1. Authentication & Authorization
- **Login** – Email/password, JWT-based
- **Register** – Name, email, password, role, department
- **Protected routes** – Role-based access (Employee, IT, Admin)
- **AuthContext** – Token, user, login, logout, register
- **Redirects** – Role-based redirect after login (Employee→/, IT→/it, Admin→/admin)

### 2. Ticketing System
- **Create ticket** – Title, description, category (Network/Software/Hardware/Other), priority (Low/Medium/High)
- **My Tickets** – Employee sees own tickets
- **Ticket detail** – Full view with status, SLA, assigned user
- **Admin** – Assign tickets to IT staff
- **IT** – Update ticket status (Open, Assigned, In Progress, Resolved, Closed)
- **SLA** – Auto-calculated deadline by priority; SLA breached flag

### 3. Leave Management
- **Apply leave** – Annual, Sick, Personal, Unpaid
- **My Leaves** – Balance (Annual/Sick/Personal) + history
- **Leave Approvals** – Admin/IT approve or reject with optional reason

### 4. Announcements
- **List** – Company-wide (or by department)
- **Create** – Admin/IT; optional pin to top
- **Pinned** – Shown first

### 5. Employee Directory
- **Search** – By name or email
- **Filter** – By department
- **Card view** – Name, email, department, role

### 6. Calendar & Events
- **List** – Upcoming or this month
- **Add event** – Admin/IT: title, type (Meeting/Holiday/Team Event/Training), dates, location
- **Types** – Meeting, Holiday, Team Event, Training, Other

### 7. Policies & Documents
- **List** – Filter by category (HR, IT, Finance, Security, General)
- **Detail** – Full policy content
- **Add policy** – Admin/IT: title, category, content

### 8. About the Company
- **View** – Mission, vision, values, founded, address, phone, email
- **Edit** – Admin can edit inline (CompanyInfo key-value store)

### 9. What’s New (Upcoming)
- **List** – Features, updates, maintenance
- **Add** – Admin/IT: title, category, target date, status
- **Status** – Planned, In Progress, Done, Cancelled (Admin/IT can update)

### 10. Knowledge Base
- **Articles** – List all
- **Add article** – Admin/IT: title, category, keywords, solution
- **Suggest** – AI-enhanced suggestions (rule-based fallback or OpenAI)

### 11. AI Chatbot
- **Floating widget** – Bottom-right
- **Chat** – Uses OpenAI when `OPENAI_API_KEY` is set; otherwise built-in fallback
- **Context** – Portal features (tickets, leave, announcements, etc.)

### 12. Navigation & UX
- **Breadcrumbs** – Above main content
- **Command palette** – Ctrl/Cmd+K for search/navigation
- **Sidebar** – Role-specific nav; collapsible; mobile drawer
- **Dark mode** – Toggle; persists in localStorage
- **Page transitions** – Framer Motion (fade + slide)

---

## Tech Stack

| Layer     | Tech                          |
|----------|-------------------------------|
| Frontend | React 18, Vite, Tailwind CSS  |
| State    | AuthContext, ThemeContext     |
| Routing  | React Router v7               |
| API      | Axios + JWT interceptors      |
| Backend  | Node.js, Express              |
| Database | MongoDB, Mongoose             |
| Auth     | JWT, bcrypt                   |

---

## Role Permissions

| Feature        | Employee | IT   | Admin |
|----------------|----------|------|-------|
| Dashboard      | ✅       | ✅   | ✅    |
| Create Ticket  | ✅       | ❌   | ❌    |
| My Tickets     | ✅       | ❌   | ❌    |
| Assign Ticket  | ❌       | ❌   | ✅    |
| Update Status  | ❌       | ✅   | ✅    |
| My Leaves      | ✅       | ❌   | ❌    |
| Leave Approvals| ❌       | ✅   | ✅    |
| Add Announcement | ❌     | ✅   | ✅    |
| Add Event      | ❌       | ✅   | ✅    |
| Add Policy     | ❌       | ✅   | ✅    |
| Edit About     | ❌       | ❌   | ✅    |
| Add Upcoming   | ❌       | ✅   | ✅    |
| Add KB Article | ❌       | ✅   | ✅    |
| Directory      | ✅       | ✅   | ✅    |
| Calendar       | ✅       | ✅   | ✅    |
| Policies       | ✅       | ✅   | ✅    |
| About          | ✅       | ✅   | ✅    |
| What’s New     | ✅       | ✅   | ✅    |
| Knowledge Base | ✅       | ✅   | ✅    |
| AI Chat        | ✅       | ✅   | ✅    |

---

## UI Updates (Latest)
- **Color palette** – Teal primary (#0d9488), enterprise grays
- **Page transitions** – Framer Motion (fade + slide)
- **Cards** – Shadow and hover states
- **Sidebar / Topbar** – Enterprise styling and dark mode

---

## Potential Additions (Ideas)

1. **Notifications** – In-app notifications, backend already has `/api/notifications`
2. **Expense management** – Submit, approve, track expenses
3. **Time/Attendance** – Check-in/out, timesheets
4. **Asset management** – Laptops, monitors; assign/track
5. **Goals & performance** – OKRs, KPIs, 1:1 notes
6. **Surveys & feedback** – Pulse surveys, feedback forms
7. **Document upload** – Policy PDFs, attachments
8. **Birthday/anniversary** – Birthday and work anniversary reminders
9. **Org chart** – Visual org structure
10. **Advanced search** – Full-text search across tickets, KB, policies
11. **Audit log viewer** – Admin view of audit logs
12. **Profile/Settings** – Edit profile, change password
13. **SSO / OAuth** – Google, Microsoft login
14. **Mobile app** – React Native or PWA
15. **Email notifications** – Leave approval, ticket updates
