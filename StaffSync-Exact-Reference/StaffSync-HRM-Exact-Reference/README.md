# StaffSync HRM — College Project

A responsive Human Resource Management demo built with React + Vite, Express, MongoDB/Mongoose, JWT authentication and bcrypt password hashing.

## Features
- Login and registration with Employee, HR and Manager demo roles
- Role-aware dashboard and navigation
- Employee directory (HR can add, edit and delete employee records)
- Attendance check-in/check-out and history
- Leave requests and HR/Manager approval/rejection
- Announcements (HR publishing)
- Training sessions (Manager creation)
- Responsive dark navy/blue UI

## Requirements
- Node.js 20 or newer
- MongoDB Atlas connection string (or local MongoDB)

## Setup (Windows PowerShell)
1. Extract the ZIP into a new folder and open the `StaffSync-HRM` folder in VS Code.
2. Open `server/.env.example`, copy its contents into a new file named `server/.env`.
3. In `server/.env`, set your real `MONGO_URI`, a long random `JWT_SECRET`, and keep `PORT=8000`, `CLIENT_URL=http://localhost:5173`, `NODE_ENV=development` for local testing. The URI should contain one slash before `staffsync`, e.g. `...mongodb.net/staffsync?retryWrites=true&w=majority`.
4. From the project root terminal, run:
   ```powershell
   npm.cmd install
   npm.cmd run install:all
   npm.cmd run dev
   ```
5. Open `http://localhost:5173`. Backend health check: `http://localhost:8000/health`.

If `npm.cmd run dev` reports that a port is already in use, stop the old Vite/backend terminal with Ctrl+C before starting again. Keep backend and frontend running in separate terminals if you prefer.

## Demo flow
1. Register an account. For a college demonstration, choose HR to add employee records and publish announcements; choose Manager to create training and review leave; choose Employee to test attendance and leave requests.
2. Log out and sign in with each test account to demonstrate role-aware pages.
3. Employee records are stored in MongoDB collection `employees`; users are stored in `users`.

## Important demo limitations
- Role selection is enabled at registration to make the classroom demo easy. Do not deploy this configuration publicly: public users should not be allowed to self-assign HR or Manager roles.
- This is an educational project, not a production-ready payroll/security system. Add account provisioning, rate limiting, audit logging, backups, and a privacy/security review before real use.
- Runtime success depends on your local Node.js installation, Atlas credentials, and Atlas Network Access. The backend source files and JSON configuration have been syntax-checked, but this package cannot be tested against your private Atlas account from here.

## Deployment outline
Backend: deploy `server` to a Node host such as Render with `MONGO_URI`, `JWT_SECRET`, `CLIENT_URL` and `NODE_ENV=production` environment variables. Frontend: deploy `client` to Vercel/Netlify with `VITE_API_URL` set to the deployed backend URL. See `client/vercel.json` for SPA fallback configuration.
