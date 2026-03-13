# ScanVision

**Smart Barcode & QR Code Detection Web App**

ScanVision is a real-time barcode and QR code detection application built with React. It supports live webcam scanning, image upload decoding, scan history, CSV export, and an analytics dashboard with charts.

---

## Project Structure

```
ScanVision/
├── src/
│   ├── main.jsx                  # App entry point
│   ├── App.jsx                   # Root component
│   ├── index.css                 # Global styles
│   ├── components/
│   │   ├── ScanVision.jsx        # Main layout & tab controller
│   │   ├── Header.jsx            # Top navigation bar
│   │   ├── ScannerTab.jsx        # Scanner page layout
│   │   ├── AnalyticsTab.jsx      # Analytics page with charts
│   │   ├── LiveScanner.jsx       # Webcam scanner component
│   │   ├── ImageUpload.jsx       # Drag-and-drop image upload
│   │   ├── LatestResult.jsx      # Latest decoded result panel
│   │   ├── ScanHistory.jsx       # Scrollable scan history list
│   │   ├── Card.jsx              # Reusable card wrapper
│   │   └── Icons.jsx             # All SVG icons
│   ├── hooks/
│   │   ├── useTheme.js           # Dark/light theme hook
│   │   └── useScanHistory.js     # Scan state management hook
│   └── utils/
│       └── formatters.js         # Date/time formatters & helpers
├── docs/
│   ├── USAGE.md                  # User guide
│   └── API.md                    # Component API reference
├── index.html                    # HTML entry point (loads jsQR from CDN)
├── package.json                  # Node dependencies & scripts
├── vite.config.js                # Vite build configuration
├── requirements.txt              # Python dependencies (optional backend)
├── architecture.png              # System architecture diagram
└── README.md                     # This file
```

---

## Features

- **Live webcam scanner** — Start your camera and point at any QR code for instant decode
- **Image upload** — Drag-and-drop or browse to upload an image containing a barcode or QR code
- **Real-time decode** — Uses [jsQR](https://github.com/cozmo/jsQR) for client-side QR decoding (no server required)
- **Scan history** — All decoded results stored in session with timestamps and type badges
- **CSV export** — Download full scan history as a `.csv` file
- **Analytics dashboard** — Bar chart (scans per day) and donut chart (code types)
- **Dark / light theme** — Toggle with the sun/moon icon in the header
- **Demo mode** — Simulate scans without a camera using the demo button

---

## Getting Started

### Prerequisites

- Node.js 18+
- npm or yarn

### Install & Run

```bash
# Clone or download the project
cd ScanVision

# Install dependencies
npm install

# Start development server
npm run dev
```

Open [http://localhost:5173](http://localhost:5173) in your browser.

### Build for Production

```bash
npm run build
```

Output is in the `dist/` folder — ready to deploy to Netlify, Vercel, or any static host.

---

## Usage

### Scanner Tab

1. Click **Start Scanner** to activate your webcam
2. Point the camera at a QR code — it decodes automatically and stops
3. Or use **Upload Image** to drag-and-drop an image file containing a code
4. The **Latest Result** panel shows the decoded text and scan type
5. **Scan History** lists all scans with timestamps; use the download icon to export CSV

### Analytics Tab

- **Total Scans** — all-time count
- **Today** — scans made today
- **Types** — number of unique code types detected
- **Scans Per Day** bar chart — last 7 days
- **Code Types** donut chart — distribution by type

---

## Tech Stack

| Layer | Technology |
|---|---|
| UI framework | React 18 |
| Build tool | Vite 5 |
| Charts | Recharts |
| QR decoding | jsQR (CDN) |
| Styling | Inline styles + CSS variables |
| Python backend (optional) | Flask, OpenCV, Pyzbar |

---

## Architecture

See [`architecture.png`](./architecture.png) for the full system diagram.

```
Browser
  └── React App (Vite)
        ├── ScanVision (root)
        │     ├── Header
        │     ├── Scanner Tab
        │     │     ├── LiveScanner  ──► getUserMedia API ──► jsQR decode
        │     │     ├── ImageUpload  ──► FileReader API  ──► jsQR decode
        │     │     ├── LatestResult
        │     │     └── ScanHistory
        │     └── Analytics Tab
        │           ├── Stat Cards
        │           ├── Bar Chart (Recharts)
        │           └── Donut Chart (Recharts)
        └── Hooks
              ├── useTheme
              └── useScanHistory
```

---

## Optional Python Backend

If you want server-side decoding (for barcodes that jsQR can't handle):

```bash
pip install -r requirements.txt
python app.py
```

The Flask server exposes a `/decode` endpoint that accepts an image and returns decoded results using OpenCV + Pyzbar.

---

## Team

| Name | Roll Number |
|---|---|
| PRATIKSHA L | 2023LCSE07AED667 |
| SIRIPIREDDY VGNAI | 2023BCSE07AED335 |
| KOMMIRI SIVA | 2023BCSE07AED371 |

**Mentor:** Dr. VARTIKA MISHRA
**Course:** 5CS1990/5IT1990 Design Project – 1

---

## License

MIT License — free to use, modify, and distribute.
