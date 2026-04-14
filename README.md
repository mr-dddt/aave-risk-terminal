```
╔══════════════════════════════════════════════════════════════════════════════╗
║                                                                              ║
║      ██████╗  ██╗ ███████╗ ██╗  ██╗    ████████╗ ███████╗ ██████╗  ███╗    ║
║     ██╔══██╗ ██║ ██╔════╝ ██║ ██╔╝       ██╔══╝ ██╔════╝ ██╔══██╗ ████╗   ║
║     ██████╔╝ ██║ ███████╗ █████╔╝         ██║   █████╗   ██████╔╝ ██╔██╗  ║
║     ██╔══██╗ ██║ ╚════██║ ██╔═██╗         ██║   ██╔══╝   ██╔══██╗ ██║╚██╗ ║
║     ██║  ██║ ██║ ███████║ ██║  ██╗        ██║   ███████╗ ██║  ██║ ██║ ╚██╗║
║     ╚═╝  ╚═╝ ╚═╝ ╚══════╝ ╚═╝  ╚═╝        ╚═╝   ╚══════╝ ╚═╝  ╚═╝ ╚═╝  ╚═╝║
║                                                                              ║
║              A A V E   R I S K   T E R M I N A L   v 1 . 0                 ║
║                    S T A B L E C O I N   M O N I T O R                      ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

```
// SYSTEM SPECIFICATIONS ─────────────────────────────────────────────────────

  PROTOCOL  : Aave V3 + V4
  ASSETS    : USDC / USDT (side-by-side per chain)
  NETWORKS  : Ethereum · Arbitrum · Base · Polygon
  DATA SRC  : The Graph Protocol
  REFRESH   : 60s automatic + manual trigger [ REFRESH ]
  RUNTIME   : Single HTML file — zero build tools required
```

---

## // QUICK START

### [ DEMO MODE — no API key required ]

Open `index.html` directly in any browser. Realistic mock data loads automatically.

### [ LIVE DATA ]

**Step 1** — Get a Graph API key from https://thegraph.com/studio/

**Step 2** — Create your local config:

```bash
cp config.example.js config.js
cp .env.example .env
```

**Step 3** — Insert your key in `config.js`:

```js
window.GRAPH_API_KEY = 'your-key-here';
```

And in `.env`:

```
GRAPH_API_KEY=your-key-here
```

**Step 4** — Open in browser or serve locally:

```bash
# Option A — direct open
open index.html          # macOS
start index.html         # Windows
xdg-open index.html      # Linux

# Option B — local server (avoids font CORS issues)
python3 -m http.server 8080
# → http://localhost:8080
```

---

## // ADDING AAVE V4 SUBGRAPHS

V4 rows are pre-wired in the config but show as `SUBGRAPH NOT CONFIGURED` until you paste the endpoints.

**Step 1** — Find your subgraph IDs at https://thegraph.com/explorer  
Search: `aave v4 ethereum`, `aave v4 arbitrum`, etc.

**Step 2** — Open `index.html` and locate the `// Aave V4` section in `CHAINS`:

```js
{ id: 'ethereum-v4', name: 'ETHEREUM', ver: 'V4', abbr: 'ETH', col: '#627eea', chainId: 1,
  url: 'https://gateway.thegraph.com/api/YOUR_KEY/subgraphs/id/SUBGRAPH_ID' },
```

Replace `YOUR_KEY` and `SUBGRAPH_ID` for each chain. V4 rows will activate on next refresh.

---

## // RISK INDEX

```
■ LOW       Utilization < 70%                              [ GREEN  ]
■ MEDIUM    Utilization 70–85%                             [ AMBER  ]
■ HIGH      Utilization 85–92% or available liq < $10M    [ ORANGE ]
■ CRITICAL  Utilization > 92% or available liq < $5M      [ RED ██ ]
```

Risk badge per row shows the **worst** of USDC and USDT for that chain.  
The alert ticker at the top surfaces HIGH / CRITICAL pools in real time.

---

## // TABLE CONTROLS

```
[ CLICK HEADER ]   Sort ascending / descending by that column
[ REFRESH ]        Immediate data pull from all configured subgraphs
[ AUTO ]           Fires every 60 seconds in the background
```

Columns are sortable independently for USDC and USDT — click `USDC UTILIZATION`
to rank chains by USDC pressure, or `USDT AVAIL. LIQ` to find the tightest USDT pools.

---

## // FILE STRUCTURE

```
aave-risk-terminal/
├── index.html          Main application — open this in a browser
├── config.js           Your API key (gitignored — do not commit)
├── config.example.js   Template for config.js
├── .env                Server-side key reference (gitignored)
├── .env.example        Template for .env
├── .gitignore          Excludes config.js and .env from git
├── fonts/
│   ├── SpaceMono-Regular.ttf / .woff2
│   └── SpaceMono-Bold.ttf / .woff2
└── README.md           This file
```

---

## // DISCLAIMER

```
╔══════════════════════════════════════════════════════╗
║  NOT FINANCIAL ADVICE                                ║
║  FOR MONITORING AND INFORMATIONAL PURPOSES ONLY      ║
║  DATA MAY BE DELAYED — VERIFY BEFORE ACTING          ║
╚══════════════════════════════════════════════════════╝
```

---

```
────────────────────────────────────────────────────────────────────────────
  DATA: THE GRAPH PROTOCOL  //  PROTOCOL: AAVE  //  TERMINAL v1.0
────────────────────────────────────────────────────────────────────────────
```
