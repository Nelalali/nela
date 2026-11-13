# NELA AI backend

This repository contains the NELA chat API used by the NELA frontend.

## Deploy on Render

1. In Render, choose **New + → Web Service**.
2. Connect the GitHub repository **Nelalali/nela** and branch **main**.
3. Render can use the included `render.yaml`; otherwise use:
   - Runtime: Node
   - Build command: `npm install`
   - Start command: `npm start`
4. Add environment variables:
   - `GEMINI_API_KEY`: your private Google AI Studio API key
   - `FRONTEND_URL`: `https://nela-frontend1.onrender.com`
   - Optional `GEMINI_MODEL`: `gemini-2.5-flash`
5. Deploy and check `https://YOUR-BACKEND.onrender.com/health`. It should return `status: ok` and `aiConfigured: true`.

## Connect the frontend

In the Render settings for the NELA Static Site, add:

- Key: `VITE_API_URL`
- Value: the backend base URL, for example `https://nela-ai.onrender.com` (do not add `/chat`).

Then trigger **Manual Deploy → Clear build cache & deploy** so Vite rebuilds with the new environment variable.

The API key belongs only in the backend environment. Never put it in the frontend or commit it to GitHub.
