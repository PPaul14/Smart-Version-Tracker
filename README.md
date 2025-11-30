# Smart‑Version‑Tracker

## 🚀 What is Smart‑Version‑Tracker?

Smart‑Version‑Tracker is a micro web‑app that lets a user type or edit text, and then track every change they save — with a full audit trail of added or removed words, length changes, and timestamps.  
Each time the user clicks “Save Version”, the system captures and saves a version summary so you can review the history of edits.  
This makes it perfect for note-taking, drafts, documentation history — anytime you want to track how content evolves.

---

## 🔧 Features

- React / Next.js frontend with a simple text editor UI.  
- Backend (Node.js / Express / Next.js API) to record versions.  
- Detects and records:  
  - Words added  
  - Words removed  
  - Previous and new text length  
  - Timestamp and a unique ID per version (UUID)  
- Version history panel to view all saved versions.  
- Easy data storage — using an in‑memory array, JSON file, or SQLite (as per choice).  
- Clean, minimal UI — focused on functionality.  

---

## 🧰 Tech Stack

- Frontend: React + Next.js, TypeScript, Tailwind CSS (or CSS-in-JS)  
- Backend/API: Node.js + Express (or Next.js API routes)  
- Utils: UUID generation, date/time for timestamps  
- Data storage option: JSON file, SQLite, or in-memory array (for quick prototyping)  

---

## 📁 Project Structure (example)


*(Modify structure as per your actual setup — but keep clear separation of frontend, backend, and data layers.)*

---

## 🛠️ Installation & Local Development

To run the project locally:

```bash
# 1. Clone the repository
git clone https://github.com/PPaul14/Smart-Version-Tracker.git

# 2. Go into project directory
cd Smart-Version-Tracker

# 3. Install dependencies
npm install

# 4. Start development server
npm run dev
### Live Demo  
Live version deployed at: https://mini-audit-scribe.lovable.app
User edits text
       │
       ▼
Clicks "Save Version"
       │
       ▼
Frontend sends POST /save-version request (with the new text)
       │
       ▼
Backend retrieves previous version
       │
       ├── Compare previous text & new text  
       ├── Detect added words  
       ├── Detect removed words  
       ├── Count previous and new text length  
       └── Generate a summary object:
           {
             id: "uuid",
             timestamp: "YYYY-MM-DD HH:MM:SS",
             addedWords: [...],
             removedWords: [...],
             oldLength: <number>,
             newLength: <number>
           }
       │
       ▼
Store the version summary (in-memory / JSON / SQLite)
       │
       ▼
Client can GET /versions to fetch all versions
       │
       ▼
Frontend displays the version history panel with the full edit history

