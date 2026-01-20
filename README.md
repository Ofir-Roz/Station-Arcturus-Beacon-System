# 🛰️ Station Arcturus Beacon System

> A real-time space beacon tracking system demonstrating TCP/IP networking with Unity 3D visualization and FastAPI backend.

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Unity 6000. 2. 10f1](https://img.shields.io/badge/unity-6000.2.10f1-black.svg)](https://unity.com/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.121.1-009688.svg)](https://fastapi.tiangolo.com/)
[![Socket.IO](https://img.shields.io/badge/Socket.IO-Enabled-010101.svg)](https://socket.io/)

---

## 📖 Overview

Station Arcturus simulates a space station command center that tracks and visualizes beacon positions in real-time 3D space. The system demonstrates practical implementation of the **TCP/IP networking model** through a modern web-socket architecture.

### 🎬 Live Visualization

<div align="center">

<img width="600" height="800" alt="צילום מסך 2026-01-20 150749" src="https://github.com/user-attachments/assets/01d763c1-3ba8-4d4c-b470-a4bfdaccc7b6" />

*Real-time beacon tracking visualization showing multiple beacons around a planetary body*

<img width="600" height="800" alt="צילום מסך 2026-01-20 150822" src="https://github.com/user-attachments/assets/8bbfe327-0a05-4f5f-8710-d07adaa9f02c" />

*Command interface displaying beacon status with active, damaged, and offline beacons*

</div>

### ✨ Key Features

- 🌐 **Real-time communication** via WebSocket (Socket.IO)
- 🎮 **3D visualization** with Unity 6000.2.10f1
- 🔄 **Live beacon tracking** with position and status updates
- 🖥️ **Cross-platform** builds for Windows and macOS
- 🌍 **Multi-client support** (Unity, HTML5 web client)
- 📡 **RESTful API** for beacon data access

### 🎯 System Components

| Component | Technology | Purpose |
|-----------|-----------|---------|
| **Backend Server** | FastAPI + Socket.IO | Real-time data broadcast and REST API |
| **Unity Frontend** | Unity 6000.2.10f1 | 3D visualization and interaction |
| **Web Client** | HTML5 + Socket.IO | Browser-based testing interface |
| **Communication** | WebSocket over TCP | Bidirectional real-time updates |

### 📊 Beacon States

Beacons are tracked with **3D coordinates** (x, altitude, z) and dynamic status:

- ✅ **ACTIVE** (Yellow) - Operational and transmitting
- ⚠️ **DAMAGED** (Red) - Functional with errors
- ❌ **OFFLINE** (Red) - Not responding

---

## 📁 Project Structure

```
Station-Arcturus-Beacon-System/
├── 📱 Builds/                                    # Pre-built executables
│   ├── Windows/
│   │   └── Station Arcturus Command Room.exe
│   └── macOS. app/
│
├── 🎨 frontend/
│   └── unity/
│       └── StationArcturusCommand/              # Unity 6000.2.10f1 project
│           ├── Assets/
│           │   ├── Scripts/                     # C# networking & visualization
│           │   ├── Scenes/                      # Main command room scene
│           │   └── Prefabs/                     # Beacon prefabs
│           └── ProjectSettings/
│
├── ⚙️ backend/                                   # Python FastAPI server
│   ├── app/
│   │   ├── main.py                              # FastAPI + Socket.IO setup
│   │   ├── models. py                            # Pydantic data models
│   │   ├── beacons.py                           # Beacon simulation logic
│   │   └── events.py                            # WebSocket event handlers
│   ├── static/                                  # HTML test client
│   ├── requirements.txt
│   └── run. py                                   # Server entry point
│
├── 📚 Documentation/
│   ├── TCP-IP-IMPLEMENTATION.md                 # TCP/IP layer breakdown
│   ├── Station Arcturus_ System Architecture Overview.pdf
│   ├── Architectural Deep Dive_ Communication Protocol.pdf
│   └── TCP-IP-Implementation_in_app.pdf
│
└── README.md                                    # This file
```

---

## 🚀 Quick Start

### Prerequisites

- **Python 3.8+** ([Download](https://www.python.org/downloads/))
- **Pre-built executable** or **Unity 6000.2.10f1** (for development)

### 1️⃣ Start the Backend Server

```bash
# Navigate to backend directory
cd backend

# Create virtual environment (first time only)
python -m venv .venv

# Activate virtual environment
. venv\Scripts\activate          # Windows
source .venv/bin/activate       # macOS/Linux

# Install dependencies (first time only)
pip install -r requirements.txt

# Start the server
python run.py
```

✅ **Server running at:** `http://127.0.0.1:8000`

#### 🧪 Test the Backend

| Endpoint | Description |
|----------|-------------|
| [`/ui`](http://127.0.0.1:8000/ui) | HTML5 test client |
| [`/status`](http://127.0.0.1:8000/status) | Server health check |
| [`/beacons`](http://127.0.0.1:8000/beacons) | REST API for beacon data |
| [`/docs`](http://127.0.0.1:8000/docs) | Interactive API documentation |

### 2️⃣ Launch the Unity Frontend

#### Option A: Pre-Built Executable (Recommended)

**Windows:**
```bash
cd Builds/Windows
# Double-click Station Arcturus Command Room.exe
```

**macOS:**
```bash
cd Builds
# Double-click macOS.app
# If blocked:  System Preferences → Security & Privacy → "Open Anyway"
```

#### Option B: Unity Editor (Development)

1. Open **Unity Hub**
2. Add project: `frontend/unity/StationArcturusCommand`
3. Open with **Unity 6000.2.10f1**
4. Press ▶️ **Play** in the editor

---

## 🏗️ System Architecture

### 🌐 Networking Stack (TCP/IP Implementation)

```
┌─────────────────────────────────────────────────────────┐
│  APPLICATION LAYER                                      │
│  • FastAPI (REST API)                                   │
│  • Socket.IO (WebSocket events)                         │
│  • JSON serialization                                   │
│  • CORS middleware                                      │
└─────────────────────────────────────────────────────────┘
                         ↕
┌─────────────────────────────────────────────────────────┐
│  TRANSPORT LAYER                                        │
│  • TCP connections (reliable, ordered delivery)         │
│  • Port 8000 multiplexing                               │
│  • WebSocket handshake (HTTP → WS upgrade)              │
└─────────────────────────────────────────────────────────┘
                         ↕
┌─────────────────────────────────────────────────────────┐
│  INTERNET LAYER                                         │
│  • IPv4 addressing (127.0.0.1:8000)                     │
│  • IP packet routing                                    │
└─────────────────────────────────────────────────────────┘
```

> 📘 **Deep Dive:** See [TCP-IP-IMPLEMENTATION. md](TCP-IP-IMPLEMENTATION.md) for detailed layer-by-layer breakdown. 

### 🔄 Real-Time Data Flow

```
Backend (Python)                     Frontend (Unity)
─────────────────                    ────────────────
beacon_updater()                           │
    │                                      │
    ├─ Simulate beacon movement            │
    ├─ Update positions/status             │
    │                                      │
    └─ sio.emit("beacon_update")  ────────►│  SocketIOClient
           │                               │      │
           │ (Every 2 seconds)             │      └─ Parse JSON
           │                               │      └─ Update GameObjects
           │                               │      └─ Render particles
           │                               │
           └───────────────────────────────┴─ WebSocket over TCP
```

### 🛠️ Backend Technology Stack

| Component | Version | Purpose |
|-----------|---------|---------|
| **FastAPI** | 0.121.1 | REST API framework |
| **python-socketio** | 5.14.2 | WebSocket event handling |
| **uvicorn** | 0.34.0 | ASGI web server |
| **pydantic** | 2.12.4 | Data validation |
| **python-engineio** | 4.12.2 | Socket.IO transport |

### 🎮 Unity Features

- **🎥 Orbital Camera Controller** - Interactive 3D navigation
- **✨ Particle Systems** - Visual beacon status effects (see screenshots above)
- **🔌 Socket.IO Client** - Real-time data synchronization
- **🗺️ Coordinate Mapping** - Planetary position visualization
- **🎯 Dynamic Instantiation** - Runtime beacon spawning

---

## ⚙️ Configuration

### Backend Configuration

Edit `backend/run.py` to customize server settings:

```python
import uvicorn

if __name__ == "__main__": 
    uvicorn.run(
        "app.main:socket_app",
        host="0.0.0.0",      # Bind to all interfaces
        port=8000,           # Server port
        reload=True          # Auto-reload on code changes (dev mode)
    )
```

**Key Settings:**
- **Port:** Default `8000` (change if port conflict occurs)
- **CORS:** Configured for `*` (all origins) - **restrict in production! **
- **Broadcast Interval:** 2 seconds (configurable in `beacons.py`)

### Unity Configuration

**Connection settings** in `Assets/Scripts/SocketIOManager.cs`:

```csharp
private string serverUrl = "http://127.0.0.1:8000";
```

To connect to a remote server:
1. Modify `serverUrl` in Unity project
2. Rebuild the application

---

## 🧪 Development

### Backend Development

```bash
cd backend

# Run with auto-reload
python run.py

# Run tests (if available)
pytest

# View logs
# Logs appear in console with uvicorn output
```

**API Endpoints:**

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/beacons` | Get all beacon data |
| GET | `/status` | Server health check |
| GET | `/ui` | HTML test interface |
| WS | `/socket. io/` | WebSocket connection |

**WebSocket Events:**

| Event | Direction | Payload |
|-------|-----------|---------|
| `connect` | Client → Server | Connection established |
| `beacon_update` | Server → Client | Beacon position/status array |
| `ping` / `pong` | Bidirectional | Health check |

### Unity Development

**Requirements:**
- Unity 6000.2.10f1
- Universal Render Pipeline (URP)
- SocketIOClient NuGet package

**Key Scripts:**
- `SocketIOManager.cs` - WebSocket communication
- `BeaconManager.cs` - Beacon instantiation and updates
- `OrbitCamera.cs` - Camera controls

**Building for Distribution:**
1. File → Build Settings
2. Select platform (Windows/macOS)
3. Add `MainScene` to build
4. Set output to `Builds/[Platform]/`
5. Build

---

## 🐛 Troubleshooting

### Common Issues

| Problem | Solution |
|---------|----------|
| ❌ **"Connection refused"** | Ensure backend server is running on port 8000 |
| ❌ **"Port 8000 already in use"** | Stop other services or change port in `run.py` |
| ❌ **"Module not found"** | Activate venv and run `pip install -r requirements.txt` |
| ❌ **Unity can't connect** | Check firewall settings and server URL |
| ❌ **macOS "unidentified developer"** | Right-click → Open → "Open Anyway" |
| ❌ **Beacons not updating** | Check browser console / Unity console for errors |

### Debug Mode

**Backend:**
```bash
# Enable detailed logging
uvicorn app.main:socket_app --log-level debug
```

**Unity:**
- Open Console window (Ctrl+Shift+C / Cmd+Shift+C)
- Check for connection errors and JSON parsing issues

**Browser:**
- Open `/ui` endpoint
- Check DevTools Console (F12) for WebSocket errors

---

## 📚 Documentation

- **[System Architecture Overview](Station%20Arcturus_%20System%20Architecture%20Overview.pdf)** - High-level design
- **[Communication Protocol Deep Dive](Architectural%20Deep%20Dive_%20Communication%20Protocol%20for%20Station%20Arcturus.pdf)** - WebSocket protocol details
- **[Backend README](backend/README.md)** - Server-specific documentation

---

## 🤝 Contributing

Contributions are welcome! Please feel free to: 
- Report bugs via [Issues](../../issues)
- Suggest features
- Submit pull requests

---

## 📄 License

This project is open source and available for educational purposes.

---

## 👤 Author

**Ofir Roz** - [GitHub Profile](https://github.com/Ofir-Roz)


</div>
