# File Recovery Tool - Frontend Setup Guide

## How the Frontend Connects to Your Backend

Your Flask backend and this React frontend communicate through **HTTP API calls**. Here's how it works:

### Architecture Overview

```
┌─────────────────┐      HTTP Requests      ┌──────────────────┐
│                 │  ───────────────────────> │                  │
│  React Frontend │                           │  Flask Backend   │
│  (Port 5173)    │  <─────────────────────── │  (Port 5000)     │
│                 │      JSON Responses       │                  │
└─────────────────┘                           └──────────────────┘
```

### API Endpoints Used

The frontend connects to these Flask endpoints:

1. **GET /** - Check if backend is running
2. **POST /recover** - Start file recovery
   - Sends: `{ "drive": "C:" }`
   - Receives: `{ "status": "success", "message": "..." }`
3. **GET /files** - Get list of recovered files
   - Receives: `{ "files": ["path/to/file1", "path/to/file2"] }`

### Where the Connection Happens

Check `src/services/api.ts` - this file handles all API communication:

```typescript
const API_BASE_URL = 'http://localhost:5000';  // Your Flask server

// Example: Calling the /recover endpoint
fetch(`${API_BASE_URL}/recover`, {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({ drive: 'C:' })
})
```

## Setup Instructions

### Step 1: Start Your Flask Backend

Navigate to your backend folder and run:

```bash
cd file-recovery-tool/backup
python app.py
```

Your backend should start on `http://localhost:5000`

### Step 2: Start the Frontend

In this directory, run:

```bash
npm install    # Install dependencies (first time only)
npm run dev    # Start development server
```

The frontend will open at `http://localhost:5173`

### Step 3: Using the Application

1. Enter a drive path (e.g., `C:` for Windows or `/dev/sda1` for Linux)
2. Click "Start Recovery"
3. The frontend sends a POST request to `/recover`
4. Wait for the recovery to complete
5. View recovered files organized by category

## Understanding CORS

Your Flask backend has this line:
```python
CORS(app)
```

This allows the frontend (running on port 5173) to make requests to the backend (running on port 5000). Without CORS, browsers would block these cross-origin requests.

## Troubleshooting

### "Backend Disconnected" Message

If you see this:
- Make sure your Flask server is running (`python app.py`)
- Check that it's running on port 5000
- Try clicking "Retry Connection"

### Recovery Not Starting

- Ensure you've entered a valid drive path
- Check the Flask console for error messages
- Make sure PhotoRec is properly configured in `config.py`

### Files Not Showing

- Files appear after recovery completes
- Click the refresh button or restart recovery
- Check the `recovered_files` folder in your backend directory

## Key Files

- `src/App.tsx` - Main UI component
- `src/services/api.ts` - API connection logic
- `src/components/FilesList.tsx` - Displays recovered files

## How to Modify

### Change Backend URL

If your Flask server runs on a different port, edit `src/services/api.ts`:

```typescript
const API_BASE_URL = 'http://localhost:YOUR_PORT';
```

### Add New API Endpoints

1. Add endpoint to Flask backend
2. Add corresponding function in `src/services/api.ts`
3. Call it from your React components

## Production Deployment

For production, you'll need to:

1. Build the frontend: `npm run build`
2. Serve the `dist` folder with a web server
3. Update `API_BASE_URL` to your production backend URL
4. Configure your Flask backend for production (use Gunicorn, etc.)
