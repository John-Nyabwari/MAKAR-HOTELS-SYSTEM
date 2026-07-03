# MAKAR HOTELS SYSTEM

A comprehensive hotel management and guest portal system for Makar Hotel in Nairobi, featuring luxury accommodations, virtual waiter dining, and an admin management console.

## 🎯 What This Is

MAKAR HOTELS SYSTEM is a modern, integrated platform serving luxury hotel guests and staff at Makar Hotel in Westlands, Nairobi. It provides:

- **Guest Portal** — Seamless booking, room browsing, virtual waiter dining, reviews, and contact management
- **Admin Console** — Complete operational dashboard for bookings, F&B orders, front desk, housekeeping, HR, accounting, and inventory management
- **Real-time Database** — Live synchronization between guest interactions and staff dashboards powered by Supabase

Designed for upscale hospitality with a focus on elegance, efficiency, and guest experience.

## 📋 Stack

- **Language(s):** HTML, CSS, TypeScript, JavaScript
- **Framework/Runtime:** Vanilla HTML + Tailwind CSS, Supabase (backend/database), Chart.js (analytics)
- **Notable Libraries:**
  - **Supabase JS SDK** — Real-time PostgreSQL database, instant data sync
  - **Tailwind CSS** — Utility-first responsive design
  - **Font Awesome 6.4** — Icon system
  - **Chart.js** — Dashboard analytics & revenue charts
  - **Google Fonts** — Playfair Display & DM Sans typography

## 📁 How It's Organized

```
MAKAR-HOTELS-SYSTEM/
├── index.html              Guest-facing portal (hero, rooms, dining, bookings, reviews)
├── admin/
│   └── index.html          Staff/admin management console
├── src/
│   └── supabaseClient.js   Database client config (Supabase credentials)
├── my-project/             Vite project scaffold (optional)
└── README.md               This file
```

### How It Fits Together

1. **Guest Portal** (`index.html`) — Landing page with navigation, room showcase, menu with virtual waiter, booking form, reviews, and contact
   - Guests browse rooms → select dates → fill booking form → place F&B orders → submit reviews
   - All data flows to Supabase tables: `bookings`, `orders`, `reviews`, `contact_messages`

2. **Admin Console** (`admin/index.html`) — Staff dashboard with role-based views
   - **Dashboard** — KPIs (bookings, revenue, orders, reviews) + activity feed
   - **Bookings** — Manage guest reservations, filter by status, view details
   - **Front Desk** — Room occupancy overview, today's arrivals, check-out management
   - **F&B Orders** — Virtual waiter order tracking with status transitions (pending → preparing → served)
   - **Reviews** — Guest feedback moderation
   - **Messages** — Contact form submissions
   - **Housekeeping** — Task cards with priority and staff assignment
   - **HR & Staff** — Team directory, payroll summary
   - **Inventory & Suppliers** — Stock levels, supplier contacts, invoices
   - **Accountant** — Invoice approvals, payroll processing
   - **Reports** — Charts, occupancy analysis, revenue breakdown

3. **Database** (Supabase) — Shared PostgreSQL tables
   - `bookings`, `orders`, `reviews`, `contact_messages`, `invoices` (live-synced in real-time)

## 🚀 How to Run It

### Guest Portal
```bash
# Simply open in a browser
open index.html

# Or serve locally
python -m http.server 8000
# Visit http://localhost:8000
```

### Admin Console
```bash
# Open in a browser
open admin/index.html

# Login with demo credentials:
# Email: admin@makarhotels.com
# Password: admin
```

### Environment Setup
No build step required — all code is vanilla HTML/CSS/JS. However, ensure:

1. **Supabase Project is Active** — The console uses Supabase credentials embedded in `index.html` and `admin/index.html` (public anon key for guest portal and API access)
2. **Database Tables Exist:**
   - `bookings` (guest_name, email, phone, room_type, check_in, check_out, total_amount, status, etc.)
   - `orders` (items, total, status, created_at)
   - `reviews` (name, email, rating, text, date, created_at)
   - `contact_messages` (name, email, message, created_at)

3. **Optional — Deploy**
   - Deploy `index.html` and `admin/` to Vercel, Netlify, or any static host
   - Admin is already deployed at: https://project-m7yru.vercel.app

## 🔑 Key Features

### Guest Experience
- **Browse Luxury Rooms** — Deluxe Suite, Presidential Penthouse, Standard Twin, Family Suite, etc. with pricing
- **Virtual Waiter** — Order from Kenyan and international menu (starters, mains, desserts, drinks)
- **Real-time Cart** — Dynamic pricing with service charge (10%)
- **Secure Booking** — Full guest details, ID verification, payment method selection (Credit Card / M-Pesa)
- **Leave Reviews** — 5-star ratings with feedback
- **Contact Hotel** — Direct message submission

### Staff/Admin Operations
- **Dashboard KPIs** — Bookings, revenue, F&B orders, reviews at a glance
- **Booking Management** — View, filter, cancel, checkout
- **Order Tracking** — Kitchen-facing order status: pending → preparing → served
- **Front Desk** — Room occupancy, today's arrivals, check-in/out
- **Housekeeping** — Priority task cards, staff assignment, auto-assign
- **HR Payroll** — Gross payroll, overtime, deductions, net disbursement
- **Inventory** — Stock levels (OK, Low, Critical), supplier contacts, purchase orders
- **Accountant Panel** — Invoice & payroll approval workflow
- **Reports** — Revenue charts, occupancy analysis, F&B performance, audit logs

## 🎨 Design Highlights

- **Color Scheme** — Gold (#c9a227 / #b8952a) + Dark Navy (#0f172a) + Soft Cream (#f8f9fa)
- **Typography** — Playfair Display (serif, headlines) + Inter/DM Sans (body text)
- **Responsive** — Mobile-first Tailwind grid, glassmorphic nav on hero, animated transitions
- **Accessibility** — ARIA-friendly form labels, semantic HTML, icon + text combos

## 📊 Tech Details

- **Real-time Sync** — Supabase listener pattern keeps admin console updated live
- **Status Badges** — Color-coded booking/order status (pending, confirmed, preparing, served, etc.)
- **Toast Notifications** — User feedback for actions (order placed, review submitted, booking cancelled, etc.)
- **Charts** — Chart.js bar chart for booking distribution by room type
- **Mobile Navigation** — Hamburger menu on mobile, fixed header, overlay backdrop

## ⚙️ Configuration

### Supabase Credentials (Embedded)
Both portals use the same Supabase project:
- **Project URL** — `https://neknhnxwcmcxwdqrwdta.supabase.co`
- **Anon Key** — Public key for guest & admin portal (can be exposed in frontend)

### Default Admin Login
- **Email** — `admin@makarhotels.com`
- **Password** — `admin` (change in production)

### Room Data (Hardcoded in Portal)
```javascript
{ id: 'r1', name: 'Deluxe Suite', type: 'suite', price: 25000, ... }
{ id: 'r2', name: 'Executive Room', type: 'suite', price: 18000, ... }
// ... 6 rooms total
```

### Menu Data (Hardcoded in Portal)
```javascript
{ id: 'm1', name: 'Grilled Tilapia', cat: 'mains', price: 1800, ... }
{ id: 'm2', name: 'Nyama Choma Platter', cat: 'mains', price: 2200, ... }
// ... 6 menu items across categories
```

## 🔐 Security Notes

- Admin login is hardcoded in JavaScript (use proper auth in production)
- Supabase anon key is public in frontend (use Row Level Security policies in Supabase)
- No input validation on sensitive fields (sanitize in production)
- All data is plaintext in transit (use HTTPS in production)

## 📱 Deployment

Deployed on **Vercel** at: https://project-m7yru.vercel.app

To redeploy:
```bash
vercel --prod
```

## 🐛 Known Limitations

- Housekeeping, HR, and invoice data are hardcoded (not yet in Supabase)
- No authentication for guest portal (any user can book)
- No email confirmations or payment processing (demo only)
- Reports are placeholder UI (no real data export)
- No multi-language support

## 🛠 Future Enhancements

- [ ] Real authentication (OAuth2, email verification)
- [ ] Payment gateway integration (Stripe, M-Pesa)
- [ ] Email confirmations & reminders
- [ ] Multi-room/admin user accounts
- [ ] Invoice PDF generation
- [ ] Housekeeping task sync to Supabase
- [ ] Mobile app (React Native / Flutter)
- [ ] SMS notifications
- [ ] Analytics dashboard (occupancy trends, revenue forecasting)

## 📞 Contact & Support

- **Hotel Address** — Westlands, Nairobi, Kenya
- **Phone** — +254 700 123 456
- **Email** — reservations@makarhotel.com
- **Portal Version** — v1.0

---

**© 2026 Makar Hotel Group. All rights reserved.**

Built with ❤️ for luxury hospitality in Nairobi.
