# React + TypeScript + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## Expanding the ESLint configuration

If you are developing a production application, we recommend updating the configuration to enable type-aware lint rules:

```js
export default tseslint.config({
  extends: [
    // Remove ...tseslint.configs.recommended and replace with this
    ...tseslint.configs.recommendedTypeChecked,
    // Alternatively, use this for stricter rules
    ...tseslint.configs.strictTypeChecked,
    // Optionally, add this for stylistic rules
    ...tseslint.configs.stylisticTypeChecked,
  ],
  languageOptions: {
    // other options...
    parserOptions: {
      project: ['./tsconfig.node.json', './tsconfig.app.json'],
      tsconfigRootDir: import.meta.dirname,
    },
  },
})
```

You can also install [eslint-plugin-react-x](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-x) and [eslint-plugin-react-dom](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-dom) for React-specific lint rules:

```js
// eslint.config.js
import reactX from 'eslint-plugin-react-x'
import reactDom from 'eslint-plugin-react-dom'

export default tseslint.config({
  plugins: {
    // Add the react-x and react-dom plugins
    'react-x': reactX,
    'react-dom': reactDom,
  },
  rules: {
    // other rules...
    // Enable its recommended typescript rules
    ...reactX.configs['recommended-typescript'].rules,
    ...reactDom.configs.recommended.rules,
  },
})
```
# Job Chat Assistant

An AI-powered conversational job assistant built with Node.js (Express) and React. It allows users to explore job openings, inquire about responsibilities, qualifications, and benefits, and even apply by sharing their profile step-by-step.

---

## 🧠 Conversation Design Approach

The bot is designed to:
- Understand natural language inputs (e.g., "I want to apply", "What are the qualifications for developer?")
- Recognize user intent using keyword-based matching (like "apply", "responsibilities")
- Guide the user through a structured question flow if they want to apply for a job
- Respond dynamically based on the current context (e.g., the job being discussed)

---

## 📋 Candidate Information Collection

When a user wants to apply, the assistant enters a **collecting state**, prompting them one-by-one for:
- Full Name
- Experience
- Skills
- Location
- Notice Period

Responses are stored in `candidateState.info`. Once complete, a formatted summary is returned using the `getCandidateSummary()` function.

---

## ⚙️ Technical Decisions & Tradeoffs

- **Backend (Node.js with Express)**:
  - Lightweight and easy to set up for REST-style endpoints.
  - Uses simple string matching for intent detection (fast but not very robust for NLP).

- **Frontend (React)**:
  - Simple chat interface with basic state management.
  - Easily extendable for animations, avatars, or persistent chat.

- **Tradeoffs**:
  - No NLP/AI service used to keep it lightweight. Could be improved with NLP (Dialogflow, Rasa, or OpenAI).
  - State is stored in memory (non-persistent). In production, a DB or session manager should be used.

---

Setup Instructions

Prerequisites

Node.js (v14+)
npm or yarn

-**Backend Setup**
cd backend
npm install
npm run dev

-**Frontend Setup**
npm install
npm start

Run in Browser

Visit: http://localhost:5173

Try:

What jobs are available?

I want to apply

Tell me the qualifications of Backend Developer