# RemOBS — Remote Control for OBS Studio

A lightweight web interface to control OBS Studio remotely via browser. Built with HTML, CSS, JavaScript (Vanilla), and PHP (for To-Do List persistence). Communicates with OBS using **OBS WebSocket v5**.

Perfect for tablets, smartphones, or secondary monitors during live streaming, podcasting, or recording.

## Features

- **Dynamic WebSocket Connection** — Promise-based connection ensures reliable communication between browser and OBS.
- **Auto-Sync Status** — On connection, automatically reads OBS state in real-time (volume, mic mute, stream/record status, active scene).
- **Scene Switcher (Realtime Highlight)** — Displays all scenes from OBS; highlights the active scene with a glowing green indicator. Highlight updates automatically when scene changes in OBS.
- **Audio & Volume Control** — Mute/unmute Mic/Aux, real-time volume sliders for Desktop Audio and Mic/Aux.
- **Output Control** — Start/Stop Streaming, Start/Stop Recording, Save Replay Buffer.
- **Camera Toggle** — Show/hide camera sources in the active scene with a single click.
- **Text Overlay** — Change text sources in OBS instantly (great for switching game names, discussion topics, or host names).
- **Scene Sources** — View and toggle individual scene items on/off.
- **Transition Selector** — Choose and change transitions from the web interface.
- **Media Controls** — Play, pause, stop, and restart media sources.
- **Interactive To-Do List** — Create rundown checklists saved automatically via PHP backend.

## Prerequisites

1. **OBS Studio** v28.0+ (OBS WebSocket v5 is built-in).
2. A web server with **PHP** (e.g., XAMPP, Laragon, MAMP, Nginx/Apache) for the To-Do feature.

## Setup

1. Clone or extract this project into your web server directory:
   - XAMPP: `htdocs/obs`
   - Nginx/Apache: `/var/www/html/obs`
2. Open **OBS Studio** → `Tools` → `WebSocket Server Settings`:
   - Enable **Enable WebSocket server**
   - Note the **Server Port** (default: `4455`)
   - Optionally enable **Authentication** and set a password
3. Ensure your OBS audio sources are named `Desktop Audio` and `Mic/Aux` (or edit the names in `index.html`).
4. For the **Text Overlay** feature, create a text source named `TeksOverlay`.

## Usage

1. Open a browser on your control device (phone, tablet, etc.). Ensure it's on the same WiFi/LAN as the OBS computer.
2. Navigate to `http://<your-ip>/obs`
3. Enter the **local IP** of the OBS computer.
4. Enter the **Port** (default: `4455`).
5. Enter the **Password** (leave blank if authentication is disabled).
6. Adjust the **Camera Source Name** to match your camera source in OBS.
7. Click **Connect**.

## File Structure

| File | Description |
|------|-------------|
| `index.html` | Main application UI + WebSocket logic (JavaScript) |
| `save-todo.php` | PHP backend for persisting the To-Do list |
| `todo-data.json` | JSON-based To-Do storage (auto-created/updated by PHP) |
| `todo-display.html` | Standalone overlay view for To-Do items (can be used as a browser source in OBS) |

## Tech Stack

- **Frontend**: Vanilla HTML, CSS, JavaScript
- **Backend**: PHP
- **Protocol**: OBS WebSocket v5
- **Storage**: JSON file
