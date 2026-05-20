# 🚀 Quick Start Commands

## Start Backend (Terminal 1)
```bash
cd backend
npm start
```

## Start Frontend (Terminal 2)
```bash
cd frontend
npm run dev
```

## Access Application
Open browser: http://localhost:3000

## Test Accounts (run `node seedUsers.js` in backend folder)
| Role    | Email               | Password    |
|---------|---------------------|-------------|
| Employee| employee@example.com| password123 |
| IT      | it@example.com      | password123 |
| Admin   | admin@example.com   | password123 |

## First Time Setup
If this is your first time:

### Backend Setup
```bash
cd backend
npm install
npm install cors
node seedUsers.js   # Create demo users (employee@example.com, it@example.com, admin@example.com)
npm start
```

### Frontend Setup
```bash
cd frontend
npm install
npm run dev
```

## Production Build
```bash
cd frontend
npm run build
```

Serve the `dist/` folder with any static server.

---

## Phase A Features

- **Leave Management** – Employees apply leave (Annual, Sick, Personal, Unpaid); Admin/IT approve or reject
- **Employee Directory** – Search and filter employees by name, department
- **Announcements** – Company-wide announcements; Admin/IT can create and pin
- **AI Chatbot** – Floating chat widget (bottom-right). Uses OpenAI when `OPENAI_API_KEY` is set; otherwise uses built-in fallback responses

### AI Chatbot Setup (Optional)

To enable real AI responses via OpenAI:

1. Create `backend/.env` with:
   ```
   OPENAI_API_KEY=sk-your-openai-api-key-here
   ```
2. Restart the backend server

Without the key, the chatbot still works with rule-based fallback responses.

---

**That's it! Your enterprise portal is ready!** 🎉
