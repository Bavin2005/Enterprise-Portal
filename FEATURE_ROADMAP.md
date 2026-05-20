# Enterprise Portal – Feature Roadmap

## Current Features (Implemented)

- **Announcements** – Admin & IT create; all view. Create via Announcements → Create Announcement (Admin/IT only).
- **Calendar** – Month picker for Indian holidays 2026–2027; events; Admin/IT add events.
- **Cafeteria Status** – Open/closed on dashboards; Mon–Fri 8am–3pm.
- **Tickets, Leaves, Directory, Policies, About, What’s New, Knowledge Base, AI Chat**

---

## Suggested Next Features (Prioritized)

### 1. Meeting Room Booking
- List rooms with capacity and amenities.
- View availability (day/week).
- Book slots; Admin manages rooms.
- Notifications for upcoming bookings.

### 2. Desk/Seat Booking (Hybrid)
- Floor plan or seat grid.
- Reserve desk for specific days.
- Availability by day/week.
- Integration with “work from home” policies.

### 3. Transport / Shuttle Schedule
- Shuttle routes and timings.
- Pickup/drop points.
- Today’s schedule on dashboard.
- Optional seat booking.

### 4. Birthday & Work Anniversary
- Birthday and anniversary list (opt-in).
- Dashboard widget: “Today’s celebrations.”
- Optional greeting cards or reminders.

### 5. Today’s Menu (Cafeteria)
- Admin/IT manage daily menu.
- Show on dashboard with cafeteria status.
- Filters (veg/non-veg, dietary).

### 6. Emergency Contacts & SOS
- HR, Security, Medical, IT.
- Quick dial/shortcuts.
- Office evacuation map.
- Optional incident reporting.

### 7. Visitor Management
- Pre-register visitors.
- Host approval flow.
- Check-in/check-out.
- Visitor badge printing info.

### 8. Parking Management
- Total and available slots.
- Status on dashboard.
- Optional vehicle registration.
- Special slots (EV, accessible).

### 9. Facility Booking (Gym, Sports)
- Gym, courts, etc.
- Slot booking.
- Availability view.
- Rules/policies.

### 10. Office Map / Floor Plan
- Interactive floor map.
- Departments, meeting rooms, cafeteria, exits.
- Search by person/room.
- Visitor navigation.

### 11. Printer/Copier Status
- Printer status (online/offline, paper, toner).
- Location and floor.
- Optional print job history.

### 12. Break Room Status
- Coffee machines, vending.
- Real-time or estimated status.
- Maintenance alerts.

### 13. Quick Links / Shortcuts
- Custom shortcuts per user.
- Admin-defined org-wide links.
- Usage analytics.

### 14. Weather Widget
- Local weather on dashboard.
- Alerts (rain, heat).
- Commute impact.

### 15. Expense & Reimbursement
- Submit expense requests.
- Upload bills.
- Manager approval.
- Status tracking.

### 16. Training & Learning
- Course catalog.
- Enroll and track progress.
- Certifications.
- Recommended learning paths.

### 17. Feedback & Pulse Surveys
- Anonymous surveys.
- Pulse checks.
- Results dashboard for HR.

### 18. Asset Management (IT)
- Laptop, monitor, peripherals.
- Assign/return flows.
- Warranty and maintenance.

---

## Implementation Notes

- Start with **Meeting Room Booking** and **Today’s Menu** for immediate value.
- Use real-time updates (polling or WebSockets) for cafeteria, parking, room status.
- Keep cafeteria timings and menu configurable (Admin settings).
- Add role-based access for each feature.
- Use existing patterns: API routes, models, React components, Tailwind.
