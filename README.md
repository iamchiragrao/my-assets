# ⚡ Masterplan: Dual-Engine Asset & Media Delivery

Global media architecture for **iamchiragrao**, pairing **jsDelivr Anycast Edge CDN** for web-performance streaming with **GitHub Releases Vault** for high-capacity object storage up to **2 GB per file**.

---

## 🚀 Live Dashboard UI

Manage, preview, stream, upload, and purge assets across both engines in one unified view:

👉 **[https://iamchiragrao.github.io/my-assets/home](https://iamchiragrao.github.io/my-assets/home)**

---

## 🏛️ Architecture Breakdown

| Feature | ⚡ Engine 1: Edge CDN (jsDelivr) | 📦 Engine 2: Release Vault (GitHub Releases) |
| :--- | :--- | :--- |
| **Primary Use** | Website Video Clips, Hero Graphics, SVGs, Loops | 4K Client Masters, Long Reels, Heavy Project Archives |
| **File Size Limit** | Up to **20 MB** per file | Up to **2 GB** per file |
| **Latency** | Sub-15ms Anycast Edge (750+ POPs) | Global Fastly Edge Network |
| **Video Scrubbing** | Native HTTP/2 Byte-Range (Perfect for iOS/Android) | Standard HTTP Range with 302 Redirect |
| **URL Format** | `https://cdn.jsdelivr.net/gh/iamchiragrao/my-assets@main/assets/<file>` | `https://github.com/iamchiragrao/my-assets/releases/download/v1.0-assets/<file>` |
| **Upload Pipeline** | Base64 via Git Contents API | Raw Binary Stream via Release Asset API |
| **Cache Purging** | `https://purge.jsdelivr.net/gh/...` (1-click in UI) | Instant (Immutable asset URL) |

---

## 🤖 Smart Auto-Routing in the Web Dashboard

When you drag and drop files onto the dashboard:
1. **Files < 20 MB:** Automatically routed to **Edge CDN** for instant mobile-optimized web streaming.
2. **Files > 20 MB (up to 2 GB):** Automatically routed to **Release Vault** with real-time percentage progress bars via raw binary streaming.
3. You can also manually toggle between **⚡ Edge CDN** and **📦 Release Vault** before uploading.

---

## 🛠 Local 1-Click Desktop Tool (`tools/upload-asset.py`)

A desktop script is included in `c:\Projects\iamchiragrao\tools` allowing you to compress large 250MB+ raw video exports into web-optimized H.264 clips in 3 seconds before publishing, or upload them directly to the Vault!
