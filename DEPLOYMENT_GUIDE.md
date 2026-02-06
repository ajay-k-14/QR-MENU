# Self-Hosted Deployment Guide

This guide explains how to run QR Menu on your own server for both local and global access.

## **Local Network Access (Same WiFi/LAN)**

### Step 1: Find Your Computer's IP Address
```powershell
ipconfig
```
Look for "IPv4 Address" (e.g., `192.168.1.100`)

### Step 2: Start the Server
```powershell
npm run dev
```

Server will show:
```
Running on port 5000
📍 http://localhost:5000
🌐 http://192.168.1.100:5000
🌍 http://YOUR_DOMAIN:5000
```

### Step 3: Access from Multiple Devices

**On the same device (your computer):**
```
http://localhost:5000
```

# Deployment Guide — Minimal files for production

Purpose: this file lists the minimal set of files/folders required to deploy the backend (and optional static frontend) and gives the simplest run steps.

## Minimal files required for backend deployment
- `components/backend/server.js` — Express + Socket.IO server (main server code)
- `backend/package.json` — backend dependencies and start scripts
- `backend/.env.example` — example environment variables (copy to `.env` and edit)

Optional (if you want the repo to also serve the static frontend):
- `index.html`, `staff-dashboard.html`, `staff-login.html` (root)
- `components/` (static assets: `js/`, `css/`, `image/`)

If you only deploy the backend service, you can omit the optional frontend files and serve the frontend separately (CDN, S3, Netlify, etc.).

## Quick deploy steps (minimal)
1. Copy the `backend/` folder to your server (or clone the repo and keep only `backend/`).
2. Create a `.env` in `backend/` based on `.env.example` and set `MONGODB_URI` and `PORT`.
3. On the server run:

```bash
cd backend
npm install
npm start
```

Notes:
- The backend falls back to in-memory storage if MongoDB is unreachable, but for production use a running MongoDB instance (local or Atlas).
- If serving the optional static frontend from the same server, place those files in the same folder where `server.js` can serve them (or configure a reverse proxy).

## Environment variables
- `MONGODB_URI` — MongoDB connection string (required for persisted orders)
- `PORT` — port to listen on (default `5000`)

## Recommended production considerations (brief)
- Use a process manager (PM2, systemd, or NSSM on Windows) to keep the process running.
- Use HTTPS in front (reverse proxy like Nginx or a managed TLS service).
- Keep `backend/.env` out of version control; commit only `.env.example`.

---

If you want, I can: remove frontend files from the repository, move the root `server.js` into `backend/` (already copied), or update the root `package.json` to point to the backend. Which would you like next?
Staff dashboard: http://203.45.67.89:5000/staff-dashboard.html
