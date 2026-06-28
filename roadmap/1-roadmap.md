```markdown
📦 MVP_LangGraph_Project
 ┃
 ┣━━ 🛠️ Part 1: Environment & Dependency Setup
 ┃    ┃
 ┃    ┣━━ 📝 Task 1.1: Setup virtual environment (venv / conda) [cite: 72]
 ┃    ┣━━ 📦 Task 1.2: Install dependencies utama (`langgraph`, `langchain-core`) [cite: 73]
 ┃    ┗━━ 🔑 Task 1.3: Install LLM SDK (`langchain-google-genai` / `langchain-openai`) & setup API Key [cite: 74]
 ┃
 ┣━━ 🗃️ Part 2: State Definition (Data Contract) [cite: 75]
 ┃    ┃
 ┃    ┣━━ 📥 Task 2.1: Import `TypedDict` dari modul `typing` [cite: 77]
 ┃    ┣━━ 🏗️ Task 2.2: Buat class `AgentState` [cite: 77]
 ┃    ┗━━ 📊 Task 2.3: Tentukan fields wajib (`task`, `draft`, `critique`, `revision_count`) [cite: 78]
 ┃
 ┣━━ ⚙️ Part 3: Nodes Implementation (The Workers) [cite: 79]
 ┃    ┃
 ┃    ┣━━ ✍️ Task 3.1: Buat `writer_node` (Membaca task/critique, generate/revisi draf, increment counter) [cite: 81]
 ┃    ┗━━ 🔍 Task 3.2: Buat `critic_node` (Evaluasi draf, beri feedback kritik / status "APPROVED") [cite: 82]
 ┃
 ┣━━ 🔄 Part 4: Graph Construction & Routing (The Brain) [cite: 83]
 ┃    ┃
 ┃    ┣━━ 🗺️ Task 4.1: Inisialisasi graf menggunakan `StateGraph(AgentState)` [cite: 84]
 ┃    ┣━━ 📌 Task 4.2: Daftarkan `writer` & `critic` node menggunakan `.add_node()` [cite: 85]
 ┃    ┣━━ 🚀 Task 4.3: Tentukan titik mulai graf menggunakan `.set_entry_point("writer")` [cite: 86]
 ┃    ┣━━ 🔀 Task 4.4: Buat fungsi conditional routing (`route_after_critic`) untuk cek status critique [cite: 87]
 ┃    ┗━━ 🔗 Task 4.5: Hubungkan antar-node pakai `.add_edge()` dan `.add_conditional_edges()` [cite: 88]
 ┃
 ┣━━ 🔒 Part 5: Compilation (The App) [cite: 89]
 ┃    ┃
 ┃    ┗━━ ⚙️ Task 5.1: Mengunci arsitektur graf dengan memanggil fungsi `.compile()` [cite: 90]
 ┃
 ┗━━ 🚀 Part 6: Execution & Testing [cite: 91]
      ┃
      ┣━━ 📥 Task 6.1: Siapkan payload `initial_input` dictionary (berisi tugas awal) [cite: 92]
      ┣━━ 🏃 Task 6.2: Jalankan aplikasi menggunakan `.invoke(initial_input)` [cite: 93]
      ┗━━ 🖥️ Task 6.3: Cetak (`print`) hasil akhir dan pantau perubahan state tiap perulangan [cite: 94]

```