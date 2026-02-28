# Deploying Uptoskills-Ai-Resume-Builder

This repository contains a React frontend (Vite) in `frontend/` and an Express backend in `backend/`.

Recommended approach:

1. Frontend: Deploy to Vercel (continuous deployment from GitHub)
   - Connect your GitHub account to Vercel and import this repository.
   - In project settings set the Root Directory to `frontend`.
   - Build command: `npm run build`
   - Output Directory: `dist`
   - Vercel will handle preview and production deploys automatically.

2. Backend: Deploy separately (Render, Railway, or Heroku)
   - The backend is an Express app (`backend/index.js`) and expects environment variables listed below.
   - Use a service that supports a persistent Node process (Render or Railway recommended).

Environment variables required by the backend

- `MONGO_DB_URL` or `MONGO_URI` (MongoDB connection string)
- `JWT_SECRET` (JWT signing secret)
- `ADMIN_EMAIL` (optional admin email used for seeding/admin login)
- `ADMIN_PASSWORD` (optional admin password)
- `CLIENT_URL` (frontend URL, e.g., https://your-site.vercel.app)
- `GROQ_API_KEY` (if using the AI features that require GROQ)
- `BACKEND_URL` (public URL of your backend; used to build template URLs)

Quick steps to connect GitHub → Vercel

1. Sign in to https://vercel.com and click "New Project" → "Import Git Repository".
2. Pick `niyaz-ahmad777/Uptoskills-Ai-Resume-Builder`.
3. Under "Root Directory" enter `frontend` and leave other defaults.
4. Add any environment variables required by the frontend (if any) in Vercel's dashboard.
5. Deploy. After the first deploy, set `CLIENT_URL` in your backend service to the Vercel URL.

Notes
- Vercel is suitable for the static frontend. The backend is a full Express server and should be deployed to a Node host.
- If you want a single-host solution, we can refactor the backend into serverless functions (would require changes).
