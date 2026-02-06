````markdown
# QR Menu — Backend

This folder contains the extracted backend for the QR Menu project (Express, Socket.IO, MongoDB).

Quick start:

1. Open a terminal in `components/backend/`
2. Copy `.env.example` to `.env` and set `MONGODB_URI` and `PORT` as needed.

```bash
npm install
npm run start
```

Notes:
- The backend expects a MongoDB instance (local or Atlas). If MongoDB is not available, the server falls back to in-memory storage.
- The original project also contains frontend files in the repository root; move or configure static files if you want the backend to serve them.


````
