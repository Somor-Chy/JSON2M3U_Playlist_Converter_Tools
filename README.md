# JSON-TO-M3U

**A universal, client-side tool to convert any JSON playlist (IPTV, streaming, etc.) into a standard M3U file — with live preview, custom field mapping, and a rich UI.**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)

---

## 🌟 Features | বৈশিষ্ট্য

- ✅ **Universal JSON Support** – Recursively scans any JSON structure to find channel arrays.
- ⚙️ **Custom Field Mapping** – Define which JSON keys map to `tvg-id`, `tvg-logo`, `group-title`, `title`, and `url`.
- 📂 **File Upload + Paste Input** – Drag & drop a JSON file or paste directly.
- 🎯 **Manual Conversion** – Convert only when you click the big **Convert to M3U** button.
- 🌐 **Bilingual UI** – Toggle between **English** and **বাংলা** (Bengali) interface.
- 🎨 **Theme Switcher** – Light, Dark, or follow System preference.
- 🔍 **Live Search & Highlight** – Find text in the M3U output instantly with yellow highlighting and navigation (Prev/Next).
- 📋 **Copy & Download** – Copy the M3U content to clipboard or download as `.m3u` file.
- 📱 **Desktop-Optimized Layout** – Fixed width layout for consistent experience across devices.

---

## 🚀 Live Demo | সরাসরি ব্যবহার

> You can run this tool **completely offline** – no internet required after loading the page.

1. Clone or download this repository.
2. Open `index.html` in any modern browser.
3. Upload a JSON file or paste JSON content.
4. Adjust field mapping if needed (defaults work for most IPTV JSON structures).
5. Click **"Convert to M3U"**.
6. Copy or download the generated M3U playlist.

---

## 📸 Screenshots | স্ক্রিনশট

| Light Theme | Dark Theme |
|-------------|------------|
| ![Light Theme Screenshot](screenshots/light.png) | ![Dark Theme Screenshot](screenshots/dark.png) |

*Replace with actual screenshots after testing.*

---

## 🧠 How It Works | কিভাবে কাজ করে

1. **JSON Parsing** – The tool recursively traverses the uploaded/pasted JSON object.
2. **Channel Detection** – It identifies arrays whose elements contain a stream URL (using your defined URL keys).
3. **Field Extraction** – For each channel, it extracts `id`, `logo`, `group`, `title`, and `url` based on the mapping settings.
4. **Parent Group Detection** – If a channel array is nested inside an object with a `cat_name` or similar key, that value is used as `group-title`.
5. **M3U Generation** – Produces a valid `#EXTM3U` playlist with proper formatting and blank lines for readability.

### Example JSON Input:
```json
[
  {
    "cat_name": "Group/Category",
    "livetvs": [
      {
        "id": 23,
        "channel_name": "Channel 1",
        "stream_url": "https://example.com/channel1.m3u8",
        "channel_logo": "https://example.com/channel1.png"
      }
    ]
  }
]

```
### Example M3U Output:
```html
#EXTM3U

#EXTINF:-1 tvg-id="1" tvg-logo="https://example.com/bbc.png" group-title="Group/Category", Channel 1
https://example.com/channel1.m3u8

