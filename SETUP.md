# Setup Guide — Insight.IO Dashboard

## Option 1: Python (Recommended — No install needed)
```bash
# Navigate to project folder
cd eric-robotics-insight

# Run server
python3 -m http.server 8080

# Open in browser
http://localhost:8080
```

## Option 2: Node.js
```bash
cd eric-robotics-insight
npx serve . -p 8080
# Open: http://localhost:8080
```

## Option 3: VS Code Live Server
1. Install "Live Server" extension in VS Code
2. Open the project folder
3. Right-click `index.html`
4. Select "Open with Live Server"

---
## Troubleshooting
- If port 8080 is busy: `python3 -m http.server 3000`
- Use Chrome or Firefox for best Three.js performance
- If map doesn't load: hard refresh with `Ctrl+Shift+R`
