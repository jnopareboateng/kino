# 🎬 Kino

> A beautiful, modern desktop video library manager and player for your local collection

<p align="center">
  <img src="https://img.shields.io/badge/Electron-191970?style=for-the-badge&logo=Electron&logoColor=white" alt="Electron" />
  <img src="https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB" alt="React" />
  <img src="https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript" />
  <img src="https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white" alt="Tailwind" />
</p>

Kino transforms your local video collection into a Netflix-like experience. Point it at your folders, and watch as it automatically organizes everything with beautiful posters, metadata, and smart playlists.

---

## ✨ Features

### 📚 Intelligent Library Management
- **Auto-Discovery** - Watches your folders and instantly adds new videos
- **Rich Metadata** - Automatically fetches titles, years, plots, and stunning poster art
- **Zero Manual Work** - Your collection stays organized without lifting a finger

### 🎥 Powerful Video Player
- **Custom Built** - Designed specifically for the best viewing experience
- **Multi-Audio** - Switch between audio tracks on the fly
- **Subtitle Magic** - Embedded and external subtitle support (`.srt`, `.vtt`)
- **Smart Playback** - Variable speed, Picture-in-Picture, and auto-resume

### 🎯 Playlists That Work
- **Manual Playlists** - Create custom collections for any mood
- **Auto-Generated** - Smart playlists based on your folder structure
- **Series Ready** - Perfect for binge-watching TV shows

### 🔍 Find Anything Fast
- **Instant Search** - Lightning-fast filtering through your entire library
- **Smart Filters** - Find exactly what you're looking for

---

## 🚀 Quick Start

### Prerequisites

- **Node.js** 16+ ([Download](https://nodejs.org/))
- npm, yarn, or pnpm

### Installation

```bash
# Clone the repo
git clone <repository-url>
cd kino

# Install dependencies
npm install

# Start developing
npm run dev
```

That's it! Kino will launch with hot-reload enabled.

### Building for Production

```bash
npm run build
```

The packaged app will be ready in the `dist` directory.

---

## 🛠️ Tech Stack

| Technology | Purpose |
|------------|---------|
| **Electron** | Desktop app framework |
| **React + TypeScript** | UI and type safety |
| **Vite** | Lightning-fast builds |
| **TailwindCSS** | Beautiful, utility-first styling |
| **better-sqlite3** | Fast local database |
| **ffmpeg** | Media metadata extraction |
| **chokidar** | Real-time file watching |
| **react-router-dom** | Seamless navigation |

---

## 📁 Project Structure

```
kino/
├── src/                    # Frontend React application
│   ├── components/         # Reusable UI components
│   │   ├── Sidebar.tsx
│   │   ├── VideoPlayer.tsx
│   │   └── MovieCard.tsx
│   ├── pages/             # Main application views
│   │   ├── Library.tsx
│   │   ├── PlaylistPage.tsx
│   │   └── Settings.tsx
│   └── assets/            # Images and icons
│
├── electron/              # Electron main process
│   ├── main.ts           # App entry point
│   └── lib/              # Core backend modules
│       ├── database.ts   # SQLite operations
│       ├── ipc.ts        # IPC handlers
│       ├── scraper.ts    # Metadata fetching
│       ├── watcher.ts    # File system monitoring
│       ├── playlists.ts  # Playlist logic
│       └── ffmpeg.ts     # Media processing
```

---

## 🎯 How It Works

1. **Point Kino at your video folders** - Add directories through the settings
2. **Watch the magic happen** - Kino scans and enriches your library with metadata
3. **Browse beautifully** - Your collection comes alive with posters and details
4. **Play seamlessly** - Custom player with all the features you need

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## 📝 License

[Add License Information Here]

---

## 🌟 Show Your Support

Give a ⭐️ if this project helped you organize your video collection!

---

<p align="center">Made with ❤️ by developers who love movies</p>
