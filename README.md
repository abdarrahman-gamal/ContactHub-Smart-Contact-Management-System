# ContactHub

A simple, responsive address book that runs entirely in the browser. It stores contacts in `localStorage`, accepts Arabic and English names, validates Egyptian phone numbers, and lets you attach photos directly from your device.

[![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-F7DF1E?logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![Bootstrap](https://img.shields.io/badge/Bootstrap-5.3-7952B3?logo=bootstrap&logoColor=white)](https://getbootstrap.com/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
## Features

### Input validation
- **Names:** Supports both Arabic and Latin characters using `/^[A-Za-z\u0600-\u06FF\s]{2,50}$/`.
- **Phone numbers:** Matches Egyptian mobile prefixes (`010`, `011`, `012`, `015`). Handles local numbers (`010...`) as well as international formats (`+20...` or `0020...`), stripping hyphens and extra spaces before saving.
- **Alerts:** Uses SweetAlert2 modals for validation errors and delete prompts instead of native browser popups.

### Storage and media
- All data stays on your machine using `localStorage`.
- Contact IDs are generated with `Date.now()`.
- Uploaded profile images are converted into base64 strings via `FileReader` and saved straight into storage.
- Contacts without photos get assigned one of eight background colors based on their ID (`id % 8`), so their avatar color stays the same every time the list reloads.

### Search and quick shortcuts
- The search bar filters by name, phone number, and email at the same time.
- Clicking phone numbers or email addresses triggers native `tel:` and `mailto:` links.
- Contacts can be flagged as favorites or emergency contacts, pinning them to the side columns.

## Tech stack

| Layer | Tools |
| :--- | :--- |
| Frontend | Vanilla JavaScript (ES6+), HTML5 |
| UI & Layout | Bootstrap 5.3, custom CSS |
| Icons | FontAwesome 6 |
| Popups | SweetAlert2 |
| Persistence | Browser `localStorage` |

## Project structure

```text
ContactHub/
├── css/
│   ├── all.min.css           # FontAwesome
│   ├── bootstrap.min.css     # Bootstrap 5
│   └── style.css             # Custom styling and color themes
├── js/
│   ├── all.min.js             # FontAwesome script
│   ├── bootstrap.bundle.min.js# Bootstrap components
│   └── main.js               # Form handling, validation, and storage
├── img/                      # Icons and default assets
├── index.html                # App layout and modals
└── README.md
```
## Notes on implementation

- **Base64 photos:** Converting photos to base64 strings avoids needing a backend file server. Since `localStorage` is generally limited to around 5MB, keep uploaded images relatively small.
- **Deterministic avatar colors:** Deriving the avatar palette index from `contact.id % 8` prevents avatars from randomly changing color every time the UI re-renders.
- **Modal reuse:** Adding and editing contacts share the same Bootstrap modal (`#contactModal`). The form fields clear when closed so editing one contact does not carry over into the next.