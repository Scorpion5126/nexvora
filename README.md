# Nexvora Digital Assessment Platform V10

## Local development

### Terminal 1 — backend
```powershell
cd server
npm install
npm run dev
```
Backend: http://localhost:5000
Health: http://localhost:5000/api/health

### Terminal 2 — frontend
```powershell
cd client
npm install
npm run dev
```
Frontend: http://localhost:5173

The Vite dev server proxies `/api` to `http://localhost:5000`, so no `VITE_API_URL` is required locally.

## Admin demo
- Email: admin@nexvoradigital.com
- Password: Admin@123

Change the default admin password before production use.

## Render
This project is designed to run as one Node web service. Build:
```bash
npm install --prefix server && npm install --prefix client && npm run build --prefix client
```
Start:
```bash
npm start --prefix server
```
If the repository contains an extra project folder, set Render Root Directory to that folder.


## Email OTP verification
Candidate registration now requires a 6-digit email OTP. The OTP expires after 10 minutes, allows 5 incorrect attempts, and can be resent after 60 seconds. Admin login remains unchanged.

### Gmail setup
Use a Gmail/Google Workspace account with 2-Step Verification enabled and create a Google **App Password**. Do not use the normal Gmail password. Add these server environment variables: `SMTP_HOST=smtp.gmail.com`, `SMTP_PORT=465`, `SMTP_SECURE=true`, `SMTP_USER=yourgmail@gmail.com`, `SMTP_PASS=your-16-character-app-password`, and optionally `SMTP_FROM=Nexvora Digital <yourgmail@gmail.com>`.

For local development, put the same values in `server/.env`. For Render, add them under the Web Service Environment Variables. Never commit the real SMTP password or app password to GitHub.


## V11 manual mode
- Candidate registration no longer uses email OTP or SMTP.
- Candidate account is created immediately after valid registration.
- Questions are added manually to each assessment.
- Automatic question generation and random question shuffling are disabled.
