# CVR-KEYS 🔑

A real-time, smart Key Management System designed for college campus operations. CVR-KEYS simplifies and digitizes key issuance, tracking, and returns across classrooms, laboratories, auditoriums, and administrative offices using QR code automation, role-based access control, and live status synchronization.

---

## 📌 Project Overview

In educational institutions, manual logbooks for key management often lead to misplaced keys, delayed handovers, and lack of accountability. **CVR-KEYS** solves this by providing:

- **Automated QR-Based Handover**: Frictionless key requests and returns by scanning dynamic QR codes.
- **Real-Time Key Tracking**: Live synchronization of available and taken keys across the campus via Socket.io.
- **Role-Based Workflows**: Custom dashboard interfaces tailored to each stakeholder (Admin, Faculty, Security, Operator, Responder).
- **Audit Logs & Reports**: Comprehensive history tracking of all transactions and downloadable PDF audit reports.
- **Notifications & Reminders**: Automated notifications and alerts for overdue or unreturned keys.

---

## 👥 Users & Roles

The system employs granular **Role-Based Access Control (RBAC)** to ensure security and smooth daily operations:

### 1. 🛡️ Admin
- **Full System Administration**: Create, edit, and delete keys, blocks, and departments.
- **User Management**: Approve registrations, manage user permissions, and assign roles.
- **System Reports**: Generate and export detailed PDF audit reports with date and department filtering.
- **Security & API Keys**: Manage department API access keys and review real-time audit logs.

### 2. 👨‍🏫 Faculty / Attender
- **Key Catalog & Search**: Browse and search keys categorized by block (Block A, B, C, etc.) and department.
- **Favorites & Frequent Keys**: Star and quickly access frequently needed keys.
- **Request Keys (QR)**: Generate instant QR codes to present to security for key pickup.
- **Return Keys (QR)**: Generate return QR codes for seamless check-in at the security desk.
- **My Keys**: View currently held keys with checkout timestamps.

### 3. 👮 Security (Key Monitor)
- **Live QR Scanner**: Mobile-optimized scanner to scan faculty request and return QR codes instantly.
- **Available Keys Tab**: Real-time view of all keys currently present in the key room with location tags.
- **Unavailable / Taken Keys Tab**: Live list of keys currently checked out, showing holder details and checkout time.
- **Manual Collection**: "Collect" button to manually check in keys if returned without scanning.

### 4. ⚙️ Operator
- **Operational Oversight**: View key activity feeds, monitor daily logbook checkouts/check-ins, and assist faculty and staff.

### 5. 🚨 Responder
- **Emergency Access**: Fast lookup and priority clearance for emergency facilities, safety personnel, and crisis responders.

---

## 🚀 Setup & Installation Instructions

### Prerequisites

Ensure you have the following installed on your machine:
- **Node.js** (v18.x or later)
- **npm** (v9.x or later) or **yarn**
- **MongoDB** (Local instance or [MongoDB Atlas](https://www.mongodb.com/atlas))
- **Git**

---

### 1. Clone the Repository

```bash
git clone https://github.com/chakrinaini05/CVR-KEYS.git
cd CVR-KEYS
```

---

### 2. Backend Setup

1. **Navigate to the backend directory**:
   ```bash
   cd backend
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Configure environment variables**:
   Create a `.env` file in the `backend/` directory based on `.env.example`:
   ```bash
   cp .env.example .env
   ```

   Configure the variables inside `backend/.env`:
   ```env
   PORT=6203
   MONGO_URI=mongodb://localhost:27017/cvrkeys
   JWT_SECRET=your_jwt_secret_key_here
   CLIENT_URL=http://localhost:3203
   BACKEND_URL=http://localhost:6203

   # Email Configuration (Nodemailer)
   EMAIL_HOST=smtp.gmail.com
   EMAIL_PORT=587
   EMAIL_SECURE=false
   EMAIL_USER=your-email@example.com
   EMAIL_PASS=your-app-password
   EMAIL_FROM=your-email@example.com
   EMAIL_FROM_NAME=CVR Keys

   # Google OAuth (Optional / Production)
   GOOGLE_CLIENT_ID=your-google-client-id
   GOOGLE_CLIENT_SECRET=your-google-client-secret
   ```

4. **Seed initial keys (Optional)**:
   ```bash
   npm run seed:keys
   ```

5. **Start the backend development server**:
   ```bash
   npm run dev
   ```
   *The backend API server will run at: `http://localhost:6203`*

---

### 3. Frontend Setup

1. **Open a new terminal and navigate to the frontend directory**:
   ```bash
   cd frontend
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Configure environment variables**:
   Create a `.env` file in the `frontend/` directory based on `.env.example`:
   ```bash
   cp .env.example .env
   ```

   Configure the variables inside `frontend/.env`:
   ```env
   VITE_APP_NAME=CVR Keys
   VITE_APP_VERSION=1.0.0
   VITE_API_URL=http://localhost:6203/api
   VITE_FRONTEND_URL=http://localhost:3203
   ```

4. **Start the frontend development server**:
   ```bash
   npm run dev
   ```
   *The frontend client will run at: `http://localhost:3203`*

---

### 4. Build for Production

- **Frontend**:
  ```bash
  cd frontend
  npm run build
  ```
- **Backend**:
  ```bash
  cd backend
  npm start
  ```

---

## 🛠 Tech Stack

- **Frontend**: React 19, Vite, Tailwind CSS, Framer Motion, Zustand, Lucide Icons, html2canvas, jsPDF
- **Backend**: Node.js, Express.js, MongoDB, Mongoose, Socket.io, Nodemailer, JWT, bcryptjs, Helmet
- **Source Code**: [https://github.com/chakrinaini05/CVR-KEYS](https://github.com/chakrinaini05/CVR-KEYS)

---