# 🗺️ Roadmap & Goals: Elevasi MVP LangGraph ke Level Produksi

Dokumen ini menetapkan pelan tindakan, matlamat (*goals*), dan fasa pembangunan terperinci bagi menaik taraf skrip **MVP Writer-Critic** tunggal (`main.py`) yang sedia ada menjadi sebuah seni bina aplikasi ejen AI (*Agentic Application*) yang modular, selamat, dan sedia untuk persekitaran produksi.

---

## 🎯 Objektif Utama Sesi Ini (*The Goals*)

1. **Zero Hardcoding & Jaminan Keselamatan Data**
   - Mengasingkan semua kredensial sensitif (`GOOGLE_API_KEY`) ke dalam fail konfigurasi persekitaran `.env`.
   - Menggantikan struktur data longgar dengan pengesahan jenis (*type validation*) yang ketat untuk mengelakkan ralat masa jalanan (*runtime errors*).

2. **Pencegahan Gelung Infiniti (*Infinite-Loop Prevention*)**
   - Menyuntik mekanisme kawalan (*autonomous guardrails*) untuk mengehadkan pusingan kerja maksimum antara penulisan dan kritikan demi mengelakkan pembaziran token API.

3. **Seni Bina Kod Modular & Teragih**
   - Memecahkan fail tunggal `main.py` kepada beberapa modul mikro-servis tersendiri supaya sistem mudah diskalakan di masa hadapan (contoh: menambah ejen baru atau pangkalan data).

4. **Keterlihatan Masa Nyata (*Real-time Observability*)**
   - Mengubah mod pelaksanaan pasif kepada penstriman interaktif supaya sebarang perubahan status (*state updates*) dapat dipantau langkah-demi-langkah.

---

## 🗺️ Pelan Tindakan Pembangunan (*The Milestone Roadmap*)

Pembangunan ini dibahagi kepada tiga mileston utama yang dilaksanakan secara taktikal:

```
📦 MVP_LangGraph_Project (Lanjutan)
 ┣━━ 📍 MILESTONE 1: Pengukuhan Kod & Kawalan Automatik
 ┣━━ 📍 MILESTONE 2: Refactoring & Modularisasi Folder
 ┗━━ 📍 MILESTONE 3: Ciri Lanjutan & Penstriman Masa Nyata
```

### 📍 Milestone 1: Pengukuhan Kod Semasa & Kawalan Automatik (Fasa Segera)
Fasa fokus utama untuk membaiki skrip `main.py` sedia ada agar menjadi lebih stabil sebelum dipecahkan.

* **Task 1.1: Migrasi Skema Validasi `AgentState`**
    - Menggantikan kaedah `TypedDict` lama kepada model **Pydantic v2 Model**.
    - Memastikan setiap medan data (*fields*) mempunyai jenis data (*type*) dan nilai lalai (*default values*) yang jelas.
* **Task 1.2: Isolasi Kredensial Environment**
    - Mengintegrasikan library `python-dotenv`.
    - Memastikan tiada kunci API terdedah secara terus di dalam kod sumber semasa dihantar ke repositori Git.
* **Task 1.3: Suntikan Guardrail pada Conditional Routing**
    - Mengemas kini fungsi haluan `route_after_critic`.
    - Memaksa graf beralih ke penamat (`END`) secara automatik sekiranya bilangan semakan (`revision_count`) mencecah had maksimum (had dicadangkan: 3 kali).

### 📍 Milestone 2: Refactoring & Modularisasi Folder
Memotong fail tunggal yang padat kepada struktur folder mikro-servis yang bersih mengikut amalan terbaik pengkodan (*Clean Code*).

* **Struktur Folder Sasaran:**
    ```text
    📦 MVP_LangGraph_Project
     ┃
     ┣━━ 📂 src
     ┃   ┣━━ 📄 __init__.py
     ┃   ┣━━ 📄 state.py      # Kontrak data global (Pydantic AgentState)
     ┃   ┣━━ 📄 nodes.py      # Logika perniagaan ejen (writer_node & critic_node)
     ┃   ┗━━ 📄 graph.py      # Konfigurasi StateGraph, edges, & kompilasi (.compile)
     ┃
     ┣━━ 📄 .env              # Menyimpan API Keys (GOOGLE_API_KEY)
     ┣━━ 📄 .gitignore        # Mengabaikan .env daripada pengesanan git
     ┣━━ 📄 main.py           # Entry-point utama aplikasi untuk mencetuskan graf
     ┗━━ 📄 requirements.txt  # Fail senarai dependencies projek
    ```

### 📍 Milestone 3: Ciri Lanjutan & Penstriman Masa Nyata (Menuju Tahap Expert)
Menerapkan keupayaan lanjutan LangGraph untuk menguruskan sesi pengguna dan memantau prestasi ejen.

* **Task 3.1: State Persistence & Memory Saver**
    - Mengintegrasikan `MemorySaver` (In-memory checkpointer) bawaan asli LangGraph.
    - Membolehkan graf mempunyai memori jangka pendek dan menyokong *Thread ID* unik bagi setiap sesi sembang pengguna untuk jejak sejarah revisi lama.
* **Task 3.2: Implementasi Live Streaming Execution**
    - Mengubah pemanggilan kaedah `.invoke()` kepada generator dinamik `.stream()`.
    - Memisahkan log sistem dalaman dengan teks ouput yang sedang dijana oleh LLM demi pengalaman pengguna (*UX*) yang lebih lancar.

---

## 🛠️ Ringkasan Alur Tindakan & Matlamat Projek

| Fasa Kerja | Komponen Utama | Hasil Output Akhir | Status |
| :--- | :--- | :--- | :--- |
| **Milestone 1** | Pydantic v2, `python-dotenv`, Routing Guardrails | Fail `main.py` yang selamat dan kebal daripada masalah *Infinite Loop*. | 🔄 Dalam Proses |
| **Milestone 2** | Pemisahan Modular (`src/` folder) | Struktur projek standard industri yang sedia untuk diskalakan. | ⏳ Seterusnya |
| **Milestone 3** | Checkpointers (`MemorySaver`), `.stream()` | Ejen AI yang mempunyai memori berterusan dan output masa nyata. | ⏳ Akan Datang |

---
*Nota: Sentiasa pastikan persekitaran maya (virtual environment) anda diaktifkan semasa melakukan pemasangan dependencies baharu seperti `pydantic` dan `python-dotenv`.*