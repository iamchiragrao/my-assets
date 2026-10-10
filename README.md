# ⚡ My Assets & High-Performance CDN Delivery

Global media asset repository and ultra-fast edge delivery for **iamchiragrao**, powered by **jsDelivr Anycast CDN** and **GitHub Pages**.

---

## 🚀 Live Web Dashboard

Manage, upload, preview, and delete assets with a high-performance studio interface:

👉 **[https://iamchiragrao.github.io/my-assets/home](https://iamchiragrao.github.io/my-assets/home)**

---

## 🌐 Global CDN URL Formats

All files uploaded to `/assets` are cached at 750+ Anycast edge nodes worldwide:

### 1. jsDelivr Ultra-Fast CDN (Recommended for Production)
```text
https://cdn.jsdelivr.net/gh/iamchiragrao/my-assets@main/assets/<filename>
```
* **Latency:** <15ms globally
* **Caching:** Unlimited global Anycast edge caching with HTTP/2 and Brotli/Gzip compression
* **Best for:** Video clips, hero graphics, photos, SVGs, audio clips

### 2. GitHub Pages Direct URL (Fallback)
```text
https://iamchiragrao.github.io/my-assets/assets/<filename>
```

### 3. GitHub Raw Content URL (For raw downloads)
```text
https://raw.githubusercontent.com/iamchiragrao/my-assets/main/assets/<filename>
```

---

## 🔄 Instant Cache Invalidation (Purge Trick)

When you update or replace an existing asset with the same name, jsDelivr edge nodes can be instantly purged:

```bash
curl https://purge.jsdelivr.net/gh/iamchiragrao/my-assets@main/assets/<filename>
```
*(The web dashboard also includes a 1-click **Purge** button for every asset.)*

---

## 🛠 Features of the Web Dashboard

- **Drag-and-Drop Uploader:** Upload single or batch files with progress indicators.
- **Auto-Sanitization:** Renames files to web-safe slugs (no spaces or URL-breaking special characters).
- **Inline Video Player:** Hover preview, loop, volume, and fullscreen modal player for MP4 / WebM / MOV videos.
- **1-Click Copy Links:** Instant copy buttons for jsDelivr CDN URLs, HTML tags (`<video>`, `<img>`), and Markdown.
- **Safe Authentication:** Token is stored locally in your browser's `localStorage` and never committed into public git code.
- **Deletion:** Remove assets directly from GitHub with 1 click.

---

## 📦 Directory Structure

```text
my-assets/
├── assets/          # All uploaded videos, images, and media files
├── home/
│   └── index.html   # Entrypoint for /home route
├── index.html       # Web Dashboard SPA
├── 404.html         # GitHub Pages SPA fallback
└── README.md        # Documentation
```
