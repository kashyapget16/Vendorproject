# Vendor Management Portal (ERP Module)

A comprehensive, responsive web application for managing vendor onboarding, purchase orders, shipments, invoices, and payments. Built as a mock frontend demo using React, Vite, and Tailwind CSS.

## 🌟 Overview

This project serves as the frontend interface for an ERP vendor management module. It features two distinct portals:
1. **Admin Portal**: For internal employees to manage vendors, approve purchase orders, track shipments, and release payments.
2. **Vendor Portal**: For external vendors to accept purchase orders, submit invoices, dispatch shipments, and track their payment statuses.

## 🔐 Simulated Authentication Flow

> [!NOTE]
> **There is no real backend API.** The entire application runs locally in your browser.

To allow seamless demonstration of both Admin and Vendor features, the app uses a **Simulated Authentication Flow**:
- State is managed globally via React Context (`MockDataContext`).
- When clicking "Login as Admin" or "Login as Vendor", no network requests are made. The app simply sets a local `user` object in the React Context (`{ role: 'admin' }` or `{ role: 'vendor', vendorId: 'v1' }`).
- This mock database and user session are instantly persisted to your browser's `localStorage` (under the key `vendorPortalData`). If you refresh the page, your "session" remains active.
- To switch roles, simply click **Logout** in the sidebar, and you will be redirected back to the login page.

## ✨ Key Features

### 🏢 Admin Workflow
- **Dashboard**: KPI tiles and visual charts for active vendors, POs, and payments.
- **Vendor Onboarding**: Approve/Reject new vendor registrations.
- **Vendor Management**: Update vendor status (Active, Inactive, Blacklisted) and view details.
- **Product Catalog**: Add/manage products and generate/print barcodes.
- **PO Creation**: Generate purchase orders, add line items, and assign them to vendors.
- **Invoice Approval**: Review vendor-submitted invoices and approve/reject them.
- **Payment Tracking**: Track and release payments for approved invoices.

### 🚚 Vendor Workflow
- **Multi-step Signup**: Modern, guided registration flow.
- **Dashboard**: Quick view of assigned POs, pending invoices, and payments due.
- **PO Management**: Review, accept, or reject assigned purchase orders.
- **Invoice Submission**: Create invoices against accepted/fulfilled purchase orders.
- **Shipment Handling**: Dispatch shipments and update tracking information.
- **Payment Tracking**: View ledger of submitted invoices and payment status.
- **Barcode View**: Generate and print product barcodes for packaging.

## 📁 Project Structure

```text
src/
├── assets/         # Static images and icons
├── components/     # Reusable UI components (Buttons, Cards, Tables, Inputs)
├── context/        # React Context (MockDataContext for state management)
├── layouts/        # Shared page wrappers (AdminLayout, VendorLayout)
├── lib/            # Utility functions (e.g., class string merging)
├── pages/          # Application routes
│   ├── admin/      # Admin-specific pages (Dashboard, Vendor Mgmt, etc.)
│   ├── vendor/     # Vendor-specific pages (Dashboard, POs, Invoices, etc.)
│   └── auth/       # Login and Signup pages
├── App.jsx         # Main React Router configuration
├── index.css       # Global styles and Tailwind imports
└── main.jsx        # React application entry point
```

## 🛠️ Technology Stack

- **Frontend Framework**: React 19 (Bootstrapped with Vite)
- **Routing**: React Router DOM v7
- **Styling**: Tailwind CSS v4 (Using `@tailwindcss/postcss`)
- **Icons**: Lucide React
- **Charts**: Recharts
- **Barcode Generation**: `react-barcode`
- **State Management**: React Context API
- **Data Persistence**: LocalStorage (Mock Database)

## 🚀 Setup & Local Development

1. **Clone the repository**
2. **Install Dependencies**:
   ```bash
   npm install
   ```
3. **Start the Development Server**:
   ```bash
   npm run dev
   ```
4. **Open in Browser**: Navigate to `http://localhost:5173`

> [!WARNING]
> **Tailwind v4 Troubleshooting:** If you encounter PostCSS or Tailwind-related errors (e.g., `Failed to resolve import "tailwindcss"` or PostCSS configuration errors), ensure you completely **stop your terminal process (Ctrl + C)** and restart the server with `npm run dev`. Vite caches PostCSS configurations heavily.

## 🌐 Deployment (Vercel)

This project is fully ready to be deployed on Vercel. 
1. Push the code to a GitHub repository.
2. Log into Vercel and import the repository.
3. Vercel will automatically detect the **Vite** framework.
4. Click **Deploy**. No environment variables are required since the data is mocked locally.
