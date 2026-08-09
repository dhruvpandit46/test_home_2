# 🏠 Oslune — Smart Home Control Panel

![HTML](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6-yellow?style=for-the-badge&logo=javascript)
![Cloud](https://img.shields.io/badge/Realtime-Cloud%20Sync-2ce09a?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

**Oslune** is a minimal, single-file smart home control panel for toggling a cloud-connected IoT device on and off. It polls a remote server in real time to stay in sync with the device's actual state — whether it was switched via the app, a physical button, or another client — and reflects that state through a glowing, glassmorphism-styled UI.

---

# 📑 Table of Contents

- Features
- Live Demo
- Technologies
- Project Structure
- How It Works
- Configuration
- Installation
- Future Improvements
- Contributing
- License
- Author

---

# ✨ Features

✅ One-Tap Power Toggle — a large animated switch to turn the connected device on/off

✅ ☁️ Real-Time Cloud Sync — polls the backend every 2 seconds to reflect the device's true state

✅ 🔄 Multi-Client Consistency — if the device is toggled elsewhere, this panel updates automatically

✅ 🎨 Reactive Glow Feedback — the card glows green when the device is on, red/orange when off

✅ 🧠 Busy-State Locking — prevents overlapping requests while a toggle is in flight

✅ 🪟 Glassmorphism UI — blurred dark dashboard card with a soft radial background

✅ Zero Backend Code in This Repo — pure frontend client that talks to a REST endpoint

✅ Single-File Simplicity — the entire app lives in one `index.html`, easy to read and deploy anywhere

---

# 🚀 Live Demo

https://dhruvpandit46.github.io/test_home_2/

---

# ⚙ Technologies Used

- HTML5
- CSS3 (glassmorphism, gradients, custom toggle switch, radial background)
- JavaScript (Vanilla, ES6, `fetch` API)
- Font Awesome (icons)
- Google Fonts (Inter)
- REST API polling for real-time device state

---

# 📂 Project Structure

```
test_home_2/
│
├── index.html
├── logo.png
└── README.md
```

---

# ⚡ How It Works

1. On load, the page fetches the device's current state from `GET /status` on the configured cloud server and reflects it in the toggle and status label (`on` / `off`).
2. Flipping the toggle sends a `POST /status` request with the new desired state (`{ "state": true|false }`).
3. The UI updates **optimistically** the moment you tap the switch, then reconciles with whatever the server confirms back.
4. A `busy` flag prevents sending a new request while one is still in flight, avoiding race conditions from rapid toggling.
5. The panel **auto-refreshes every 2 seconds**, polling `GET /status` so the switch and glow color always reflect the device's real, current state — even if it changed from somewhere else.
6. The card's box-shadow glows **green** when the device is on and **red/orange** when it's off, giving an at-a-glance status indicator.

---

# 🔧 Configuration

The cloud endpoint is defined at the top of the inline script in `index.html`:

```js
const SERVER = "https://iot.xiron.in";
```

The panel expects this server to expose:

| Endpoint | Method | Body | Response |
|---|---|---|---|
| `/status` | `GET` | — | `{ "state": true \| false }` |
| `/status` | `POST` | `{ "state": true \| false }` | `{ "state": true \| false }` |

To point this dashboard at your own backend, update the `SERVER` constant to your API's base URL. The device name shown in the UI (`ANIQUE`) can be changed directly in the `.device-name` element in `index.html`.

---

# 📦 Installation

Clone the repository

```bash
git clone https://github.com/dhruvpandit46/test_home_2.git
```

Go inside the project

```bash
cd test_home_2
```

Run

Simply open `index.html` in your browser. No build step, no dependencies — just make sure the `SERVER` endpoint in the script is reachable.

---

# 🎯 Future Improvements

- Support for multiple devices/rooms in one dashboard
- Authentication before allowing toggles
- Scheduling / timer-based automation
- Connection-lost indicator when the server is unreachable
- Historical on/off activity log
- Light/dark theme toggle

---

# 🤝 Contributing

Contributions are welcome.

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push your branch
5. Open a Pull Request

---

# 📜 License

Licensed under the **MIT License**.

MIT © 2026 Dhruv Pandit.

See the [LICENSE](LICENSE) file for full license details.

---

# 👨‍💻 Author

**Dhruv Pandit**

GitHub — https://github.com/dhruvpandit46

LinkedIn — https://linkedin.com/in/dhruv-pandit-755786326

Instagram — https://instagram.com/dhruv_pandit2007

---

# ⭐ Support

If you found this project useful, please consider giving it a ⭐ on GitHub.
It helps support future development.
