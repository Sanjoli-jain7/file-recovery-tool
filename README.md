<<<<<<< HEAD
# File System Recovery & Optimization Simulator

An interactive, educational full-stack web application that demonstrates OS-level file system concepts including virtual file systems, disk block allocation, crash simulation, journaling-based recovery, defragmentation, and real-time performance monitoring — all in a dark terminal aesthetic.

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Getting Started (Local — Windows)](#getting-started-local--windows)
- [API Reference](#api-reference)
- [Pages & Modules](#pages--modules)
- [Core Simulation Logic](#core-simulation-logic)
- [Deployment](#deployment)
- [Troubleshooting](#troubleshooting)

---

## Overview

This simulator lets users interact with a virtual file system running entirely in memory on the backend. Users can create and delete files, watch disk block allocation in real time, trigger crash events, recover corrupted/deleted files via journaling or backup methods, and run defragmentation or block reallocation to improve performance. Every action is logged and charted.

It is designed for educational use — particularly for students studying operating systems — to make abstract concepts like inodes, block bitmaps, fragmentation, and journaling tangible and interactive.

---

## Features

| Feature | Description |
|---|---|
| Virtual File System | Hierarchical directory tree with file/directory CRUD |
| Disk Block Visualization | 100-block bitmap grid showing used, free, and fragmented blocks |
| File Access Simulation | Sequential vs direct access with seek and transfer time metrics |
| Crash Simulation | Randomized corruption and deletion of files, simulating disk failure |
| File Recovery | Journal-based (75% success rate) and backup-based (65%) recovery modes |
| Defragmentation | Compacts all healthy files into contiguous blocks, reduces fragmentation |
| Block Reallocation | Reallocates multi-block files to reduce fragmentation with less disruption |
| Performance Charts | Line charts showing fragmentation score and average access time over time |
| Real-time Log Viewer | Filterable live activity and system journal log stream |
| Dashboard | Summary stats: file health, block usage, crash/recovery/optimization counts |
| Reset | Restores the entire filesystem to its initial state |

---

## Tech Stack

### Frontend (`artifacts/fs-simulator`)
- **React 19** — UI framework
- **Vite 7** — Dev server and bundler
- **TailwindCSS 4** — Utility-first styling
- **Recharts** — Performance history charts
- **Framer Motion** — Animated transitions
- **TanStack Query** — Server state and data fetching
- **Wouter** — Lightweight client-side routing
- **Radix UI** — Accessible component primitives
- **Lucide React** — Icon set

### Backend (`artifacts/api-server`)
- **Node.js + Express** — HTTP server
- **TypeScript** — Type-safe throughout
- **esbuild** — Fast TypeScript bundler
- **Pino** — Structured logging
- **UUID** — File/node identity generation

### Workspace
- **pnpm workspaces** — Monorepo package management
- **cross-env** — Cross-platform environment variables

---

## Project Structure

```
File-System-Explorer/
├── artifacts/
│   ├── api-server/                  # Express REST API (backend)
│   │   ├── src/
│   │   │   ├── index.ts             # Server entry point (PORT, listen)
│   │   │   ├── app.ts               # Express app setup, CORS, middleware
│   │   │   ├── lib/
│   │   │   │   └── filesystem.ts    # Core simulation engine (FilesystemManager)
│   │   │   └── routes/
│   │   │       ├── index.ts         # Route registration
│   │   │       ├── health.ts        # GET /api/health
│   │   │       ├── filesystem.ts    # File/directory CRUD + disk blocks
│   │   │       ├── crash.ts         # Crash and corrupt endpoints
│   │   │       ├── recovery.ts      # Recovery endpoints
│   │   │       ├── optimization.ts  # Defrag and reallocation endpoints
│   │   │       └── stats.ts         # Dashboard stats, logs, performance
│   │   ├── build.mjs                # esbuild script
│   │   └── package.json
│   │
│   └── fs-simulator/                # React + Vite frontend
│       ├── src/
│       │   ├── App.tsx              # Root app with router
│       │   ├── components/
│       │   │   ├── layout.tsx       # Sidebar navigation shell
│       │   │   └── ui/              # Radix UI component library
│       │   └── pages/
│       │       ├── dashboard.tsx    # Stats overview
│       │       ├── filesystem.tsx   # File tree + disk block grid
│       │       ├── access.tsx       # Access simulation
│       │       ├── crash.tsx        # Crash simulation controls
│       │       ├── recovery.tsx     # Recovery controls and results
│       │       ├── optimization.tsx # Defrag/realloc controls + charts
│       │       ├── logs.tsx         # Live log viewer
│       │       └── not-found.tsx    # 404
│       ├── vite.config.ts
│       └── package.json
│
├── lib/
│   └── api-spec/
│       └── openapi.yaml             # OpenAPI 3.0 contract (source of truth)
│
├── pnpm-workspace.yaml              # Workspace config + platform overrides
├── package.json                     # Root scripts
└── README.md
=======
# 🚀 File Recovery Tool

A full-stack file recovery tool built with:

* ⚙️ Flask (Backend)
* 🎨 React + Tailwind (Frontend)
* 🧠 PhotoRec (Recovery Engine)

---

## 📦 Features

* Recover deleted files
* Simple UI to start recovery
* Works locally on your machine
* Supports multiple file types

---

## ⚙️ Setup Instructions

### 🔹 1. Clone the repository

```
git clone https://github.com/Saksham-2006/file-recovery-tool.git
cd file-recovery-tool
>>>>>>> 03fbfc36de705870b8a798a58dbbf0a85ba800fd
```

---

<<<<<<< HEAD
## Getting Started (Local — Windows)

### Prerequisites

- **Node.js** v18 or higher — [nodejs.org](https://nodejs.org)
- **pnpm** — Install with: `npm install -g pnpm`

### 1. Download the project

Download the zip from Replit (three dots → Download as zip) and extract it.

### 2. Fix Windows platform overrides

Open `pnpm-workspace.yaml` and delete these lines (they block Windows native binaries):

```yaml
  "esbuild>@esbuild/win32-arm64": "-"
  "esbuild>@esbuild/win32-ia32": "-"
  "esbuild>@esbuild/win32-x64": "-"
  "lightningcss>lightningcss-win32-arm64-msvc": "-"
  "lightningcss>lightningcss-win32-x64-msvc": "-"
  "@tailwindcss/oxide>@tailwindcss/oxide-win32-arm64-msvc": "-"
  "@tailwindcss/oxide>@tailwindcss/oxide-win32-x64-msvc": "-"
  "rollup>@rollup/rollup-win32-arm64-msvc": "-"
  "rollup>@rollup/rollup-win32-ia32-msvc": "-"
  "rollup>@rollup/rollup-win32-x64-gnu": "-"
  "rollup>@rollup/rollup-win32-x64-msvc": "-"
```

### 3. Install dependencies

Open PowerShell or VS Code terminal in the project folder:

```powershell
pnpm install
```

### 4. Start the backend (Terminal 1)

```powershell
pnpm --filter @workspace/api-server run dev
```

Wait for: `Server listening port: 8080`

### 5. Start the frontend (Terminal 2)

```powershell
pnpm --filter @workspace/fs-simulator run dev
```

Wait for: `VITE ready`

### 6. Open in browser

```
http://localhost:5173
```

---

## API Reference

All endpoints are prefixed with `/api`. The backend runs on port `8080`.

| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/health` | Server health check |
| GET | `/api/filesystem` | Get full filesystem tree + block stats |
| GET | `/api/filesystem/blocks` | Get disk block bitmap and block map |
| POST | `/api/filesystem/files` | Create a new file or directory |
| DELETE | `/api/filesystem/files/:id` | Delete a file or directory |
| POST | `/api/filesystem/access` | Simulate file access (read/write, sequential/direct) |
| POST | `/api/filesystem/reset` | Reset filesystem to initial state |
| POST | `/api/crash/simulate` | Trigger a random disk crash event |
| POST | `/api/crash/corrupt/:id` | Manually corrupt a specific file |
| POST | `/api/recovery/recover` | Recover all corrupted/deleted files |
| POST | `/api/recovery/recover/:id` | Recover a specific file by ID |
| POST | `/api/optimization/defragment` | Run full defragmentation |
| POST | `/api/optimization/reallocate` | Run block reallocation |
| GET | `/api/stats/dashboard` | Aggregated dashboard statistics |
| GET | `/api/stats/logs` | System journal and recovery logs |
| GET | `/api/stats/activity` | Activity log (all user actions) |
| GET | `/api/stats/performance` | Performance history (fragmentation + access time) |

Full schema details are in `lib/api-spec/openapi.yaml`.

---

## Pages & Modules

### Dashboard
Displays live aggregate statistics: total files, healthy/corrupted/deleted counts, disk usage percentage, fragmentation score, and counters for crashes, recoveries, and optimizations performed.

### File System
Interactive file tree browser with disk block visualization. Create files and directories under any parent, delete nodes, and see the 100-block bitmap update in real time. Blocks are color-coded: teal = used, gray = free.

### Access Simulation
Select any file, choose a read or write operation, and choose sequential or direct access mode. The simulator calculates seek time and transfer time based on block count and access pattern, and returns the exact millisecond cost.

### Crash Simulation
One button triggers a randomized crash event that corrupts 30–60% of healthy files — some lose block pointers, others are marked deleted. Individual files can also be manually corrupted. Post-crash, file statuses update visually across the UI.

### Recovery
Run recovery on all damaged files or target a specific file. Two methods are available:
- **Journal-based**: 75% full recovery, 15% partial recovery probability
- **Backup-based**: 65% full recovery, 15% partial recovery probability

Results show per-file recovery status and an overall success rate percentage.

### Optimization
Two optimization strategies are available:
- **Defragment**: Rewrites all healthy file blocks into contiguous order starting from block 0. Most effective at reducing fragmentation.
- **Reallocate**: Frees and re-allocates blocks for multi-block files without full reordering. Less disruptive but smaller improvement.

Both operations display before/after fragmentation scores and access time improvements, with a performance history chart showing trends over all operations.

### Logs
Filterable view of the complete system journal. Filter by log type (journal, backup, crash, recovery, info) and severity (info, warn, error, success). Each entry shows timestamp, message, and affected file ID.

---

## Core Simulation Logic

The `FilesystemManager` class (`artifacts/api-server/src/lib/filesystem.ts`) is a singleton that holds the entire in-memory virtual filesystem state.

### Block Allocation
- 100 blocks total, tracked by a bitmap array (`0` = free, `1` = used)
- Files allocate `ceil(size / 512)` blocks minimum, always at least 1
- A `blockMap` dictionary maps block index → file ID for reverse lookup

### Fragmentation Score
Calculated as the percentage of files whose block indices are non-contiguous. A file is fragmented if any two adjacent block entries differ by more than 1.

### Crash Model
A crash randomly selects 30–60% of healthy files. Each selected file has a 60% chance of becoming corrupted (may also lose half its blocks) and a 40% chance of being marked deleted.

### Recovery Model
Recovery iterates candidates (corrupted or deleted files) and rolls per-file:
- Roll < threshold → full recovery, blocks restored if missing
- Roll < threshold + 0.15 → partial recovery, additional blocks allocated
- Otherwise → recovery fails

### Defragmentation
Clears the entire bitmap, then replays all healthy files sequentially into contiguous blocks starting at index 0. The `blocksMoved` count reflects how many blocks changed position.

---

## Deployment

### Frontend — Vercel
- Root directory: `artifacts/fs-simulator`
- Build command: `pnpm install && pnpm --filter @workspace/fs-simulator run build`
- Output directory: `dist/public`
- Environment variable: `VITE_API_BASE_URL=https://your-backend.onrender.com`

### Backend — Render
- Build command: `pnpm install && pnpm --filter @workspace/api-server run build`
- Start command: `pnpm --filter @workspace/api-server run start`
- Environment variable: `PORT=10000` (Render sets this automatically)

---

## Troubleshooting

| Error | Cause | Fix |
|---|---|---|
| `'sh' is not recognized` | Root `package.json` uses Unix shell | Replace preinstall with Node.js script |
| `'export' is not recognized` | Unix env syntax in npm script | Use `cross-env` in dev scripts |
| `PORT environment variable is required` | `.env` not loaded | PORT is now embedded in the dev script |
| `Cannot find module @rollup/rollup-win32-x64-msvc` | pnpm-workspace.yaml blocks Windows rollup binary | Remove win32 override lines, delete node_modules + pnpm-lock.yaml, reinstall |
| `Cannot find module lightningcss.win32-x64-msvc.node` | Same as above for lightningcss | Remove lightningcss + tailwindcss/oxide win32 overrides, reinstall |
| Port 8080 already in use | Another process using the port | Change `PORT=8080` to `PORT=3001` in the dev script |
| Vite crashes on start | Missing BASE_PATH/PORT env vars | vite.config.ts now uses defaults (5173, /) |
=======
### 🔹 2. Install PhotoRec (IMPORTANT)

Download from:
https://www.cgsecurity.org/

Extract it and note the path to:

```
photorec_win.exe
```

---

### 🔹 3. Set environment variable

#### Windows:

```
set PHOTOREC_PATH=C:\path\to\photorec_win.exe
```

---

### 🔹 4. Run Backend

```
cd backend
pip install -r requirements.txt
python app.py
```

---

### 🔹 5. Run Frontend

```
cd frontend
npm install
npm run dev
```

### 🔹 6. Then start both servers again:

```
pnpm --filter @workspace/api-server run dev

pnpm --filter @workspace/fs-simulator run dev
```

---

## ⚠️ Note

* This tool works locally only
* Requires administrator privileges
* Do not interrupt recovery process

---

## 👨‍💻 Author

Sanjoli Jain
>>>>>>> 03fbfc36de705870b8a798a58dbbf0a85ba800fd
