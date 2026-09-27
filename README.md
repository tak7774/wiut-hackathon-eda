# T-book — Fashion Reserve Platform
## Real App: Python + Flask + SQLite

### How to Run

1. **Install Python 3** (3.8+ required)
2. **Install Flask:**
   ```
   pip install flask
   ```
3. **Run the app:**
   ```
   python app.py
   ```
4. **Open in browser:**
   ```
   http://localhost:5000
   ```

---

### Project Structure
```
tbook_app/
├── app.py          ← Python Flask backend + SQLite DB logic
├── tbook.db        ← SQLite database (auto-created on first run)
├── static/
│   ├── index.html  ← App shell HTML
│   ├── app.css     ← Full dark-mode app stylesheet
│   ├── app.js      ← Frontend logic (API calls, UI)
│   └── logos.js    ← Brand logos (base64 embedded)
└── README.md
```

---

### Features
- **6 brands** · **36 stores** · **432 products** in SQLite
- **Real-time search** — products + stores via `/api/search`
- **Sidebar navigation** — Dashboard, Stores, Search, Reservations
- **Cart system** — add/remove products, floating cart panel
- **Reservation API** — 2% fee, 14-day limit, auto-cancel logic
- **Dark mode UI** — app-style layout with sidebar + topbar
- **Category filters** — filter products per store by category

---

### API Endpoints
| Method | Path | Description |
|--------|------|-------------|
| GET | /api/brands | All brands with store/product counts |
| GET | /api/stores?brand=X | Stores for a brand |
| GET | /api/products?store=X | Products for a store |
| GET | /api/search?q=X | Search products + stores |
| GET | /api/categories | All categories |
| POST | /api/reserve | Create reservation |
| GET | /api/reservations | All reservations |
| GET | /api/stats | Platform stats |

### Reservation Rules
- Fee = 2% of product price (charged immediately)
- Max duration = 14 days (enforced by server)
- If >3 days: max 2 products per reservation
- Status auto-updates to "cancelled" after expiry
