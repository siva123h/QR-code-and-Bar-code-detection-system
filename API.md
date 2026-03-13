# ScanVision — Component API Reference

---

## Components

### `<ScanVision />`

Root component. Manages global state and renders tabs.

No props required — self-contained.

---

### `<Header />`

Top navigation bar with logo and theme toggle.

| Prop | Type | Description |
|---|---|---|
| `theme` | `"dark" \| "light"` | Current theme |
| `toggleTheme` | `() => void` | Callback to switch theme |
| `styles` | `StylesObject` | Theme-derived style tokens |

---

### `<ScannerTab />`

Layout container for the Scanner page.

| Prop | Type | Description |
|---|---|---|
| `scans` | `Scan[]` | All scans in history |
| `latestResult` | `Scan \| null` | Most recent scan |
| `addScan` | `(data, type) => void` | Add a new scan entry |
| `clearHistory` | `() => void` | Clear all scans |
| `exportCSV` | `() => void` | Download history as CSV |
| `styles` | `StylesObject` | Theme style tokens |

---

### `<AnalyticsTab />`

Analytics page with stat cards and charts.

| Prop | Type | Description |
|---|---|---|
| `scans` | `Scan[]` | All scans for computing metrics |
| `styles` | `StylesObject` | Theme style tokens |

---

### `<LiveScanner />`

Webcam scanner using `getUserMedia` + jsQR frame analysis.

| Prop | Type | Description |
|---|---|---|
| `addScan` | `(data, type) => void` | Called on successful decode |
| `styles` | `StylesObject` | Theme style tokens |

---

### `<ImageUpload />`

Drag-and-drop / file picker image decoder.

| Prop | Type | Description |
|---|---|---|
| `addScan` | `(data, type) => void` | Called on successful decode |
| `styles` | `StylesObject` | Theme style tokens |

---

### `<LatestResult />`

Displays the most recently decoded scan.

| Prop | Type | Description |
|---|---|---|
| `result` | `Scan \| null` | Scan to display |
| `styles` | `StylesObject` | Theme style tokens |

---

### `<ScanHistory />`

Scrollable list of all scan entries.

| Prop | Type | Description |
|---|---|---|
| `scans` | `Scan[]` | Array of scan objects |
| `clearHistory` | `() => void` | Clears all scans |
| `exportCSV` | `() => void` | Downloads scan history |
| `styles` | `StylesObject` | Theme style tokens |

---

### `<Card />`

Reusable surface card wrapper.

| Prop | Type | Description |
|---|---|---|
| `children` | `ReactNode` | Card content |
| `styles` | `StylesObject` | Theme style tokens |
| `style` | `CSSProperties` | Optional override styles |

---

## Hooks

### `useTheme()`

Returns theme state and derived style tokens.

```js
const { theme, toggleTheme, styles } = useTheme();
```

**Returns:**

| Key | Type | Description |
|---|---|---|
| `theme` | `"dark" \| "light"` | Current theme name |
| `toggleTheme` | `() => void` | Toggle between dark and light |
| `styles` | `StylesObject` | Object with bg, surface, border, text colors |

---

### `useScanHistory()`

Manages scan entries array.

```js
const { scans, latestResult, addScan, clearHistory, exportCSV } = useScanHistory();
```

**Returns:**

| Key | Type | Description |
|---|---|---|
| `scans` | `Scan[]` | All scans, newest first |
| `latestResult` | `Scan \| null` | Most recent scan |
| `addScan` | `(data, type) => Scan` | Add a new scan |
| `clearHistory` | `() => void` | Empty the history |
| `exportCSV` | `() => void` | Download as CSV |

---

## Types

### `Scan`

```ts
type Scan = {
  id: number;
  data: string;       // Decoded content (URL, text, etc.)
  type: string;       // "qr-code" | "image-scan" | "barcode"
  timestamp: number;  // Unix ms
};
```

### `StylesObject`

```ts
type StylesObject = {
  bg: string;
  surface: string;
  surface2: string;
  border: string;
  textPrimary: string;
  textSecondary: string;
  textMuted: string;
};
```

---

## Utils

### `formatters.js`

| Function | Signature | Description |
|---|---|---|
| `formatDateTime` | `(timestamp: number) => string` | e.g. "Mar 13, 08:47 PM" |
| `formatShort` | `(timestamp: number) => string` | Same as above (alias) |
| `last7Days` | `() => string[]` | Returns array of last 7 weekday abbreviations |
