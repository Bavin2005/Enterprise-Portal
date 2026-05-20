# Cab Booking Feature

## Overview
Added cab booking functionality to the Transport module. Employees, IT staff, and admins can now book cabs from one location to another.

## Backend

### Model: CabBooking
**File:** `backend/models/CabBooking.js`

**Fields:**
- `user` – Reference to User (who booked)
- `pickupLocation` – String (required)
- `dropLocation` – String (required)
- `pickupDate` – Date (required)
- `pickupTime` – String (e.g., "09:00", required)
- `cabType` – Enum: "Sedan", "SUV", "Hatchback" (default: "Sedan")
- `passengerCount` – Number (1-7, default: 1)
- `purpose` – String (optional, e.g., "Client meeting")
- `status` – Enum: "Pending", "Confirmed", "Completed", "Cancelled" (default: "Pending")
- `driverName` – String (filled by Admin/IT when confirming)
- `driverPhone` – String
- `cabNumber` – String
- `notes` – String (optional)
- `confirmedBy` – Reference to User (Admin/IT who confirmed)
- `confirmedAt` – Date

### Routes
**File:** `backend/routes/transportRoutes.js`

| Endpoint | Method | Access | Purpose |
|----------|--------|--------|---------|
| `/api/transport/book-cab` | POST | All authenticated | Book a cab |
| `/api/transport/my-cab-bookings` | GET | All authenticated | Get user's own bookings |
| `/api/transport/cab-bookings` | GET | Admin/IT only | Get all bookings |
| `/api/transport/cab-bookings/:id` | PATCH | Admin/IT (confirm), User (cancel own) | Update booking status |
| `/api/transport/cab-bookings/:id` | DELETE | Admin/IT or User (own pending) | Delete booking |

**Notifications:**
- When Admin/IT confirms a booking, the user receives a notification with booking details.

## Frontend

### API Client
**File:** `frontend/src/api/transportApi.js`

Functions:
- `bookCab(bookingData)` – Submit cab booking
- `getMyCabBookings()` – Get user's bookings
- `getAllCabBookings()` – Get all bookings (Admin/IT)
- `updateCabBooking(id, updates)` – Update booking
- `deleteCabBooking(id)` – Delete booking

### Transport Page
**File:** `frontend/src/pages/transport/Transport.jsx`

**Features:**
- **Two tabs**: "Shuttle Routes" and "Cab Bookings"
- **Book Cab button** – Opens booking form
- **Booking form:**
  - Pickup location (text)
  - Drop location (text)
  - Pickup date (date picker, min: today)
  - Pickup time (time picker)
  - Cab type (dropdown: Sedan, SUV, Hatchback)
  - Passenger count (1-7)
  - Purpose (optional text)
- **My Bookings / All Bookings:**
  - Shows list of cab bookings
  - Status badge (Pending/Confirmed/Completed/Cancelled)
  - Displays: locations, date/time, cab type, passengers, purpose
  - For confirmed bookings: shows driver name, phone, cab number
  - **Employee actions:** Cancel own pending booking
  - **Admin/IT actions:** Confirm pending bookings (prompts for driver details)

**UI:**
- Pending bookings show count badge on "Cab Bookings" tab
- Color-coded status badges (yellow: Pending, green: Confirmed, blue: Completed, red: Cancelled)
- Toast notifications for success/error

## User Flow

### Employee
1. Go to **Transport** page → **Cab Bookings** tab
2. Click **Book a Cab**
3. Fill in: pickup location, drop location, date, time, cab type, passenger count, purpose
4. Click **Submit Booking** → booking created with status "Pending"
5. View booking in **My Cab Bookings**
6. Wait for Admin/IT to confirm → receives notification when confirmed
7. Can **Cancel** own pending booking

### Admin/IT
1. Go to **Transport** page → **Cab Bookings** tab
2. See **All Cab Bookings** (all users)
3. For pending bookings, click **Confirm**
4. Enter: driver name, driver phone, cab number
5. Booking updated to "Confirmed" → user receives notification
6. Can view all bookings across all statuses

## Chatbot Integration
The Portal Assistant chatbot recognizes "transport", "cab", "taxi", "bus", "route", "pickup" keywords and provides guidance:

> "Transport page offers shuttle routes with pickup points and timings (Mon-Fri), and cab booking for point-to-point travel. Book a cab by specifying pickup/drop locations, date, time, and cab type (Sedan/SUV/Hatchback). Admin/IT will confirm bookings."

## Database
- New collection: `cabbookings`
- Seeding: Not included in `seedAll.js` (cab bookings are user-generated)

---

**Summary:** Cab booking is now fully integrated into the Transport module. Employees can book cabs for company travel, and Admin/IT can manage and confirm bookings.
