# VIDYAVERSE-AI-d
**VIDYAVERSE AI** is a futuristic study companion for Class 8 and Class 9 students. Using Dual-Explain AI, it teaches Mathematics, Science, SST, and English Grammar step-by-step in English, Hindi, and Bilingual modes, featuring an interactive translator, adaptive quizzes, and revision tools.
<!DOCTYPE html>
<html lang="en">
<head>
<!-- ===== STEP 1: PASTE YOUR API KEY BETWEEN THE QUOTES ON LINE 6 ===== -->
<script>
const API_KEY = "YOUR_API_KEY_HERE";
const MODEL = "gemini-3.5-flash-lite";
</script>
<script>
// ===== YOUR CHATBOT'S INSTRUCTIONS (RTCC) =====
const SYSTEM_PROMPT = `
ROLE: You are VIDYAVERSE AI (“Your AI Teacher. Your Language. Your Future.”), an all-in-one personal AI teacher, English-Hindi translator, subject expert, and adaptive exam preparation coach for Class 8 and Class 9 students.
CRITICAL RULE: You are talking directly to a Class 8 or Class 9 student inside the VIDYAVERSE AI study app. NEVER output HTML code, CSS, JavaScript, or <!DOCTYPE html>. Always reply directly to the student's question with clear, helpful educational explanations, step-by-step solutions, translations, quizzes, or revision notes!

TASK:
Help Class 8 and Class 9 students master their subjects in English, Hindi, and Bilingual (Hindi + English) modes. Provide clear explanations, step-by-step calculations, accurate translations, interactive quizzes, revision notes, and practice exercises.

CONTEXT & SUBJECT MODULES:
1. Mathematics — Maths Master:
   - Teach Class 8 and Class 9 mathematics (algebra, linear equations, geometry, mensuration, percentages, rational numbers, polynomials, etc.).
   - Explain formulas, calculations, and reasoning step by step.
   - Check student answers kindly, point out where a mistake happened, and show how to fix it.
2. Science — Science Lab:
   - Cover Physics, Chemistry, and Biology.
   - Explain scientific concepts using simple language and everyday life examples.
   - Teach definitions, formulas, principles, and practical applications. Suggest only safe, age-appropriate demonstrations.
3. Social Studies — SST Explorer:
   - Cover History, Geography, and Civics.
   - Explain historical events using timelines, important dates, causes, and consequences.
   - Teach Geography and Civics through real-life examples, comparisons, key points, and revision summaries.
4. English Grammar — Grammar Lab:
   - Teach tenses, parts of speech, active and passive voice, direct and reported speech, subject-verb agreement, sentence structure, vocabulary, and punctuation.
   - Provide correct examples, incorrect examples, and clear rules.

SIGNATURE FEATURE — DUAL-EXPLAIN AI:
- Simple English Mode: Clear, grade-appropriate English explanations.
- Easy Hindi Mode: Natural, easy-to-understand Hindi (सरल हिंदी) explanations.
- Bilingual Exam Mode: Explain in simple English AND easy Hindi, showing important English textbook terminology alongside their Hindi meanings (e.g., Linear Equation (रैखिक समीकरण), Force (बल), Photosynthesis (प्रकाश संश्लेषण)) so students understand the concept in Hindi while learning the exact English terms required for exams.

ADAPTIVE EXAM COACH & TEACHING QUALITY:
- Always match the student's selected Class (Class 8 or Class 9), Board (CBSE, ICSE, State Board), Subject, Chapter, Language, and Learning Mode.
- Encourage students to understand concepts rather than rote memorization.
- When asked for hints, give progressive hints before revealing the final answer.
- Do not invent textbook facts. Correct mistakes kindly.
LANGUAGE: If the user writes in Hindi or Hinglish, reply in the same language (or Bilingual mode as selected).
`;
</script>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<title>VIDYAVERSE AI — Your Personal Study Universe</title>
<style>
  :root {
    --bg-main: #060913;
    --bg-panel: rgba(14, 21, 38, 0.78);
    --bg-card: rgba(20, 30, 55, 0.65);
    --bg-input: rgba(10, 15, 28, 0.9);
    --text-main: #f0f6fc;
    --text-muted: #94a3b8;
    --cyan: #00f0ff;
    --cyan-glow: rgba(0, 240, 255, 0.35);
    --violet: #8a2be2;
    --violet-glow: rgba(138, 43, 226, 0.35);
    --neon-blue: #3b82f6;
    --border-color: rgba(0, 240, 255, 0.22);
    --success: #10b981;
    --warning: #f59e0b;
    --danger: #ef4444;
    --radius: 14px;
    --font-sans: 'Segoe UI', system-ui, -apple-system, sans-serif;
  }

  body.light-mode {
    --bg-main: #f0f4f8;
    --bg-panel: rgba(255, 255, 255, 0.9);
    --bg-card: rgba(241, 245, 249, 0.95);
    --bg-input: #ffffff;
    --text-main: #0f172a;
    --text-muted: #475569;
    --cyan: #0284c7;
    --cyan-glow: rgba(2, 132, 199, 0.2);
    --violet: #6d28d9;
    --violet-glow: rgba(109, 40, 217, 0.2);
    --border-color: rgba(2, 132, 199, 0.3);
  }

  body.reduced-motion * {
    animation: none !important;
    transition: none !important;
  }

  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: var(--font-sans);
    background-color: var(--bg-main);
    background-image: 
      radial-gradient(circle at 15% 15%, var(--violet-glow), transparent 35%),
      radial-gradient(circle at 85% 85%, var(--cyan-glow), transparent 35%);
    color: var(--text-main);
    height: 100vh;
    display: flex;
    flex-direction: column;
    overflow: hidden;
  }

  /* Header */
  header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 10px 20px;
    background: var(--bg-panel);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid var(--border-color);
    z-index: 20;
    flex-wrap: wrap;
    gap: 10px;
  }

  .brand {
    display: flex;
    align-items: center;
    gap: 12px;
  }

  .brand-logo {
    width: 38px;
    height: 38px;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--cyan), var(--violet));
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 800;
    font-size: 18px;
    color: #fff;
    box-shadow: 0 0 12px var(--cyan-glow);
  }

  .brand-text h1 {
    font-size: 1.15rem;
    letter-spacing: 1px;
    color: var(--cyan);
    font-weight: 800;
  }

  .brand-text p {
    font-size: 0.72rem;
    color: var(--text-muted);
  }

  .header-controls {
    display: flex;
    align-items: center;
    gap: 8px;
    flex-wrap: wrap;
  }

  .status-pill {
    display: flex;
    align-items: center;
    gap: 6px;
    font-size: 0.78rem;
    padding: 5px 12px;
    border-radius: 20px;
    background: var(--bg-card);
    border: 1px solid var(--border-color);
  }

  .status-dot {
    width: 8px;
    height: 8px;
    border-radius: 50%;
    background: var(--success);
    box-shadow: 0 0 8px var(--success);
  }

  .status-dot.thinking {
    background: var(--warning);
    box-shadow: 0 0 8px var(--warning);
    animation: pulse 1s infinite alternate;
  }

  .status-dot.error {
    background: var(--danger);
    box-shadow: 0 0 8px var(--danger);
  }

  .btn {
    background: var(--bg-card);
    color: var(--text-main);
    border: 1px solid var(--border-color);
    padding: 6px 12px;
    border-radius: 8px;
    cursor: pointer;
    font-size: 0.82rem;
    font-weight: 600;
    display: inline-flex;
    align-items: center;
    gap: 6px;
    transition: all 0.2s ease;
  }

  .btn:hover:not(:disabled) {
    border-color: var(--cyan);
    box-shadow: 0 0 10px var(--cyan-glow);
    transform: translateY(-1px);
  }

  .btn:focus-visible, select:focus-visible, input:focus-visible, textarea:focus-visible {
    outline: 2px solid var(--cyan);
    outline-offset: 2px;
  }

  .btn:disabled {
    opacity: 0.5;
    cursor: not-allowed;
  }

  .btn-primary {
    background: linear-gradient(135deg, rgba(0,240,255,0.2), rgba(138,43,226,0.3));
    border-color: var(--cyan);
  }

  .btn-danger {
    border-color: rgba(239, 68, 68, 0.5);
    color: #fca5a5;
  }
  body.light-mode .btn-danger {
    color: #dc2626;
  }

  /* Layout */
  .app-layout {
    display: flex;
    flex: 1;
    overflow: hidden;
  }

  /* Sidebar */
  .sidebar {
    width: 220px;
    background: var(--bg-panel);
    border-right: 1px solid var(--border-color);
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    padding: 14px 10px;
    overflow-y: auto;
    flex-shrink: 0;
  }

  .nav-list {
    display: flex;
    flex-direction: column;
    gap: 6px;
  }

  .nav-item {
    display: flex;
    align-items: center;
    gap: 10px;
    padding: 10px 12px;
    border-radius: 10px;
    cursor: pointer;
    color: var(--text-muted);
    font-weight: 600;
    font-size: 0.9rem;
    border: 1px solid transparent;
    background: transparent;
    text-align: left;
    width: 100%;
    transition: all 0.2s;
  }

  .nav-item:hover {
    color: var(--text-main);
    background: var(--bg-card);
  }

  .nav-item.active {
    color: var(--cyan);
    background: rgba(0, 240, 255, 0.1);
    border-color: var(--border-color);
    box-shadow: inset 3px 0 0 var(--cyan);
  }

  /* Holographic AI Core in Sidebar */
  .holo-core-wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 16px 8px;
    margin: 10px 0;
    background: var(--bg-card);
    border-radius: var(--radius);
    border: 1px solid var(--border-color);
    position: relative;
    overflow: hidden;
  }

  .holo-core {
    position: relative;
    width: 76px;
    height: 76px;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .ring {
    position: absolute;
    border-radius: 50%;
    border: 2px solid transparent;
  }

  .ring-1 {
    width: 74px;
    height: 74px;
    border-top-color: var(--cyan);
    border-bottom-color: var(--cyan);
    animation: spin 6s linear infinite;
  }

  .ring-2 {
    width: 56px;
    height: 56px;
    border-left-color: var(--violet);
    border-right-color: var(--violet);
    animation: spin-reverse 4s linear infinite;
  }

  .core-sphere {
    width: 32px;
    height: 32px;
    border-radius: 50%;
    background: radial-gradient(circle, #fff, var(--cyan), var(--violet));
    box-shadow: 0 0 18px var(--cyan), 0 0 30px var(--violet);
    animation: pulse 2.5s ease-in-out infinite alternate;
  }

  .core-label {
    margin-top: 10px;
    font-size: 0.75rem;
    font-weight: 700;
    color: var(--cyan);
    letter-spacing: 0.8px;
    text-align: center;
  }

  @keyframes spin { 100% { transform: rotate(360deg); } }
  @keyframes spin-reverse { 100% { transform: rotate(-360deg); } }
  @keyframes pulse {
    0% { transform: scale(0.92); opacity: 0.85; }
    100% { transform: scale(1.08); opacity: 1; }
  }

  /* Main Area */
  .main-area {
    flex: 1;
    display: flex;
    flex-direction: column;
    overflow: hidden;
    position: relative;
  }

  /* Learning Controls Bar */
  .learning-bar {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 8px 16px;
    background: var(--bg-card);
    border-bottom: 1px solid var(--border-color);
    flex-wrap: wrap;
    font-size: 0.8rem;
  }

  .control-group {
    display: flex;
    align-items: center;
    gap: 4px;
  }

  .control-group label {
    color: var(--text-muted);
    font-weight: 600;
  }

  select, input[type="text"] {
    background: var(--bg-input);
    color: var(--text-main);
    border: 1px solid var(--border-color);
    padding: 5px 8px;
    border-radius: 6px;
    font-size: 0.8rem;
  }

  /* Workspace Views */
  .view-panel {
    display: none;
    flex: 1;
    overflow-y: auto;
    padding: 16px;
  }

  .view-panel.active {
    display: flex;
    flex-direction: column;
  }

  /* Chat View Specifics */
  #view-chat {
    padding: 0;
  }

  .chat-scroll {
    flex: 1;
    overflow-y: auto;
    padding: 16px;
    display: flex;
    flex-direction: column;
    gap: 14px;
  }

  /* Dashboard Banner inside Chat */
  .dashboard-hero {
    background: var(--bg-card);
    border: 1px solid var(--border-color);
    border-radius: var(--radius);
    padding: 16px;
    margin-bottom: 8px;
  }

  .subject-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(185px, 1fr));
    gap: 10px;
    margin-top: 12px;
  }

  .subject-card {
    background: var(--bg-panel);
    border: 1px solid var(--border-color);
    border-radius: 10px;
    padding: 12px;
    cursor: pointer;
    transition: all 0.2s ease;
    text-align: left;
  }

  .subject-card:hover, .subject-card.selected {
    border-color: var(--cyan);
    box-shadow: 0 0 14px var(--cyan-glow);
    transform: translateY(-2px);
  }

  .subject-card h4 {
    font-size: 0.92rem;
    color: var(--cyan);
    margin-bottom: 4px;
    display: flex;
    align-items: center;
    gap: 6px;
  }

  .subject-card p {
    font-size: 0.75rem;
    color: var(--text-muted);
    line-height: 1.35;
  }

  /* Messages */
  .msg-row {
    display: flex;
    gap: 10px;
    max-width: 88%;
    align-items: flex-start;
  }

  .msg-row.user {
    align-self: flex-end;
    flex-direction: row-reverse;
  }

  .msg-row.assistant {
    align-self: flex-start;
  }

  .avatar {
    width: 34px;
    height: 34px;
    border-radius: 50%;
    background: var(--bg-card);
    border: 1px solid var(--border-color);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.1rem;
    flex-shrink: 0;
  }

  .bubble {
    background: var(--bg-card);
    border: 1px solid var(--border-color);
    padding: 12px 15px;
    border-radius: 14px;
    font-size: 0.92rem;
    line-height: 1.55;
    position: relative;
    overflow-wrap: break-word;
    word-wrap: break-word;
  }

  .msg-row.user .bubble {
    background: linear-gradient(135deg, rgba(0, 240, 255, 0.18), rgba(138, 43, 226, 0.25));
    border-color: var(--cyan);
  }

  .bubble.error-bubble {
    background: rgba(239, 68, 68, 0.18);
    border-color: var(--danger);
    color: #fca5a5;
  }
  body.light-mode .bubble.error-bubble {
    color: #991b1b;
  }

  .bubble h1, .bubble h2, .bubble h3 {
    margin: 8px 0 4px;
    color: var(--cyan);
    font-size: 1.05rem;
  }

  .bubble ul, .bubble ol {
    margin: 6px 0 6px 20px;
  }

  .bubble li {
    margin-bottom: 4px;
  }

  .bubble code {
    background: rgba(0, 0, 0, 0.35);
    padding: 2px 5px;
    border-radius: 4px;
    font-family: monospace;
    color: var(--cyan);
  }
  body.light-mode .bubble code {
    background: rgba(0,0,0,0.08);
  }

  .bubble table {
    width: 100%;
    border-collapse: collapse;
    margin: 10px 0;
    font-size: 0.85rem;
  }

  .bubble th, .bubble td {
    border: 1px solid var(--border-color);
    padding: 6px 10px;
    text-align: left;
  }

  .bubble th {
    background: rgba(0, 240, 255, 0.1);
    color: var(--cyan);
  }

  .msg-actions {
    display: flex;
    gap: 6px;
    margin-top: 8px;
    padding-top: 6px;
    border-top: 1px solid rgba(255, 255, 255, 0.08);
    flex-wrap: wrap;
  }

  .action-btn {
    background: transparent;
    border: 1px solid var(--border-color);
    color: var(--text-muted);
    font-size: 0.72rem;
    padding: 3px 8px;
    border-radius: 6px;
    cursor: pointer;
  }

  .action-btn:hover {
    color: var(--cyan);
    border-color: var(--cyan);
  }

  /* Starter Chips & Smart Tutor Toolbar */
  .chips-row, .tutor-toolbar {
    display: flex;
    gap: 6px;
    flex-wrap: wrap;
    padding: 6px 16px;
    background: var(--bg-panel);
    border-top: 1px solid var(--border-color);
  }

  .chip {
    background: rgba(0, 240, 255, 0.08);
    border: 1px solid var(--border-color);
    color: var(--text-main);
    padding: 5px 10px;
    border-radius: 16px;
    font-size: 0.76rem;
    cursor: pointer;
    transition: all 0.2s;
  }

  .chip:hover {
    background: rgba(0, 240, 255, 0.2);
    border-color: var(--cyan);
  }

  /* Chat Input Area */
  .chat-input-bar {
    display: flex;
    gap: 8px;
    padding: 12px 16px;
    background: var(--bg-panel);
    border-top: 1px solid var(--border-color);
    align-items: flex-end;
  }

  #chat-input {
    flex: 1;
    background: var(--bg-input);
    color: var(--text-main);
    border: 1px solid var(--border-color);
    border-radius: 10px;
    padding: 10px 12px;
    font-family: inherit;
    font-size: 0.92rem;
    resize: none;
    max-height: 110px;
    min-height: 42px;
  }

  #chat-input:focus {
    border-color: var(--cyan);
    box-shadow: 0 0 10px var(--cyan-glow);
  }

  /* Typing Indicator */
  .typing-dots {
    display: inline-flex;
    gap: 4px;
    align-items: center;
    padding: 4px 2px;
  }

  .typing-dots span {
    width: 7px;
    height: 7px;
    background: var(--cyan);
    border-radius: 50%;
    animation: bounce 1.2s infinite ease-in-out;
  }

  .typing-dots span:nth-child(2) { animation-delay: 0.2s; }
  .typing-dots span:nth-child(3) { animation-delay: 0.4s; }

  @keyframes bounce {
    0%, 80%, 100% { transform: scale(0.6); opacity: 0.4; }
    40% { transform: scale(1.1); opacity: 1; }
  }

  /* Cards and Panels in other tabs */
  .panel-card {
    background: var(--bg-card);
    border: 1px solid var(--border-color);
    border-radius: var(--radius);
    padding: 16px;
    margin-bottom: 16px;
  }

  .panel-card h3 {
    color: var(--cyan);
    margin-bottom: 10px;
    font-size: 1.05rem;
  }

  .grid-2 {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
    gap: 14px;
  }

  textarea.workspace-box {
    width: 100%;
    min-height: 130px;
    background: var(--bg-input);
    color: var(--text-main);
    border: 1px solid var(--border-color);
    border-radius: 8px;
    padding: 10px;
    font-family: inherit;
    margin-top: 8px;
    resize: vertical;
  }

  /* Modal */
  .modal-backdrop {
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    background: rgba(0, 0, 0, 0.75);
    backdrop-filter: blur(6px);
    display: none;
    align-items: center;
    justify-content: center;
    z-index: 100;
    padding: 16px;
  }

  .modal-backdrop.open {
    display: flex;
  }

  .modal-content {
    background: var(--bg-panel);
    border: 1px solid var(--cyan);
    box-shadow: 0 0 25px var(--cyan-glow);
    border-radius: var(--radius);
    max-width: 500px;
    width: 100%;
    padding: 20px;
  }

  .form-row {
    margin-bottom: 12px;
    display: flex;
    flex-direction: column;
    gap: 4px;
  }

  /* Responsive */
  @media (max-width: 768px) {
    .app-layout {
      flex-direction: column;
    }
    .sidebar {
      width: 100%;
      flex-direction: row;
      padding: 8px;
      border-right: none;
      border-bottom: 1px solid var(--border-color);
      overflow-x: auto;
    }
    .nav-list {
      flex-direction: row;
    }
    .holo-core-wrapper {
      display: none;
    }
    .nav-item {
      padding: 6px 10px;
      font-size: 0.8rem;
      white-space: nowrap;
    }
  }
</style>
</head>
<body>

  <!-- Top Header -->
  <header>
    <div class="brand">
      <div class="brand-logo" aria-hidden="true">V</div>
      <div class="brand-text">
        <h1>VIDYAVERSE AI</h1>
        <p>Your AI Teacher. Your Language. Your Future.</p>
      </div>
    </div>

    <div class="header-controls">
      <div class="status-pill" aria-live="polite">
        <span id="status-dot" class="status-dot"></span>
        <span id="status-text">Ready</span>
      </div>
      <button class="btn" id="btn-welcome-setup" title="Personalize Profile">🎓 Profile</button>
      <button class="btn" id="btn-new-chat" title="Start a fresh conversation">➕ New Chat</button>
      <button class="btn btn-danger" id="btn-clear-chat" title="Clear chat and saved history">🗑️ Clear chat</button>
      <button class="btn" id="btn-theme-toggle" title="Toggle Dark/Light Mode">🌗 Theme</button>
    </div>
  </header>

  <!-- Main Layout -->
  <div class="app-layout">
    <!-- Sidebar Navigation -->
    <aside class="sidebar" aria-label="Main Navigation">
      <div class="nav-list">
        <button class="nav-item active" data-target="view-chat">💬 AI Study Chat</button>
        <button class="nav-item" data-target="view-learn">📘 Learn & Dual-Explain</button>
        <button class="nav-item" data-target="view-translate">🌐 Translate Studio</button>
        <button class="nav-item" data-target="view-quiz">📝 Adaptive Quiz</button>
        <button class="nav-item" data-target="view-revise">⚡ Quick Revise</button>
        <button class="nav-item" data-target="view-progress">📊 Planner & Progress</button>
        <button class="nav-item" data-target="view-settings">⚙️ Settings & API Guide</button>
      </div>

      <div class="holo-core-wrapper" aria-hidden="true">
        <div class="holo-core">
          <div class="ring ring-1"></div>
          <div class="ring ring-2"></div>
          <div class="core-sphere"></div>
        </div>
        <div class="core-label">HOLOGRAPHIC AI CORE</div>
      </div>
    </aside>

    <!-- Main Content Area -->
    <main class="main-area">
      <!-- Smart Learning Controls Bar -->
      <div class="learning-bar" role="region" aria-label="Learning Parameters">
        <div class="control-group">
          <label for="sel-class">Class:</label>
          <select id="sel-class">
            <option value="Class 8">Class 8</option>
            <option value="Class 9">Class 9</option>
          </select>
        </div>

        <div class="control-group">
          <label for="sel-board">Board:</label>
          <select id="sel-board">
            <option value="CBSE (NCERT)">CBSE (NCERT)</option>
            <option value="ICSE">ICSE</option>
            <option value="State Board">State Board</option>
          </select>
        </div>

        <div class="control-group">
          <label for="sel-subject">Subject:</label>
          <select id="sel-subject">
            <option value="Mathematics (Maths Master)">📐 Maths Master</option>
            <option value="Science (Science Lab)">🔬 Science Lab</option>
            <option value="Social Studies (SST Explorer)">🌍 SST Explorer</option>
            <option value="English Grammar (Grammar Lab)">✍️ Grammar Lab</option>
          </select>
        </div>

        <div class="control-group">
          <label for="inp-chapter">Chapter:</label>
          <input type="text" id="inp-chapter" placeholder="e.g. Linear Equations, Force..." style="width: 140px;">
        </div>

        <div class="control-group">
          <label for="sel-lang">Language:</label>
          <select id="sel-lang">
            <option value="Bilingual (Hindi + English)">Hindi + English (Bilingual)</option>
            <option value="Simple English">Simple English</option>
            <option value="Easy Hindi">Easy Hindi (सरल हिंदी)</option>
          </select>
        </div>

        <div class="control-group">
          <label for="sel-mode">Mode:</label>
          <select id="sel-mode">
            <option value="Learn">Learn</option>
            <option value="Solve">Solve Step-by-Step</option>
            <option value="Translate">Translate</option>
            <option value="Quiz">Quiz</option>
            <option value="Revise">Revise</option>
          </select>
        </div>
      </div>

      <!-- 1. CHAT VIEW -->
      <section id="view-chat" class="view-panel active">
        <div class="chat-scroll" id="chat-scroll" aria-live="polite">
          <!-- Dashboard Hero inside Chat -->
          <div class="dashboard-hero">
            <h2 style="font-size: 1.05rem; color: var(--cyan);">✨ Welcome to VIDYAVERSE AI Study Universe</h2>
            <p style="font-size: 0.82rem; color: var(--text-muted); margin-top: 4px;">
              Select a Subject Module below or type any question. Your selected Class, Board, Subject, and Language automatically guide your AI Teacher.
            </p>
            <div class="subject-grid">
              <button class="subject-card selected" data-subj="Mathematics (Maths Master)">
                <h4>📐 Maths Master</h4>
                <p>Step-by-step formulas, Algebra, Geometry, Mensuration & Answer Checking.</p>
              </button>
              <button class="subject-card" data-subj="Science (Science Lab)">
                <h4>🔬 Science Lab</h4>
                <p>Physics, Chemistry & Biology with everyday examples & safe demos.</p>
              </button>
              <button class="subject-card" data-subj="Social Studies (SST Explorer)">
                <h4>🌍 SST Explorer</h4>
                <p>History timelines, Geography maps, Civics real-life examples & notes.</p>
              </button>
              <button class="subject-card" data-subj="English Grammar (Grammar Lab)">
                <h4>✍️ Grammar Lab</h4>
                <p>Tenses, Active/Passive, Reported Speech, Vocabulary & error correction.</p>
              </button>
            </div>
          </div>

          <!-- Messages container -->
          <div id="messages-list" style="display: flex; flex-direction: column; gap: 14px;"></div>
        </div>

        <!-- 3 Suggested Starter Questions -->
        <div class="chips-row" id="starter-chips">
          <button class="chip" data-prompt="Explain Linear Equations in One Variable step-by-step with an example in Bilingual mode.">💡 Linear Equations (Maths)</button>
          <button class="chip" data-prompt="Explain Newton's Laws of Motion or Force & Pressure using simple everyday examples.">🚀 Force & Laws of Motion (Science)</button>
          <button class="chip" data-prompt="Teach me Active and Passive Voice rules with 3 correct and incorrect examples.">✍️ Active & Passive Voice (Grammar)</button>
        </div>

        <!-- Smart AI Tutor Quick Action Buttons -->
        <div class="tutor-toolbar" aria-label="Smart AI Tutor Actions">
          <button class="btn" data-tutor="Teach Me Like a Beginner: Explain the current topic using super simple words and an everyday life analogy.">👶 Teach Like a Beginner</button>
          <button class="btn" data-tutor="Why and How?: Explain the deep reasoning behind why this rule or formula works, not just the final facts.">🧠 Why & How?</button>
          <button class="btn" data-tutor="Explain with an Example: Give me a clear, relatable step-by-step example for this concept.">🌟 Explain with Example</button>
          <button class="btn" data-tutor="Give Me a Hint: Don't give me the full solution yet! Give me a progressive hint so I can solve it myself.">🕵️ Give Me a Hint</button>
          <button class="btn" data-tutor="Teach Me Through Questions: Act as a Socratic tutor and ask me guiding questions one by one to help me discover the answer.">❓ Teach via Questions</button>
          <button class="btn" data-tutor="Real-Life Applications: How is this chapter/concept used in real life, technology, or everyday situations?">🌍 Real-Life Use</button>
          <button class="btn" id="btn-regenerate" title="Regenerate the last AI reply">🔄 Regenerate</button>
        </div>

        <!-- Input Bar -->
        <div class="chat-input-bar">
          <button class="btn" id="btn-mic" title="Voice Input (en-IN)" style="height: 42px;">🎤</button>
          <textarea id="chat-input" rows="1" placeholder="Ask a question, paste an answer to check, or ask in Hindi / Hinglish... (Enter to send, Shift+Enter for newline)"></textarea>
          <button class="btn btn-primary" id="btn-send" style="height: 42px; padding: 0 18px;">Send 🚀</button>
        </div>
      </section>

      <!-- 2. LEARN & DUAL-EXPLAIN STUDIO -->
      <section id="view-learn" class="view-panel">
        <div class="panel-card">
          <h3>⚡ Signature Feature: DUAL-EXPLAIN AI Studio</h3>
          <p style="font-size: 0.85rem; color: var(--text-muted); margin-bottom: 12px;">
            Enter any difficult topic, theorem, or scientific law to receive a structured breakdown in your chosen explanation mode.
          </p>
          <div class="grid-2">
            <div>
              <label for="dual-topic" style="font-size:0.82rem; font-weight:600;">Topic or Concept:</label>
              <input type="text" id="dual-topic" placeholder="e.g. Photosynthesis, Pythagoras Theorem, French Revolution" style="width:100%; margin-top:4px; padding:8px;">
            </div>
            <div>
              <label for="dual-mode" style="font-size:0.82rem; font-weight:600;">Explanation Mode:</label>
              <select id="dual-mode" style="width:100%; margin-top:4px; padding:8px;">
                <option value="All 3 Modes (Simple English + Easy Hindi + Bilingual Exam Ready)">✨ All 3 Modes Side-by-Side</option>
                <option value="Simple English Mode">1. Simple English Mode</option>
                <option value="Easy Hindi Mode (सरल हिंदी)">2. Easy Hindi Mode</option>
                <option value="Bilingual Exam Mode (English Terms + Hindi Meaning + Exam Answer)">3. Bilingual Exam Mode</option>
              </select>
            </div>
          </div>
          <button class="btn btn-primary" id="btn-run-dual" style="margin-top: 12px;">🚀 Generate Dual-Explain in Chat</button>
        </div>

        <div class="grid-2">
          <!-- Compare Two Concepts -->
          <div class="panel-card">
            <h3>⚖️ Compare Two Concepts (Table Builder)</h3>
            <p style="font-size: 0.8rem; color: var(--text-muted); margin-bottom: 10px;">Present similarities and differences in a clean exam-ready table.</p>
            <input type="text" id="comp-a" placeholder="First Concept (e.g. Plant Cell, Speed)" style="width:100%; margin-bottom:8px; padding:8px;">
            <input type="text" id="comp-b" placeholder="Second Concept (e.g. Animal Cell, Velocity)" style="width:100%; margin-bottom:10px; padding:8px;">
            <button class="btn btn-primary" id="btn-run-compare">📊 Compare in Chat</button>
          </div>

          <!-- Check My Answer -->
          <div class="panel-card">
            <h3>✅ Check My Answer & Fix Mistakes</h3>
            <p style="font-size: 0.8rem; color: var(--text-muted); margin-bottom: 10px;">Paste a question and your attempt. AI will spot mistakes kindly and show how to fix them.</p>
            <input type="text" id="chk-question" placeholder="Question (e.g. Solve 2x + 5 = 15)" style="width:100%; margin-bottom:8px; padding:8px;">
            <input type="text" id="chk-attempt" placeholder="Your Attempt (e.g. 2x = 20, so x = 10)" style="width:100%; margin-bottom:10px; padding:8px;">
            <button class="btn btn-primary" id="btn-run-check">🔍 Check My Answer in Chat</button>
          </div>
        </div>
      </section>

      <!-- 3. TRANSLATE WORKSPACE -->
      <section id="view-translate" class="view-panel">
        <div class="panel-card">
          <h3>🌐 Dedicated English ⇄ Hindi Academic Translator</h3>
          <p style="font-size: 0.82rem; color: var(--text-muted); margin-bottom: 12px;">
            Translates accurately while preserving essential English textbook terms alongside their Hindi meanings.
          </p>
          <div class="grid-2" style="margin-bottom: 10px;">
            <div>
              <label for="trans-src-lang">Source Language:</label>
              <select id="trans-src-lang" style="width:100%; margin-top:4px; padding:8px;">
                <option value="English">English</option>
                <option value="Hindi">Hindi (हिंदी)</option>
                <option value="Hinglish">Hinglish</option>
              </select>
            </div>
            <div>
              <label for="trans-tgt-lang">Target Language:</label>
              <select id="trans-tgt-lang" style="width:100%; margin-top:4px; padding:8px;">
                <option value="Hindi with important English technical terms preserved in brackets">Hindi (Preserve English Subject Terms)</option>
                <option value="Exam-Ready English with Hindi vocabulary notes">English (Exam-Ready + Hindi Key Terms)</option>
                <option value="Simple Everyday Hindi">Simple Everyday Hindi</option>
              </select>
            </div>
          </div>

          <div class="grid-2">
            <div>
              <label for="trans-input" style="font-size:0.82rem; font-weight:600;">Source Text:</label>
              <textarea id="trans-input" class="workspace-box" placeholder="Paste textbook paragraph, science definition, or Hindi question here..."></textarea>
            </div>
            <div>
              <label for="trans-output" style="font-size:0.82rem; font-weight:600;">Translated Result & Key Terms:</label>
              <textarea id="trans-output" class="workspace-box" readonly placeholder="Translation will appear here..."></textarea>
            </div>
          </div>

          <div style="display:flex; gap:10px; margin-top:12px;">
            <button class="btn btn-primary" id="btn-do-translate">🔄 Translate Now</button>
            <button class="btn" id="btn-copy-translation">📋 Copy Translation</button>
          </div>
        </div>
      </section>

      <!-- 4. ADAPTIVE QUIZ COACH -->
      <section id="view-quiz" class="view-panel">
        <div class="panel-card">
          <h3>📝 Adaptive Exam Coach & Quiz Generator</h3>
          <p style="font-size: 0.82rem; color: var(--text-muted); margin-bottom: 12px;">
            Test your understanding with instant scoring, explanations, or custom AI-generated questions.
          </p>
          <div style="display:flex; gap:10px; flex-wrap:wrap; align-items:center; margin-bottom:14px;">
            <select id="quiz-type-sel" style="padding:7px;">
              <option value="All">All Question Types (MCQ, Fill-Blank, True/False, Short)</option>
              <option value="MCQ">Multiple-Choice (MCQ)</option>
              <option value="TF">True / False</option>
              <option value="FIB">Fill-in-the-Blanks</option>
            </select>
            <button class="btn btn-primary" id="btn-load-builtin-quiz">▶️ Load Built-In Practice Quiz</button>
            <button class="btn" id="btn-ai-custom-quiz">🤖 Generate AI Chapter Quiz in Chat</button>
          </div>

          <div id="quiz-container" style="display:flex; flex-direction:column; gap:12px;"></div>

          <div id="quiz-results" style="margin-top:14px; display:none;" class="panel-card"></div>
        </div>
      </section>

      <!-- 5. QUICK REVISE -->
      <section id="view-revise" class="view-panel">
        <div class="panel-card">
          <h3>⚡ Quick Revision Before Exams</h3>
          <p style="font-size: 0.82rem; color: var(--text-muted); margin-bottom: 12px;">
            Generate concise one-page revision sheets, flashcards, important dates, or formula lists for your current Class, Subject, and Chapter.
          </p>
          <div style="display:flex; gap:8px; flex-wrap:wrap;">
            <button class="btn btn-primary" data-revise="Create a concise 'Quick Revision Before Exams' cheat-sheet with key definitions, formulas, and bullet points.">📄 5-Minute Exam Cheat-Sheet</button>
            <button class="btn" data-revise="Generate 5 interactive Question & Answer Flashcards with key English terms and Hindi meanings.">🗂️ Bilingual Flashcards</button>
            <button class="btn" data-revise="List the most common exam mistakes students make in this chapter and how to avoid them.">⚠️ Common Exam Mistakes</button>
            <button class="btn" data-revise="Create a timeline of important dates/events or a summary table of all formulas in this chapter.">📅 Formula / Timeline Sheet</button>
          </div>
        </div>
      </section>

      <!-- 6. STUDY PLANNER & PROGRESS -->
      <section id="view-progress" class="view-panel">
        <div id="revision-reminder-banner" class="panel-card" style="border-color: var(--warning); display:none;">
          <h3 style="color: var(--warning);">🔔 Spaced Revision Reminder</h3>
          <p id="revision-reminder-text" style="font-size: 0.85rem;"></p>
        </div>

        <div class="grid-2">
          <div class="panel-card">
            <h3>📅 Daily Study Planner</h3>
            <div style="display:flex; gap:6px; margin-bottom:10px;">
              <input type="text" id="plan-task-inp" placeholder="Add study goal (e.g. Revise Ch-2 Force)" style="flex:1; padding:7px;">
              <button class="btn btn-primary" id="btn-add-plan">Add</button>
            </div>
            <ul id="plan-list" style="list-style:none; display:flex; flex-direction:column; gap:6px;"></ul>
          </div>

          <div class="panel-card">
            <h3>📈 Completed Topics & Weak Areas</h3>
            <div style="display:flex; gap:6px; margin-bottom:10px;">
              <input type="text" id="topic-log-inp" placeholder="Topic studied (e.g. Algebraic Identities)" style="flex:1; padding:7px;">
              <select id="topic-status-sel">
                <option value="Mastered">✅ Mastered</option>
                <option value="Needs Revision">⚠️ Needs Revision</option>
              </select>
              <button class="btn btn-primary" id="btn-add-topic">Save</button>
            </div>
            <ul id="topic-log-list" style="list-style:none; display:flex; flex-direction:column; gap:6px;"></ul>
          </div>
        </div>
      </section>

      <!-- 7. SETTINGS & API GUIDE -->
      <section id="view-settings" class="view-panel">
        <div class="panel-card">
          <h3>🔑 Gemini API Setup & Security Notice</h3>
          <p style="font-size: 0.85rem; line-height: 1.5; color: var(--text-muted); margin-bottom: 10px;">
            <strong>How to connect your AI key:</strong> Open <code>index.html</code> in any text editor (like Notepad or VS Code), paste your Gemini API key between the quotes on <strong>Line 6</strong> (<code>const API_KEY = "YOUR_KEY";</code>), save the file, and refresh your browser.<br><br>
            <strong>Model Compatibility Note:</strong> Line 7 is configured with <code>const MODEL = "gemini-3.5-flash-lite";</code>. If the Google Gemini API endpoint returns a 404 Model Not Found error for that model name, the error bubble will inform you clearly so you can check supported Gemini model names.<br><br>
            <strong>Security Warning:</strong> Storing an API key directly inside browser JavaScript (<code>index.html</code>) makes it visible to anyone who inspects the page source. This is fine for personal offline/local learning on your own computer, but for a public production website you must use a secure backend server to keep your API key hidden.
          </p>
        </div>

        <div class="panel-card">
          <h3>♿ Accessibility & Data Controls</h3>
          <div style="display:flex; gap:12px; align-items:center; flex-wrap:wrap;">
            <label style="display:flex; align-items:center; gap:6px; cursor:pointer; font-size:0.88rem;">
              <input type="checkbox" id="chk-reduced-motion"> Enable Reduced Motion (Disable Rings & Animations)
            </label>
            <button class="btn btn-danger" id="btn-reset-all-data">⚠️ Reset All Saved LocalStorage Data</button>
          </div>
        </div>
      </section>
    </main>
  </div>

  <!-- Personalized Welcome Modal -->
  <div class="modal-backdrop" id="welcome-modal" role="dialog" aria-modal="true" aria-labelledby="modal-title">
    <div class="modal-content">
      <h3 id="modal-title" style="color:var(--cyan); margin-bottom:8px;">🚀 Personalize Your VIDYAVERSE AI</h3>
      <p style="font-size:0.82rem; color:var(--text-muted); margin-bottom:14px;">
        Set up your student profile so VIDYAVERSE AI can tailor every explanation to your exact grade and language.
      </p>
      <div class="form-row">
        <label for="mod-name" style="font-size:0.8rem;">Your Name (Optional):</label>
        <input type="text" id="mod-name" placeholder="e.g. Aarav / Priya">
      </div>
      <div class="form-row">
        <label for="mod-class" style="font-size:0.8rem;">Select Class:</label>
        <select id="mod-class">
          <option value="Class 8">Class 8</option>
          <option value="Class 9">Class 9</option>
        </select>
      </div>
      <div class="form-row">
        <label for="mod-board" style="font-size:0.8rem;">Educational Board:</label>
        <select id="mod-board">
          <option value="CBSE (NCERT)">CBSE (NCERT)</option>
          <option value="ICSE">ICSE</option>
          <option value="State Board">State Board</option>
        </select>
      </div>
      <div class="form-row">
        <label for="mod-lang" style="font-size:0.8rem;">Preferred Explanation Language:</label>
        <select id="mod-lang">
          <option value="Bilingual (Hindi + English)">Hindi + English (Bilingual Exam Mode)</option>
          <option value="Simple English">Simple English</option>
          <option value="Easy Hindi">Easy Hindi (सरल हिंदी)</option>
        </select>
      </div>
      <div class="form-row">
        <label for="mod-goal" style="font-size:0.8rem;">Primary Learning Goal:</label>
        <input type="text" id="mod-goal" placeholder="e.g. Score 95% in Maths & Science, Improve English Grammar">
      </div>
      <div style="display:flex; justify-content:flex-end; gap:8px; margin-top:14px;">
        <button class="btn btn-primary" id="btn-save-profile">✨ Save & Enter Universe</button>
      </div>
    </div>
  </div>

<script>
// === COMPATIBILITY POLYFILLS FOR OLDER BROWSERS ===
if (!String.prototype.trimEnd) {
  String.prototype.trimEnd = function () {
    return this.replace(/\s+$/, "");
  };
}
if (!String.prototype.startsWith) {
  String.prototype.startsWith = function (search, pos) {
    pos = !pos || pos < 0 ? 0 : +pos;
    return this.substring(pos, pos + search.length) === search;
  };
}
if (!String.prototype.endsWith) {
  String.prototype.endsWith = function (search, this_len) {
    if (this_len === undefined || this_len > this.length) {
      this_len = this.length;
    }
    return this.substring(this_len - search.length, this_len) === search;
  };
}
if (window.NodeList && !NodeList.prototype.forEach) {
  NodeList.prototype.forEach = Array.prototype.forEach;
}

// === 4. API CONNECTION: EXACT FUNCTION AS REQUIRED ===
async function callAI(history) {
  // history = [{ role: "user" | "assistant", text: "..." }, ...]
  const url = "https://generativelanguage.googleapis.com/v1beta/models/" + MODEL + ":generateContent";
  const res = await fetch(url, {
    method: "POST",
    headers: { "Content-Type": "application/json", "x-goog-api-key": API_KEY.trim() },
    body: JSON.stringify({
      system_instruction: { parts: [{ text: SYSTEM_PROMPT }] },
      contents: history.map(m => ({
        role: m.role === "assistant" ? "model" : "user",
        parts: [{ text: m.text }]
      }))
    })
  });
  const data = await res.json().catch(() => ({}));
  if (!res.ok) throw new Error("Error " + res.status + ": " + ((data.error && data.error.message) || "Request failed"));
  const parts = (data.candidates && data.candidates[0] && data.candidates[0].content && data.candidates[0].content.parts) || [];
  const text = parts.filter(p => p.text && !p.thought).map(p => p.text).join("");
  if (!text) throw new Error("The AI sent an empty reply. Try asking again.");
  return text;
}

// === APPLICATION STATE & STORAGE ===
// Using v2 key so old accidental HTML replies stored in localStorage are automatically cleared
const STORAGE_KEYS = {
  HISTORY: "vidyaverse_chat_history_v2",
  PROFILE: "vidyaverse_profile_v1",
  PLANNER: "vidyaverse_planner_v1",
  TOPICS: "vidyaverse_topics_v1",
  THEME: "vidyaverse_theme_v1"
};

let history = [];
let isWaiting = false;

const elMessagesList = document.getElementById("messages-list");
const elChatScroll = document.getElementById("chat-scroll");
const elChatInput = document.getElementById("chat-input");
const elBtnSend = document.getElementById("btn-send");
const elStatusDot = document.getElementById("status-dot");
const elStatusText = document.getElementById("status-text");

// Safe clipboard helper that works on file:// and older browsers
function copyTextSafe(text, onSuccess) {
  if (navigator.clipboard && navigator.clipboard.writeText) {
    navigator.clipboard.writeText(text).then(onSuccess).catch(function () {
      fallbackCopy(text, onSuccess);
    });
  } else {
    fallbackCopy(text, onSuccess);
  }
}

function fallbackCopy(text, onSuccess) {
  const ta = document.createElement("textarea");
  ta.value = text;
  ta.style.position = "fixed";
  ta.style.left = "-9999px";
  document.body.appendChild(ta);
  ta.select();
  try {
    document.execCommand("copy");
    if (onSuccess) onSuccess();
  } catch (e) {}
  document.body.removeChild(ta);
}

// Escape HTML safely before formatting markdown
function escapeHTML(str) {
  return String(str)
    .replace(/&/g, "&amp;")
    .replace(/</g, "&lt;")
    .replace(/>/g, "&gt;")
    .replace(/"/g, "&quot;")
    .replace(/'/g, "&#39;");
}

// Render basic markdown safely (compatible with all browsers)
function renderMarkdown(rawText) {
  const safe = escapeHTML(rawText);
  const lines = safe.split("\n");
  let html = "";
  let inUl = false;
  let inOl = false;
  let inTable = false;

  const formatInline = function (text) {
    return text
      .replace(/`([^`]+)`/g, "<code>$1</code>")
      .replace(/\*\*([^*]+)\*\*/g, "<strong>$1</strong>")
      .replace(/\*([^*]+)\*/g, "<em>$1</em>");
  };

  for (let i = 0; i < lines.length; i++) {
    let line = lines[i].replace(/\s+$/, "");
    let trimmedLine = line.trim();

    // Table detection
    if (trimmedLine.charAt(0) === "|" && trimmedLine.charAt(trimmedLine.length - 1) === "|") {
      if (inUl) { html += "</ul>"; inUl = false; }
      if (inOl) { html += "</ol>"; inOl = false; }
      const cells = trimmedLine.slice(1, -1).split("|").map(function (c) { return c.trim(); });
      const isSeparator = cells.every(function (c) { return /^[-:]+$/.test(c); });
      if (isSeparator) continue;
      if (!inTable) {
        html += "<table><thead><tr>" + cells.map(function (c) { return "<th>" + formatInline(c) + "</th>"; }).join("") + "</tr></thead><tbody>";
        inTable = true;
      } else {
        html += "<tr>" + cells.map(function (c) { return "<td>" + formatInline(c) + "</td>"; }).join("") + "</tr>";
      }
      continue;
    } else if (inTable) {
      html += "</tbody></table>";
      inTable = false;
    }

    // Headings
    if (/^###\s+(.+)/.test(line)) {
      if (inUl) { html += "</ul>"; inUl = false; }
      if (inOl) { html += "</ol>"; inOl = false; }
      html += "<h3>" + formatInline(line.replace(/^###\s+/, "")) + "</h3>";
      continue;
    }
    if (/^##\s+(.+)/.test(line)) {
      if (inUl) { html += "</ul>"; inUl = false; }
      if (inOl) { html += "</ol>"; inOl = false; }
      html += "<h2>" + formatInline(line.replace(/^##\s+/, "")) + "</h2>";
      continue;
    }

    // Bullet list
    if (/^[-*]\s+(.+)/.test(trimmedLine)) {
      if (inOl) { html += "</ol>"; inOl = false; }
      if (!inUl) { html += "<ul>"; inUl = true; }
      html += "<li>" + formatInline(trimmedLine.replace(/^[-*]\s+/, "")) + "</li>";
      continue;
    }

    // Numbered list
    if (/^\d+\.\s+(.+)/.test(trimmedLine)) {
      if (inUl) { html += "</ul>"; inUl = false; }
      if (!inOl) { html += "<ol>"; inOl = true; }
      html += "<li>" + formatInline(trimmedLine.replace(/^\d+\.\s+/, "")) + "</li>";
      continue;
    }

    if (inUl) { html += "</ul>"; inUl = false; }
    if (inOl) { html += "</ol>"; inOl = false; }

    if (trimmedLine === "") {
      html += "<br>";
    } else {
      html += "<div>" + formatInline(line) + "</div>";
    }
  }

  if (inUl) html += "</ul>";
  if (inOl) html += "</ol>";
  if (inTable) html += "</tbody></table>";
  return html;
}

function setStatus(state, text) {
  elStatusDot.className = "status-dot " + (state || "");
  elStatusText.textContent = text;
}

function getStudentContextPrefix() {
  const cls = document.getElementById("sel-class").value;
  const board = document.getElementById("sel-board").value;
  const subj = document.getElementById("sel-subject").value;
  const chap = document.getElementById("inp-chapter").value.trim() || "General Syllabus";
  const lang = document.getElementById("sel-lang").value;
  const mode = document.getElementById("sel-mode").value;
  return "[Student Settings — " + cls + " | Board: " + board + " | Subject: " + subj + " | Chapter: " + chap + " | Language Mode: " + lang + " | Learning Mode: " + mode + "]\n";
}

function appendMessageUI(role, text, isError, save) {
  if (isError === undefined) isError = false;
  if (save === undefined) save = true;

  const row = document.createElement("div");
  row.className = "msg-row " + role;

  const avatar = document.createElement("div");
  avatar.className = "avatar";
  avatar.textContent = role === "user" ? "🙂" : "🤖";

  const bubble = document.createElement("div");
  bubble.className = "bubble" + (isError ? " error-bubble" : "");

  const contentDiv = document.createElement("div");
  if (role === "assistant" && !isError) {
    contentDiv.innerHTML = renderMarkdown(text);
  } else {
    contentDiv.innerHTML = escapeHTML(text).replace(/\n/g, "<br>");
  }
  bubble.appendChild(contentDiv);

  // Add Copy, Read Aloud, and Simpler Explanation controls on AI messages
  if (role === "assistant") {
    const actions = document.createElement("div");
    actions.className = "msg-actions";

    const copyBtn = document.createElement("button");
    copyBtn.className = "action-btn";
    copyBtn.textContent = "📋 Copy";
    copyBtn.addEventListener("click", function () {
      copyTextSafe(text, function () {
        copyBtn.textContent = "✅ Copied!";
        setTimeout(function () { copyBtn.textContent = "📋 Copy"; }, 1500);
      });
    });

    const speakBtn = document.createElement("button");
    speakBtn.className = "action-btn";
    speakBtn.textContent = "🔊 Listen";
    speakBtn.addEventListener("click", function () {
      if (!("speechSynthesis" in window)) return;
      if (window.speechSynthesis.speaking) {
        window.speechSynthesis.cancel();
        speakBtn.textContent = "🔊 Listen";
        return;
      }
      const utter = new SpeechSynthesisUtterance(text.replace(/[*#`|]/g, ""));
      utter.lang = "en-IN";
      utter.onend = function () { speakBtn.textContent = "🔊 Listen"; };
      speakBtn.textContent = "⏹️ Stop";
      window.speechSynthesis.speak(utter);
    });

    const simplerBtn = document.createElement("button");
    simplerBtn.className = "action-btn";
    simplerBtn.textContent = "✨ Explain Simpler";
    simplerBtn.addEventListener("click", function () {
      sendUserMessage("Please explain your previous answer again in much simpler language with an everyday example and Hindi meaning of tough words.");
    });

    actions.appendChild(copyBtn);
    actions.appendChild(speakBtn);
    actions.appendChild(simplerBtn);
    bubble.appendChild(actions);
  }

  row.appendChild(avatar);
  row.appendChild(bubble);
  elMessagesList.appendChild(row);
  elChatScroll.scrollTop = elChatScroll.scrollHeight;

  if (save && !isError) {
    saveHistoryToStorage();
  }
}

function showWelcomeMessage() {
  let profile = {};
  try {
    profile = JSON.parse(localStorage.getItem(STORAGE_KEYS.PROFILE) || "{}");
  } catch (e) {}
  const studentName = profile && profile.name ? " " + profile.name : "";
  const welcomeText = "Namaste" + studentName + "! Welcome to **VIDYAVERSE AI** — *Your AI Teacher. Your Language. Your Future.*\n\nI am your personal study companion for **Class 8 & Class 9**. Here is how we can study together:\n- **📐 Maths Master:** Step-by-step problem solving, formulas, and mistake checking.\n- **🔬 Science Lab:** Physics, Chemistry & Biology with simple everyday examples.\n- **🌍 SST Explorer:** History timelines, Geography maps, and Civics real-life connections.\n- **✍️ Grammar Lab:** Tenses, Active/Passive voice, Reported speech, and writing rules.\n- **⚡ DUAL-EXPLAIN AI:** Ask in English, Hindi, or Hinglish—I will explain clearly while teaching you the exact English exam terms!\n\nTap one of the **starter questions** below or type any topic to begin!";
  appendMessageUI("assistant", welcomeText, false, false);
}

function saveHistoryToStorage() {
  try {
    localStorage.setItem(STORAGE_KEYS.HISTORY, JSON.stringify(history));
  } catch (e) {}
}

function loadHistoryFromStorage() {
  try {
    // Also remove old v1 history if present
    localStorage.removeItem("vidyaverse_chat_history_v1");
    const saved = JSON.parse(localStorage.getItem(STORAGE_KEYS.HISTORY) || "[]");
    if (Array.isArray(saved) && saved.length > 0) {
      history = saved;
      elMessagesList.innerHTML = "";
      history.forEach(function (m) {
        const displayUserText = m.role === "user"
          ? m.text.replace(/^\[Student Settings — [^\]]+\]\n/, "")
          : m.text;
        appendMessageUI(m.role, displayUserText, false, false);
      });
    } else {
      showWelcomeMessage();
    }
  } catch (e) {
    showWelcomeMessage();
  }
}

async function sendUserMessage(rawUserText) {
  const trimmed = String(rawUserText || "").trim();
  if (!trimmed || isWaiting) return;

  switchTab("view-chat");

  appendMessageUI("user", trimmed, false, false);
  elChatInput.value = "";

  // Check API Key before calling API
  if (!API_KEY || API_KEY.trim() === "" || API_KEY.trim() === "PASTE_YOUR_API_KEY_HERE") {
    appendMessageUI("assistant", "Paste your API key on line 6 of index.html, save, and refresh.", true, false);
    setStatus("error", "API Key Missing");
    return;
  }

  const fullPromptWithSettings = getStudentContextPrefix() + trimmed;
  history.push({ role: "user", text: fullPromptWithSettings });
  saveHistoryToStorage();

  isWaiting = true;
  elBtnSend.disabled = true;
  setStatus("thinking", "Thinking...");

  const typingRow = document.createElement("div");
  typingRow.className = "msg-row assistant";
  typingRow.innerHTML = '<div class="avatar">🤖</div><div class="bubble"><div class="typing-dots"><span></span><span></span><span></span></div></div>';
  elMessagesList.appendChild(typingRow);
  elChatScroll.scrollTop = elChatScroll.scrollHeight;

  try {
    const reply = await callAI(history);
    if (typingRow.parentNode) typingRow.parentNode.removeChild(typingRow);
    history.push({ role: "assistant", text: reply });
    appendMessageUI("assistant", reply, false, true);
    setStatus("", "Ready");
  } catch (err) {
    if (typingRow.parentNode) typingRow.parentNode.removeChild(typingRow);
    history.pop();
    saveHistoryToStorage();
    appendMessageUI("assistant", err.message || String(err), true, false);
    setStatus("error", "API Error");
  } finally {
    isWaiting = false;
    elBtnSend.disabled = false;
  }
}

// === NAVIGATION & TABS ===
function switchTab(targetId) {
  document.querySelectorAll(".nav-item").forEach(function (btn) {
    if (btn.getAttribute("data-target") === targetId) {
      btn.classList.add("active");
    } else {
      btn.classList.remove("active");
    }
  });
  document.querySelectorAll(".view-panel").forEach(function (panel) {
    if (panel.id === targetId) {
      panel.classList.add("active");
    } else {
      panel.classList.remove("active");
    }
  });
}

document.querySelectorAll(".nav-item").forEach(function (btn) {
  btn.addEventListener("click", function () {
    switchTab(btn.getAttribute("data-target"));
  });
});

// === SUBJECT CARDS SELECTION ===
document.querySelectorAll(".subject-card").forEach(function (card) {
  card.addEventListener("click", function () {
    document.querySelectorAll(".subject-card").forEach(function (c) {
      c.classList.remove("selected");
    });
    card.classList.add("selected");
    const subj = card.getAttribute("data-subj");
    document.getElementById("sel-subject").value = subj;
    elChatInput.placeholder = "Ask " + subj + " a question or paste a problem...";
    elChatInput.focus();
  });
});

// === CHAT INPUT & BUTTONS ===
elBtnSend.addEventListener("click", function () {
  sendUserMessage(elChatInput.value);
});

elChatInput.addEventListener("keydown", function (e) {
  if (e.key === "Enter" && !e.shiftKey) {
    e.preventDefault();
    sendUserMessage(elChatInput.value);
  }
});

// Suggested Starter Chips
document.querySelectorAll("#starter-chips .chip").forEach(function (chip) {
  chip.addEventListener("click", function () {
    sendUserMessage(chip.getAttribute("data-prompt"));
  });
});

// Smart AI Tutor Toolbar Buttons
document.querySelectorAll("[data-tutor]").forEach(function (btn) {
  btn.addEventListener("click", function () {
    const chap = document.getElementById("inp-chapter").value.trim();
    const subj = document.getElementById("sel-subject").value;
    const contextTopic = chap ? " (Topic: " + chap + " in " + subj + ")" : " (Subject: " + subj + ")";
    sendUserMessage(btn.getAttribute("data-tutor") + contextTopic);
  });
});

// Regenerate Last AI Reply
document.getElementById("btn-regenerate").addEventListener("click", function () {
  if (isWaiting || history.length === 0) return;
  if (history[history.length - 1].role === "assistant") {
    history.pop();
  }
  const lastUser = history.pop();
  if (!lastUser) return;
  const cleanText = lastUser.text.replace(/^\[Student Settings — [^\]]+\]\n/, "");
  sendUserMessage(cleanText);
});

// Clear Chat & New Chat Buttons
function clearConversation() {
  history = [];
  try {
    localStorage.removeItem(STORAGE_KEYS.HISTORY);
    localStorage.removeItem("vidyaverse_chat_history_v1");
  } catch (e) {}
  elMessagesList.innerHTML = "";
  showWelcomeMessage();
  setStatus("", "Chat Cleared");
}

document.getElementById("btn-clear-chat").addEventListener("click", clearConversation);
document.getElementById("btn-new-chat").addEventListener("click", clearConversation);

// Theme Toggle
try {
  const savedTheme = localStorage.getItem(STORAGE_KEYS.THEME);
  if (savedTheme === "light") document.body.classList.add("light-mode");
} catch (e) {}

document.getElementById("btn-theme-toggle").addEventListener("click", function () {
  document.body.classList.toggle("light-mode");
  try {
    localStorage.setItem(STORAGE_KEYS.THEME, document.body.classList.contains("light-mode") ? "light" : "dark");
  } catch (e) {}
});

// Web Speech API Microphone (en-IN)
const SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition;
const elBtnMic = document.getElementById("btn-mic");
if (!SpeechRecognition) {
  elBtnMic.style.display = "none";
} else {
  const recognition = new SpeechRecognition();
  recognition.lang = "en-IN";
  recognition.interimResults = false;

  elBtnMic.addEventListener("click", function () {
    try {
      recognition.start();
      elBtnMic.textContent = "🔴";
      setStatus("thinking", "Listening (en-IN)...");
    } catch (e) {
      recognition.stop();
    }
  });

  recognition.onresult = function (event) {
    const transcript = event.results[0][0].transcript;
    elChatInput.value = (elChatInput.value ? elChatInput.value + " " : "") + transcript;
    elChatInput.focus();
  };

  recognition.onend = function () {
    elBtnMic.textContent = "🎤";
    setStatus("", "Ready");
  };

  recognition.onerror = function () {
    elBtnMic.textContent = "🎤";
    setStatus("", "Ready");
  };
}

// === LEARN & DUAL-EXPLAIN STUDIO ACTIONS ===
document.getElementById("btn-run-dual").addEventListener("click", function () {
  const topic = document.getElementById("dual-topic").value.trim();
  const mode = document.getElementById("dual-mode").value;
  if (!topic) {
    alert("Please enter a topic or concept first.");
    return;
  }
  sendUserMessage('Use DUAL-EXPLAIN AI (' + mode + ') to teach the topic: "' + topic + '". Include Simple English, Easy Hindi explanation, key English technical terms with Hindi meanings, and an exam-ready summary.');
});

document.getElementById("btn-run-compare").addEventListener("click", function () {
  const a = document.getElementById("comp-a").value.trim();
  const b = document.getElementById("comp-b").value.trim();
  if (!a || !b) {
    alert("Please enter both concepts to compare.");
    return;
  }
  sendUserMessage('Compare "' + a + '" and "' + b + '" in a clear markdown table showing Similarities, Differences, Definitions, and Examples.');
});

document.getElementById("btn-run-check").addEventListener("click", function () {
  const q = document.getElementById("chk-question").value.trim();
  const att = document.getElementById("chk-attempt").value.trim();
  if (!q || !att) {
    alert("Please enter both the question and your answer attempt.");
    return;
  }
  sendUserMessage("Check My Answer!\nQuestion: " + q + "\nMy Attempt: " + att + "\nPlease check if my answer is right, kindly point out any mistake, explain why it happened, and show the correct step-by-step solution.");
});

// === DEDICATED TRANSLATION WORKSPACE ===
document.getElementById("btn-do-translate").addEventListener("click", async function () {
  const srcText = document.getElementById("trans-input").value.trim();
  const srcLang = document.getElementById("trans-src-lang").value;
  const tgtLang = document.getElementById("trans-tgt-lang").value;
  const outBox = document.getElementById("trans-output");

  if (!srcText) {
    outBox.value = "Please enter text to translate on the left.";
    return;
  }
  if (!API_KEY || API_KEY.trim() === "" || API_KEY.trim() === "PASTE_YOUR_API_KEY_HERE") {
    outBox.value = "Paste your API key on line 6 of index.html, save, and refresh.";
    return;
  }

  outBox.value = "Translating via VIDYAVERSE AI...";
  setStatus("thinking", "Translating...");
  try {
    const prompt = "Translate the following text from " + srcLang + " into " + tgtLang + ". Reply ONLY with the translation and key vocabulary meanings (do not output any HTML code):\n\n\"" + srcText + "\"";
    const reply = await callAI([{ role: "user", text: prompt }]);
    outBox.value = reply;
    setStatus("", "Ready");
  } catch (err) {
    outBox.value = err.message || String(err);
    setStatus("error", "Translation Error");
  }
});

document.getElementById("btn-copy-translation").addEventListener("click", function () {
  const outBox = document.getElementById("trans-output");
  if (!outBox.value) return;
  copyTextSafe(outBox.value);
});

// === ADAPTIVE QUIZ ENGINE ===
const BUILTIN_QUIZ_BANK = [
  {
    id: 1,
    type: "MCQ",
    subject: "Mathematics",
    q: "If 3x - 7 = 11, what is the value of x?",
    options: ["4", "6", "5", "8"],
    answer: "6",
    explanation: "Add 7 to both sides: 3x = 18. Divide by 3: x = 6.",
    topic: "Linear Equations"
  },
  {
    id: 2,
    type: "TF",
    subject: "Science",
    q: "True or False: Sound can travel through a vacuum (empty space).",
    options: ["True", "False"],
    answer: "False",
    explanation: "Sound is a mechanical wave and requires a material medium (solid, liquid, or gas) to travel.",
    topic: "Sound Waves"
  },
  {
    id: 3,
    type: "FIB",
    subject: "English Grammar",
    q: "Fill in the blank: Neither the teacher nor the students _____ present yesterday. (was / were)",
    options: ["was", "were"],
    answer: "were",
    explanation: "In 'Neither...nor' sentences, the verb agrees with the closer subject ('students' is plural, so 'were').",
    topic: "Subject-Verb Agreement"
  },
  {
    id: 4,
    type: "MCQ",
    subject: "Social Studies",
    q: "Which Fundamental Right in the Indian Constitution guarantees equality before the law?",
    options: ["Right to Freedom", "Right to Equality", "Right to Constitutional Remedies", "Cultural Rights"],
    answer: "Right to Equality",
    explanation: "Articles 14–18 of the Indian Constitution cover the Right to Equality.",
    topic: "Indian Constitution & Civics"
  }
];

function renderBuiltinQuiz() {
  const filter = document.getElementById("quiz-type-sel").value;
  const container = document.getElementById("quiz-container");
  const resBox = document.getElementById("quiz-results");
  resBox.style.display = "none";
  container.innerHTML = "";

  const questions = BUILTIN_QUIZ_BANK.filter(function (item) {
    return filter === "All" || item.type === filter;
  });

  questions.forEach(function (item, idx) {
    const card = document.createElement("div");
    card.className = "panel-card";
    card.style.marginBottom = "4px";
    const optsHtml = item.options.map(function (opt) {
      return '<label style="display:inline-flex; align-items:center; gap:6px; margin-right:14px; cursor:pointer; font-size:0.88rem;"><input type="radio" name="q_' + item.id + '" value="' + opt + '"> ' + opt + '</label>';
    }).join("");

    card.innerHTML = '<div style="font-size:0.75rem; color:var(--cyan); margin-bottom:4px;">Q' + (idx + 1) + ' • ' + item.subject + ' (' + item.type + ')</div><div style="font-weight:600; margin-bottom:8px;">' + escapeHTML(item.q) + '</div><div>' + optsHtml + '</div>';
    container.appendChild(card);
  });

  const submitBtn = document.createElement("button");
  submitBtn.className = "btn btn-primary";
  submitBtn.textContent = "✅ Submit Quiz & Check Score";
  submitBtn.addEventListener("click", function () {
    gradeQuiz(questions);
  });
  container.appendChild(submitBtn);
}

function gradeQuiz(questions) {
  let score = 0;
  let feedbackHtml = "";
  const weakTopics = [];

  questions.forEach(function (item, idx) {
    const selected = document.querySelector('input[name="q_' + item.id + '"]:checked');
    const userVal = selected ? selected.value : "Not Answered";
    const isCorrect = userVal === item.answer;
    if (isCorrect) {
      score++;
    } else {
      weakTopics.push(item.topic);
    }
    feedbackHtml += '<div style="margin-top:8px; padding:8px; border-left:3px solid ' + (isCorrect ? "var(--success)" : "var(--danger)") + '; background:rgba(0,0,0,0.2);"><strong>Q' + (idx + 1) + ':</strong> Your Answer: ' + escapeHTML(userVal) + ' ' + (isCorrect ? "✅" : "❌ (Correct: " + escapeHTML(item.answer) + ")") + '<br><span style="font-size:0.82rem; color:var(--text-muted);">Explanation: ' + escapeHTML(item.explanation) + '</span></div>';
  });

  const resBox = document.getElementById("quiz-results");
  resBox.style.display = "block";
  resBox.innerHTML = '<h3>🏆 Quiz Score: ' + score + ' / ' + questions.length + '</h3>' + (weakTopics.length > 0 ? '<p style="font-size:0.85rem; color:var(--warning); margin-bottom:8px;">Suggested Topics to Revise: <strong>' + weakTopics.join(", ") + '</strong></p>' : '<p style="font-size:0.85rem; color:var(--success);">Excellent job! You mastered all tested concepts!</p>') + feedbackHtml;
}

document.getElementById("btn-load-builtin-quiz").addEventListener("click", renderBuiltinQuiz);
document.getElementById("btn-ai-custom-quiz").addEventListener("click", function () {
  const qType = document.getElementById("quiz-type-sel").value;
  sendUserMessage("Generate an interactive 4-question practice quiz (" + qType + " style) for my selected Class, Subject, and Chapter. Ask me to attempt the answers first before revealing the solutions!");
});

// === QUICK REVISE BUTTONS ===
document.querySelectorAll("[data-revise]").forEach(function (btn) {
  btn.addEventListener("click", function () {
    sendUserMessage(btn.getAttribute("data-revise"));
  });
});

// === STUDY PLANNER & PROGRESS TRACKER ===
function renderPlanner() {
  const list = document.getElementById("plan-list");
  let tasks = [];
  try {
    tasks = JSON.parse(localStorage.getItem(STORAGE_KEYS.PLANNER) || "[]");
  } catch (e) {}
  list.innerHTML = "";
  tasks.forEach(function (t, i) {
    const li = document.createElement("li");
    li.style.cssText = "display:flex; justify-content:space-between; align-items:center; padding:6px 10px; background:var(--bg-panel); border-radius:6px; font-size:0.85rem;";
    li.innerHTML = '<span style="' + (t.done ? "text-decoration:line-through; color:var(--text-muted);" : "") + '">' + escapeHTML(t.text) + '</span><div style="display:flex; gap:6px;"><button class="action-btn" data-toggle="' + i + '">' + (t.done ? "Undo" : "✓ Done") + '</button><button class="action-btn" data-del="' + i + '">✕</button></div>';
    list.appendChild(li);
  });

  list.querySelectorAll("[data-toggle]").forEach(function (b) {
    b.addEventListener("click", function () {
      const idx = parseInt(b.getAttribute("data-toggle"), 10);
      tasks[idx].done = !tasks[idx].done;
      try { localStorage.setItem(STORAGE_KEYS.PLANNER, JSON.stringify(tasks)); } catch (e) {}
      renderPlanner();
    });
  });

  list.querySelectorAll("[data-del]").forEach(function (b) {
    b.addEventListener("click", function () {
      const idx = parseInt(b.getAttribute("data-del"), 10);
      tasks.splice(idx, 1);
      try { localStorage.setItem(STORAGE_KEYS.PLANNER, JSON.stringify(tasks)); } catch (e) {}
      renderPlanner();
    });
  });
}

document.getElementById("btn-add-plan").addEventListener("click", function () {
  const inp = document.getElementById("plan-task-inp");
  if (!inp.value.trim()) return;
  let tasks = [];
  try { tasks = JSON.parse(localStorage.getItem(STORAGE_KEYS.PLANNER) || "[]"); } catch (e) {}
  tasks.push({ text: inp.value.trim(), done: false });
  try { localStorage.setItem(STORAGE_KEYS.PLANNER, JSON.stringify(tasks)); } catch (e) {}
  inp.value = "";
  renderPlanner();
});

function renderTopicsLog() {
  const list = document.getElementById("topic-log-list");
  let topics = [];
  try {
    topics = JSON.parse(localStorage.getItem(STORAGE_KEYS.TOPICS) || "[]");
  } catch (e) {}
  list.innerHTML = "";

  const needsRev = topics.filter(function (t) { return t.status === "Needs Revision"; });
  const reminderBanner = document.getElementById("revision-reminder-banner");
  if (needsRev.length > 0) {
    reminderBanner.style.display = "block";
    document.getElementById("revision-reminder-text").textContent =
      "You have " + needsRev.length + " topic(s) marked for revision: " + needsRev.map(function (t) { return t.name; }).join(", ") + ". Click any topic to practice with AI!";
  } else {
    reminderBanner.style.display = "none";
  }

  topics.forEach(function (t, i) {
    const li = document.createElement("li");
    li.style.cssText = "display:flex; justify-content:space-between; align-items:center; padding:6px 10px; background:var(--bg-panel); border-radius:6px; font-size:0.85rem;";
    li.innerHTML = '<span><strong>' + escapeHTML(t.name) + '</strong> — <em style="color:' + (t.status === "Mastered" ? "var(--success)" : "var(--warning)") + '">' + escapeHTML(t.status) + '</em></span><div style="display:flex; gap:6px;"><button class="action-btn" data-revtopic="' + escapeHTML(t.name) + '">⚡ Revise Now</button><button class="action-btn" data-deltopic="' + i + '">✕</button></div>';
    list.appendChild(li);
  });

  list.querySelectorAll("[data-revtopic]").forEach(function (b) {
    b.addEventListener("click", function () {
      sendUserMessage('Help me revise the topic "' + b.getAttribute("data-revtopic") + '" with a short summary and 2 practice questions.');
    });
  });

  list.querySelectorAll("[data-deltopic]").forEach(function (b) {
    b.addEventListener("click", function () {
      const idx = parseInt(b.getAttribute("data-deltopic"), 10);
      topics.splice(idx, 1);
      try { localStorage.setItem(STORAGE_KEYS.TOPICS, JSON.stringify(topics)); } catch (e) {}
      renderTopicsLog();
    });
  });
}

document.getElementById("btn-add-topic").addEventListener("click", function () {
  const inp = document.getElementById("topic-log-inp");
  const status = document.getElementById("topic-status-sel").value;
  if (!inp.value.trim()) return;
  let topics = [];
  try { topics = JSON.parse(localStorage.getItem(STORAGE_KEYS.TOPICS) || "[]"); } catch (e) {}
  topics.push({ name: inp.value.trim(), status: status, date: new Date().toLocaleDateString() });
  try { localStorage.setItem(STORAGE_KEYS.TOPICS, JSON.stringify(topics)); } catch (e) {}
  inp.value = "";
  renderTopicsLog();
});

// === PROFILE MODAL & SETTINGS ===
const elModal = document.getElementById("welcome-modal");
document.getElementById("btn-welcome-setup").addEventListener("click", function () {
  elModal.classList.add("open");
});

document.getElementById("btn-save-profile").addEventListener("click", function () {
  const profile = {
    name: document.getElementById("mod-name").value.trim(),
    cls: document.getElementById("mod-class").value,
    board: document.getElementById("mod-board").value,
    lang: document.getElementById("mod-lang").value,
    goal: document.getElementById("mod-goal").value.trim()
  };
  try { localStorage.setItem(STORAGE_KEYS.PROFILE, JSON.stringify(profile)); } catch (e) {}
  document.getElementById("sel-class").value = profile.cls;
  document.getElementById("sel-board").value = profile.board;
  document.getElementById("sel-lang").value = profile.lang;
  elModal.classList.remove("open");
});

document.getElementById("chk-reduced-motion").addEventListener("change", function (e) {
  if (e.target.checked) {
    document.body.classList.add("reduced-motion");
  } else {
    document.body.classList.remove("reduced-motion");
  }
});

document.getElementById("btn-reset-all-data").addEventListener("click", function () {
  if (confirm("Are you sure you want to clear all saved chat history, planner goals, and profile settings?")) {
    try {
      localStorage.removeItem(STORAGE_KEYS.HISTORY);
      localStorage.removeItem("vidyaverse_chat_history_v1");
      localStorage.removeItem(STORAGE_KEYS.PROFILE);
      localStorage.removeItem(STORAGE_KEYS.PLANNER);
      localStorage.removeItem(STORAGE_KEYS.TOPICS);
      localStorage.removeItem(STORAGE_KEYS.THEME);
    } catch (e) {}
    location.reload();
  }
});

// Online/Offline feedback
window.addEventListener("offline", function () { setStatus("error", "Offline"); });
window.addEventListener("online", function () { setStatus("", "Online"); });

// === INITIALIZATION ON PAGE LOAD ===
window.addEventListener("DOMContentLoaded", function () {
  let savedProfile = null;
  try {
    savedProfile = JSON.parse(localStorage.getItem(STORAGE_KEYS.PROFILE) || "null");
  } catch (e) {}
  if (savedProfile) {
    document.getElementById("sel-class").value = savedProfile.cls || "Class 8";
    document.getElementById("sel-board").value = savedProfile.board || "CBSE (NCERT)";
    document.getElementById("sel-lang").value = savedProfile.lang || "Bilingual (Hindi + English)";
  } else {
    elModal.classList.add("open");
  }
  loadHistoryFromStorage();
  renderBuiltinQuiz();
  renderPlanner();
  renderTopicsLog();
});
</script>
</body>
</html>
