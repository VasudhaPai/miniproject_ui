<h1 align="center">Sentinel — Session-Aware Prompt Injection Detection System</h1>

<p align="center">
  A session-aware security system for detecting prompt injection and jailbreak attempts in multi-turn conversations.
</p>

<p align="center">
  Python • FastAPI • PyTorch • DeBERTa • Sentence Transformers • Redis • React
</p>

<hr>

<h2>Overview</h2>

<p>
Sentinel is a session-aware security system designed to detect
<strong>prompt injection and jailbreak attempts</strong> in multi-turn conversations.
</p>

<p>
Unlike approaches that analyze each prompt independently, Sentinel combines
<strong>semantic analysis</strong> with <strong>behavioral signals from conversation history</strong>
to identify gradual or multi-turn attacks.
</p>

<h2>Key Features</h2>

<ul>
  <li>Prompt injection and jailbreak detection</li>
  <li>Session-aware multi-turn analysis</li>
  <li>DeBERTa-based semantic classification</li>
  <li>Sentence Transformer-based similarity analysis</li>
  <li>Behavioral risk analysis</li>
  <li>Attack-pattern and probing detection</li>
  <li>Role-shift and repetition analysis</li>
  <li>Redis-based session memory</li>
  <li>Risk-based decisions: <code>ALLOW</code>, <code>WARN</code>, or <code>BLOCK</code></li>
  <li>FastAPI backend with React dashboard</li>
</ul>

<h2>How It Works</h2>

```text
                         User Message
                              |
                              v
                     Semantic Analysis
                      DeBERTa + MiniLM
                              |
                              v
                    Behavioral Analysis
                   Conversation History
                              |
                              v
                      Risk Fusion Engine
                              |
                              v
                 +-----------------------+
                 |                       |
                 |   ALLOW / WARN /      |
                 |        BLOCK          |
                 |                       |
                 +-----------------------+
```

<p>
Sentinel evaluates both the current prompt and the user's conversation trajectory.
This allows it to identify attacks that may appear harmless when individual messages
are analyzed separately.
</p>

<h2>Tech Stack</h2>

<h3>Backend</h3>

<ul>
  <li>Python</li>
  <li>FastAPI</li>
  <li>PyTorch</li>
  <li>Hugging Face Transformers</li>
  <li>DeBERTa</li>
  <li>Sentence Transformers</li>
  <li>Redis</li>
</ul>

<h3>Frontend</h3>

<ul>
  <li>React</li>
  <li>Vite</li>
  <li>Tailwind CSS</li>
</ul>

<h3>Deployment</h3>

<ul>
  <li>Docker</li>
  <li>Docker Compose</li>
</ul>

<h2>Project Structure</h2>

```text
sentinel/
│
├── backend/
│   ├── behavioral/       # Behavioral analysis and risk features
│   ├── models/           # ML model components
│   ├── research/         # Evaluation and analysis scripts
│   ├── session/          # Session and conversation handling
│   ├── main.py           # FastAPI application
│   ├── pipeline.py       # Detection pipeline
│   ├── config.py         # Configuration
│   └── requirements.txt
│
├── frontend/
│   ├── src/              # React application
│   └── public/            # Static assets
│
└── docker-compose.yml     # Redis service configuration
```

<h2>Detection Pipeline</h2>

<ol>
  <li>The user submits a message.</li>
  <li>The message is analyzed using semantic detection models.</li>
  <li>Behavioral features are extracted from the conversation history.</li>
  <li>Semantic and behavioral signals are combined by the risk engine.</li>
  <li>Sentinel assigns a risk level.</li>
  <li>The system returns an <code>ALLOW</code>, <code>WARN</code>, or <code>BLOCK</code> decision.</li>
</ol>

<h2>Running the Project</h2>

<h3>Prerequisites</h3>

<p>Make sure the following are installed:</p>

<ul>
  <li>Python 3.x</li>
  <li>Node.js and npm</li>
  <li>Docker Desktop</li>
</ul>

<h3>1. Start Redis</h3>

```bash
docker compose up -d
```

<h3>2. Start the Backend</h3>

```bash
cd backend

python -m venv .venv
```

<p>On Windows, activate the virtual environment:</p>

```bash
.venv\Scripts\activate
```

<p>Install the required Python packages:</p>

```bash
pip install -r requirements.txt
```

<p>Start the FastAPI server:</p>

```bash
uvicorn main:app --reload --port 8000
```

<h3>3. Start the Frontend</h3>

<p>Open another terminal:</p>

```bash
cd frontend
npm install
npm run dev
```

<p>
The frontend can then be accessed through the local URL provided by Vite.
</p>

<h2>API</h2>

<p>
The backend provides endpoints for interacting with the detection system,
viewing session statistics, and managing sessions.
</p>

<h3>Available Endpoints</h3>

```text
POST   /api/chat
GET    /api/stats
DELETE /api/session
```

<h2>Evaluation</h2>

<p>
The system was evaluated on a prompt-injection detection dataset using
classification and behavioral evaluation metrics.
</p>

<p>
The evaluated Sentinel configuration achieved approximately:
</p>

<ul>
  <li><strong>F1-score:</strong> 0.92</li>
  <li><strong>Escalation Recall:</strong> 1.00</li>
</ul>

<p>
These results are experimental and should not be interpreted as production
security guarantees.
</p>

<h2>Limitations</h2>

<ul>
  <li>The project is a research prototype.</li>
  <li>Detection may produce false positives or false negatives.</li>
  <li>Performance depends on the evaluation dataset and attack patterns.</li>
  <li>Additional testing is required for domain-specific and previously unseen attacks.</li>
  <li>The current implementation is not intended to replace a complete production security system.</li>
</ul>

<h2>Future Improvements</h2>

<ul>
  <li>Larger and more diverse attack datasets</li>
  <li>Improved model optimization</li>
  <li>Authentication and rate limiting</li>
  <li>Configurable risk thresholds</li>
  <li>Human-review workflows</li>
  <li>Improved logging and monitoring</li>
</ul>

<hr>

<p align="center">
  <strong>Sentinel</strong> — Session-aware detection for safer multi-turn LLM interactions.
</p>
