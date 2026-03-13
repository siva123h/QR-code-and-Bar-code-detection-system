# ScanVision — Usage Guide

## Starting the App

```bash
npm install
npm run dev
```

Navigate to `http://localhost:5173`.

---

## Scanner Tab

### Live Webcam Scanner

1. Click **Start Scanner** — your browser will request camera permission
2. Grant permission when prompted
3. Hold a QR code in front of the camera
4. The app decodes it automatically, stops the scanner, and shows the result
5. Click **Start Scanner** again for another scan

> **Tip:** Use good lighting and hold the code steady for faster detection.

### Image Upload

1. Drag and drop an image onto the upload zone, **or** click **Choose File**
2. The app reads the image, runs jsQR on it, and displays the decoded result
3. Supported formats: PNG, JPG, GIF, WebP

### Latest Result

- Shows the most recently decoded value
- Includes a **type badge** (`qr-code`, `image-scan`, etc.) and timestamp
- The text box is scrollable for long URLs

### Scan History

- All scans are listed newest-first
- Click the **download icon** to export the full history as `scan-history.csv`
- Click the **trash icon** to clear all history

### Demo Mode

Click **Simulate a scan (demo)** to add a fake scan entry — useful for testing the analytics charts without a real camera or image.

---

## Analytics Tab

| Widget | Description |
|---|---|
| Total Scans | Count of all scans this session |
| Today | Scans made on today's date |
| Types | Number of unique code type labels detected |
| Scans Per Day | Bar chart covering the last 7 days |
| Code Types | Donut chart showing breakdown by type |

---

## Theme Toggle

Click the **sun / moon icon** in the top-right corner to switch between dark mode and light mode.

---

## Exporting Data

In the Scan History panel, click the download icon. A file named `scan-history.csv` is saved with columns:

```
type, data, timestamp
```

---

## Keyboard & Accessibility

- All buttons are keyboard-focusable
- The upload zone responds to drag-over events with a teal border highlight
- The video element uses `playsInline` and `muted` for mobile compatibility
