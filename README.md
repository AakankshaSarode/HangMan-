
📚 BookFinder with LLM Integration

BookFinder is a React-based web application that lets users search for books from the Open Library API, save favorites, and get AI-powered summaries/recommendations using a local LLM (via Ollama).

🚀 Features

🔍 Search Books by title, author, or subject

🖼️ View book details (cover, author, year, availability)

📌 Save favorite books (stored locally)

🤖 AI Integration: Get short summaries/recommendations for books using Ollama LLM

🎨 Clean UI with React + CSS + React Icons

🛠️ Tech Stack

Frontend: React, React Icons, CSS

Backend: Node.js + Express

LLM: Ollama (local inference engine)

API: Open Library Search API

📂 Project Structure
BookFinder/
├── client/                # React frontend
│   ├── src/
│   │   ├── App.js
│   │   ├── App.css
│   │   ├── components/
│   │   │   ├── SearchBar/
│   │   │   ├── BookList/
│   │   │   └── Favorites/
│   │   └── lib/
│   │       └── openLibrary.js
│   └── package.json
│
├── server/                # Express backend
│   ├── server.js
│   └── package.json
│
└── README.md

⚙️ Installation & Setup
1. Clone the repository
git clone https://github.com/your-username/bookfinder.git
cd bookfinder

2. Setup Frontend (React)
cd client
npm install


Run the React app:

npm start

3. Setup Backend (Express + Ollama)
cd ../server
npm install


Run backend server:

node server.js


By default, it runs on http://localhost:3001
.

4. Setup Ollama (LLM Engine)

Install Ollama → Download here

Start Ollama service (it usually auto-starts):

ollama serve


Pull a model:

Since llama3 is heavy (needs >4.6GB RAM), use a lighter one:

ollama pull mistral


Test the model:

ollama run mistral

5. Connect Backend with Ollama

Your server.js calls Ollama API at:

http://localhost:11434/api/generate


Example request from backend:

const response = await fetch("http://localhost:11434/api/generate", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({
    model: "mistral",   // or llama2, depending on what you pulled
    prompt: `Summarize the book: ${title}`,
  }),
});

▶️ Running the Project

Start Ollama service (runs in background)

Run Backend

cd server
node server.js


Run Frontend

cd client
npm start


Open browser → http://localhost:3000

🧪 Example Commands

Search book: type "Harry Potter" in search bar → results appear

Save book: click 📌 icon to add to favorites

Get AI summary: backend requests Ollama with book title and shows LLM response

⚠️ Common Issues

Port already in use (11434)

Ollama is already running. No need to run ollama serve twice.

Model memory error

If llama3 fails due to RAM, use smaller models like mistral or llama2.

Cannot GET /

Make sure both frontend (npm start) and backend (node server.js) are running.

