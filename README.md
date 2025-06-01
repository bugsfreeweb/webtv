# Bugsfree Studio IPTV Player

A modern, animated IPTV player for the web, featuring the Bugsfree Studio animated logo, playlist management, channel analysis, viewer stats, dark/light themes, and a retro TV scanlines effect.  
**No backend required – fully client-side, works with `.m3u`, `.m3u8`, `.json`, `.txt` playlists (local or via URL).**

---

## Features

- **Animated Bugsfree Studio Logo**: Dynamic effects with intro and cycling animations.
- **Playlist Management**:
  - Load playlists from file or URL (`.m3u`, `.json`, `.txt`).
  - Add favorites, view history, and easily reload playlists.
  - Persist favorites/history to browser storage.
- **Channel Analysis & Visualization**:
  - Check which channels are online or offline (HEAD request).
  - Pie chart visualization (Chart.js).
  - Filter channel list by all/online/offline.
- **Background Sync**:  
  - Auto-refresh online/offline status every 2 minutes (configurable).
- **Video Playback**:
  - HLS, DASH, MP4, TS support.
  - Custom player with mute, brightness, contrast, saturation controls.
  - Scanlines overlay for retro TV look.
  - Animated Bugsfree logo in the player.
- **UI/UX**:
  - Responsive, tabbed interface.
  - Dark and light themes (with toggle, persists to local storage).
  - Keyboard (arrow keys, space, enter, escape) and gesture support (swipe/tap for channel and volume).
  - Channel preview, logo display, and viewer count.
- **Other**:
  - "Report Issue" button linked to GitHub issues.
  - No server required: everything runs in the browser.

---

## Getting Started

### 1. Download or Clone

```sh
git clone https://github.com/YOUR_USERNAME/YOUR_REPO.git
```

Or download the HTML/JS/CSS files and open in your browser.

### 2. Playlist Formats Supported

| Format  | Description                                  | Example                                                  |
|---------|----------------------------------------------|----------------------------------------------------------|
| `.m3u`  | Standard IPTV format                         | `#EXTINF:-1 tvg-logo="logo.png",Channel Name\nURL`       |
| `.txt`  | Simple: `URL|Channel Name` per line          | `http://.../stream.m3u8|My Channel`                     |
| `.json` | Array or object with `channels` array/object | `{ "channels": [{ "src": "...", "name": "...", ... }]}`  |

### 3. Usage

- **Open in browser**  
  Just open `index.html` (or the page where this script is included).
- **Add Playlist**  
  - Drag & drop, or use the upload form (file or URL).
  - Channels are parsed and listed instantly.
- **Playback Controls**
  - Click a channel to play.
  - Use arrow keys, touch gestures, or on-screen buttons to switch channels or adjust volume.
- **Favorites & History**
  - Star a channel to add to favorites.
  - Uploaded/loaded playlists are remembered in history.

---

## UI Controls

| Action                  | How to Use               |
|-------------------------|-------------------------|
| Next/Prev Channel       | Arrow Down/Up or swipe  |
| Mute/Unmute             | Space or mute buttons   |
| Volume                  | Arrow Left/Right, swipe |
| Brightness/Contrast/etc | Use sliders             |
| Change Theme            | Sun/Moon button         |
| Sidebar                 | Toggle button or Escape |
| Add Playlist            | Upload or URL forms     |
| Check Channel Status    | "Sync" or enable auto   |

---

## Code Structure

### Core Files

- **UI & Logic**:  
  - Uses native DOM APIs (`$`, `$all` helpers).
  - All state and playlists are managed in-memory and localStorage.
- **Playlist Parsing**:
  - Parses `.m3u`, `.txt`, `.json` formats, supporting various structures.
- **Player**:
  - Renders `<video>` tag with HLS.js or native support.
  - Animated logo is injected into the player UI.
- **Analysis**:
  - Uses `fetch` with `HEAD` requests to check channel online status.
  - Chart.js for doughnut chart visualization.
- **Persistence**:
  - Uses `localStorage` for playlists, favorites, and history.
- **Settings & Theming**:
  - Theme is persisted, toggled via UI.
  - All major UI elements are accessible via keyboard and mouse/touch.

### Main Objects/Variables

- `channels`, `favorites`, `history`, `filteredChannels`: Channel lists.
- `playlistLoaded`, `playlistKey`: Playlist state.
- `currentChannelIndex`, `isMuted`, `scanlinesEnabled`, `theme`: UI/player state.
- `backgroundSyncEnabled`, `backgroundSyncInterval`: Sync status.

### Main Functions

- **Playlist**: `parseM3u`, `parseJson`, `parseTxt`, `parseCustom`
- **Playback**: `playChannel`, `playByChannel`, `nextChannel`, `prevChannel`, `toggleMute`
- **UI**: `renderChannelList`, `updateFavoritesListUI`, `updateHistoryListUI`, `updateMuteIcons`
- **Analysis**: `updateAnalysis`, `createChart`, `syncAndShowOnlineChannels`
- **Animation**: `addBugsfreeStudioLogoAnimation`, `bfsLogoAnimCycle`

---

## Customization

- **Default Logo/Poster**: Change `DEFAULT_LOGO` and `PLAYER_POSTER` constants.
- **Demo Playlist**: Customize the `demoPlaylist` array.
- **Logo Animation**: Modify or add CSS animation classes for `.special-animated`.

---

## Dependencies

- [Hls.js](https://github.com/video-dev/hls.js) (for HLS playback in browsers that don't support it natively)
- [feather-icons](https://feathericons.com/) (SVG icon replacement)
- [Chart.js](https://www.chartjs.org/) (for analysis chart)

All dependencies can be loaded via CDN.

---

## License

MIT License

---

## Credits

- **Bugsfree Studio**  
  Animated branding and overall design  
- **Contributors**  
  See [GitHub Contributors](./contributors)

---

## Issues & Contributions

- Found a bug? [Open an issue](https://github.com/bugsfreeweb/webtv/issues)
- Want to contribute? Submit a pull request!

---

## Disclaimer

IPTV streams must be used in accordance with their terms and local laws. This project is for educational purposes.
