# 📇 ContactHub — Smart Contact Management System

[![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-F7DF1E?logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![Bootstrap](https://img.shields.io/badge/Bootstrap-5.3-7952B3?logo=bootstrap&logoColor=white)](https://getbootstrap.com/)
[![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/CSS)
[![Storage](https://img.shields.io/badge/Storage-LocalStorage-blue)](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

> A modern, responsive, client-side Contact Management Application engineered with Vanilla JavaScript (ES6+), Bootstrap 5, and custom CSS design systems. Built with an offline-first architecture, strict input validation pipelines, and instant multi-criteria search capabilities.

---

## 📸 Preview

```
┌────────────────────────────────────────────────────────────────────────┐
│  [+] Add Contact    Total: 24   ★ Favorites: 6   ♥ Emergency: 2       │
├──────────────────────────────────────┬─────────────────────────────────┤
│  🔍 Search by name, phone, email...  │  ★ Quick Favorites              │
│                                      │    • John Doe (01012345678) [📞]│
│  ┌────────────────┐ ┌────────────────┐│                                │
│  │ 👤 Ahmed Gamal │ │ 👤 Sarah Nabil ││  ♥ Emergency Contacts           │
│  │ 📞 010...      │ │ 📞 012...      ││    • Mom (01187654321)      [📞]│
│  │ [Work] [★] [♥] │ │ [Family] [★]   ││                                │
│  └────────────────┘ └────────────────┘│                                │
└──────────────────────────────────────┴─────────────────────────────────┘
```
*(Add a high-resolution screenshot or animated GIF of your application here)*

---

## ⚡ Key Engineering Highlights

### 1. Robust Data Validation Pipeline
- **Regex-Driven Sanitization:** Inputs are checked against strict regular expressions before state updates:
  - **Full Name:** Unicode-aware regex `/^[A-Za-z\u0600-\u06FF\s]{2,50}$/` supporting both Latin and Arabic alphabets.
  - **Phone Format:** Egyptian Telecom standard compliance `/^(01[0125]\d{8}|(?:\+20|0020)1[0125]\d{8})$/` with automatic sanitization of hyphens and whitespace.
  - **RFC-Compliant Email:** Structural validation for clean contact distribution.
- **Fail-Safe UI Feedback:** Graceful fallback alerts utilizing **SweetAlert2** modals without disruptive browser refreshes.

### 2. Client-Side State Management & Persistence
- Complete **CRUD Lifecycle** (Create, Read, Update, Delete) decoupled from backend dependencies.
- **Offline-First Persistence:** Synchronized with the browser's `localStorage` engine, ensuring zero data loss across user sessions.
- **Normalized Data Model:** Unique deterministic timestamps (`Date.now()`) as record keys preventing collisions during concurrent mutations.

### 3. Real-Time Multi-Attribute Query Engine
- Dynamic debounced filtering executing over `name`, `phone`, and `email` properties simultaneously.
- High-performance DOM reconciliation that selectively renders contact cards without re-parsing unaffected elements.

### 4. Asynchronous Media Handling (FileReader API)
- Client-side image ingestion via the native HTML5 `FileReader` API.
- Converts uploaded profile photos to base64 `DataURL` format for seamless persistence inside `localStorage`.
- **Dynamic Avatar Fallback Engine:** Algorithmic color assignment `(contact.id % 8) + 1` producing consistent brand gradients for contacts without uploaded avatars.

### 5. Instant Action Routing
- **Direct Protocol Integration:** Native `tel:${phone}` and `mailto:${email}` hooks enabling 1-click calls and dispatching emails directly from the dashboard.
- **Emergency & Priority Toggles:** Real-time segregation into dedicated "Favorites" and "Emergency" sidebars for rapid triage.

---

## 🛠️ Tech Stack & Architecture

| Layer | Technologies |
| :--- | :--- |
| **Frontend Core** | Vanilla JavaScript (ES6+), HTML5 Semantic Elements |
| **Styling & Grid** | Bootstrap 5.3, Custom CSS Variables & Glassmorphism Design System |
| **Icons & Assets** | FontAwesome 6 (Solid & Regular icon packs) |
| **Notifications** | SweetAlert2 |
| **Storage Engine** | Browser Storage API (`Window.localStorage`) |
| **Media Engine** | HTML5 `FileReader` API |

---

## 📂 Project Architecture

```
ContactHub/
├── css/
│   ├── all.min.css           # FontAwesome icon library
│   ├── bootstrap.min.css     # Bootstrap 5 core framework
│   └── style.css             # Custom design system, badges & glow layers
├── js/
│   ├── all.min.js             # FontAwesome runtime
│   ├── bootstrap.bundle.min.js# Bootstrap components bundle
│   └── main.js               # Application logic, state & DOM manipulation
├── img/                      # Static image assets & icons
├── index.html                # Semantic single-page application layout
└── README.md                 # Technical project documentation
```

---

## 🚀 Getting Started

No build tools, bundlers, or package installations required.

### Prerequisites
A modern web browser (Chrome, Firefox, Safari, Edge).

### Installation & Run

1. **Clone the repository:**
   ```bash
   git clone https://github.com/<your-username>/ContactHub.git
   cd ContactHub
   ```

2. **Launch the application:**
   - Double-click `index.html` to open directly in your default browser, or
   - Use VS Code **Live Server** extension:
     ```bash
     # If using live-server CLI
     npx live-server
     ```

---

## 🧩 Architectural Decisions & Lessons Learned

- **Modal vs Alert Architecture:** Transitioned from heavy alert popups to native semantic modal forms (`#contactModal`) with background backdrop blur for a streamlined data-entry experience. SweetAlert2 was retained strictly for non-blocking confirmation dialogs and validation errors.
- **Deterministic Color Hashing:** Avoided random avatar background colors on render by deriving the gradient index deterministically from the entity's unique ID (`id % 8 + 1`), preserving visual consistency across re-renders.
- **Single Source of Truth:** Centralized state in an in-memory `contacts` array with a single synchronization gateway (`saveContacts()`) to guarantee synchronization between memory and persistent storage.

---

## 👨‍💻 Author

**Abdarrahman Gamal**
- GitHub: [@your-username](https://github.com/)
- LinkedIn: [linkedin.com/in/your-profile](https://linkedin.com/)

---

## 📄 License

This project is licensed under the [MIT License](LICENSE) — feel free to use and adapt this code for your portfolio or applications.
