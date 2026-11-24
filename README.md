# 🧠 NeuraNet (Semantic Mesh) — The AI Neural Internet

> **"Instead of webpages, the internet becomes a network of intelligent knowledge nodes connected through semantic reasoning."**

NeuraNet is an AI-powered Neural Internet where knowledge nodes are connected through semantic reasoning instead of hyperlinks. Built with React, FastAPI, SQLite & Google Gemini. 

Instead of browsing static pages, users query concepts and let AI build reasoning paths across connected knowledge nodes — turning the internet into an intelligent, meaning-driven network.

## 🚀 The Vision
The traditional web relies on hardcoded hyperlinks. NeuraNet reimagines this by creating a **living graph of knowledge**. Each node represents a concept, topic, or idea. Nodes auto-connect using Gemini embeddings, so the system truly understands how ideas relate. Users can search semantically, generate new nodes with AI, and visualize multi-hop reasoning trails in an interactive graph.

## ✨ Core Features
- 🕸️ **Interactive Neural Graph** — Explore knowledge as a living, connected graph (Powered by React Flow).
- 🔗 **Semantic Auto-Linking** — Nodes auto-connect based on meaning, not just text matching.
- 🔍 **Reasoning Search** — Ask a question, get an AI answer + a visual reasoning path across nodes.
- 🤖 **AI Node Generation** — Type a topic, AI suggests and generates related knowledge nodes.
- 📄 **Rich Node Pages** — AI summaries, related concepts, and connection explanations.
- 🎨 **Modern Neural UI** — Dark, glassmorphic, animated, and beautiful.

## 🛠️ Tech Stack

**Frontend:**
- React (Vite)
- TailwindCSS (for modern UI)
- React Flow (for graph visualization)
- Axios

**Backend:**
- Python (FastAPI)
- SQLAlchemy (ORM)
- SQLite (Database)
- Pydantic (Data validation)

**AI & Intelligence:**
- Google Gemini API (LLM + Embeddings)
- *Note: Designed to run efficiently on CPU-only laptops (Zero local GPU required).*

## 🏗️ Architecture & Folder Structure
The project is divided into two main parts:
- `backend/`: FastAPI server, AI services, Database models, and Routers.
- `frontend/`: React app, Graph UI, and API integration.

*(Detailed folder structure can be found in the repository files).*

## 🗄️ Database Schema

**1. Nodes Table** (`knowledge_nodes`)
- `id` (UUID): Primary Key
- `title` (String): Name of the concept
- `content` (Text): Detailed explanation
- `embedding` (JSON): Gemini generated vector for semantic matching
- `created_at` (Timestamp)

**2. Edges Table** (`semantic_edges`)
- `id` (UUID): Primary Key
- `source_id` (UUID): FK to Nodes
- `target_id` (UUID): FK to Nodes
- `relation_type` (String): E.g., "relates_to", "is_part_of", "causes"
- `weight` (Float): Semantic similarity score (0.0 to 1.0)
- `reasoning` (Text): AI explanation of why these nodes are connected

## 🔌 API Endpoints

**Node Router (`/api/nodes`)**
- `GET /` : List all knowledge nodes
- `POST /` : Create a new node (Triggers auto semantic linking)
- `GET /{id}` : Get detailed node info
- `DELETE /{id}` : Delete a node

**Graph Router (`/api/graph`)**
- `GET /` : Fetch full graph data (Nodes + Edges) for React Flow

**Search Router (`/api/search`)**
- `POST /semantic` : Search nodes using Gemini embeddings
- `POST /reason` : Multi-hop reasoning query returning an AI-generated answer and reasoning path

**AI Router (`/api/ai`)**
- `POST /generate-node` : Auto-generate a concept node based on a prompt
- `POST /suggest-links` : Suggest semantic links for a newly created node

## 🏁 Getting Started

### Prerequisites
- Python 3.9+
- Node.js 18+
- Google Gemini API Key (Get it from [Google AI Studio](https://aistudio.google.com/))

### 1. Clone the Repository
```bash
git clone https://github.com/vishakha2121/semantic-mesh.git
cd semantic-mesh


cd backend
python -m venv venv
# Activate venv (Windows: .\venv\Scripts\activate | Mac/Linux: source venv/bin/activate)
pip install -r requirements.txt

cd frontend
npm install