# 🚀 Chirag Rao Portfolio Media & Asset Management System

Welcome to your unified media asset and portfolio management platform. This system replaces Cloudinary with a **100% free, high-performance, dual-engine asset pipeline** paired with a **live Web Dashboard and Portfolio Linker Studio**.

---

## 🌐 Live URLs

| Destination | URL | Description |
| :--- | :--- | :--- |
| **Asset & Linker Studio Dashboard** | [https://iamchiragrao.github.io/my-assets/](https://iamchiragrao.github.io/my-assets/) | Upload, manage, and link videos to your live website |
| **Alternative Dashboard Route** | [https://iamchiragrao.github.io/my-assets/home](https://iamchiragrao.github.io/my-assets/home) | Mirror route for direct navigation |
| **Live Portfolio Website** | [https://iamchiragrao.github.io](https://iamchiragrao.github.io) | Your live portfolio (auto-deployed on changes) |
| **Asset Storage Repo** | [https://github.com/iamchiragrao/my-assets](https://github.com/iamchiragrao/my-assets) | Git repository hosting the assets and dashboard |
| **Main Website Codebase** | [https://github.com/iamchiragrao/iamchiragrao](https://github.com/iamchiragrao/iamchiragrao) | Next.js source code for your portfolio |

---

## 🧠 What We Built & Why

### The Problem
Previously, video assets were hosted on Cloudinary. Due to free tier bandwidth caps, quota limits, and transformation restrictions, videos either stopped loading or ran into limits.

### The Solution: Dual-Engine Architecture
We replaced Cloudinary with a completely free, enterprise-grade architecture:

```
                             ┌─────────────────────────────────┐
                             │    Your Browser / Dashboard     │
                             │  iamchiragrao.github.io/my-assets│
                             └──────────────┬──────────────────┘
                                            │
                       ┌────────────────────┴────────────────────┐
                       │                                         │
        [Files <= 20 MB]                                [Files > 20 MB (up to 2 GB)]
                       ▼                                         ▼
            ⚡ ENGINE 1: EDGE CDN                    📦 ENGINE 2: RELEASE VAULT
      ┌───────────────────────────────┐        ┌───────────────────────────────┐
      │ GitHub Repo: assets/          │        │ GitHub Release: v1.0-assets   │
      │   + jsDelivr Anycast Edge CDN │        │   + Fastly Global Edge CDN    │
      │ Sub-15ms latency, 750+ POPs   │        │ Supports heavy 4K client cuts │
      └───────────────────────────────┘        └───────────────────────────────┘
                       │                                         │
                       └────────────────────┬────────────────────┘
                                            ▼
                             ┌─────────────────────────────────┐
                             │     Portfolio Linker Studio     │
                             │  19 Slots: Carousel & Repurpose │
                             │  Stages Changes -> Diff Preview │
                             │  1-Click Commit & Auto-Deploy   │
                             └─────────────────────────────────┘
```

---

## ⚡ The Two Storage Engines Explained

| Feature | ⚡ Engine 1: Edge CDN (jsDelivr) | 📦 Engine 2: Release Vault (GitHub Releases) |
| :--- | :--- | :--- |
| **Best For** | Web video loops, short reels, hero clips, SVGs, PNGs | High-res long videos, 4K client masters, heavy archives |
| **File Size Limit** | Up to **20 MB** per file | Up to **2 GB** per file |
| **Delivery Speed** | Instant Anycast CDN (sub-15ms, 750+ PoPs worldwide) | Global Fastly Edge Network |
| **Video Streaming** | Native HTTP/2 Byte-Range (smooth seeking on iOS/Android) | Standard HTTP Range with 302 Redirect |
| **Public CDN URL** | `https://cdn.jsdelivr.net/gh/iamchiragrao/my-assets@main/assets/<filename>` | `https://github.com/iamchiragrao/my-assets/releases/download/v1.0-assets/<filename>` |
| **Storage Backend** | Git commit in `assets/` folder | Release asset in Release `v1.0-assets` |

---

## 📖 How to Use the Studio (Step-by-Step Guide for Chirag)

### Step 1: Open the Dashboard
Navigate to [https://iamchiragrao.github.io/my-assets/](https://iamchiragrao.github.io/my-assets/) on your computer.

### Step 2: Connect Your GitHub Token (First Time Only)
To allow the browser to upload files and update your live website, the app needs your GitHub Personal Access Token (PAT):
1. Click the **Enter PAT** button in the top navigation bar.
2. Paste your GitHub PAT into the input field.
3. Click **Save**.
4. The badge will change to a green **PAT Active**. It is securely stored in your browser's `localStorage` and never sent to any third-party server.

---

### Step 3: Upload Videos or Images
1. Click the purple **Upload Asset** button at the top right, or scroll to the dropzone.
2. Choose your destination policy:
   - **🤖 Smart Auto-Route (Recommended)**: Automatically puts files $\le 20\text{ MB}$ into Edge CDN and files $> 20\text{ MB}$ into Release Vault.
   - **⚡ Edge CDN**: Forces upload to Edge CDN (files must be under 20 MB).
   - **📦 Release Vault**: Forces upload to Release Vault (supports files up to 2 GB).
3. Drag and drop your video files into the dashed box, or click to browse from your computer.
4. Click **Start Upload All**.
5. Watch the real-time progress bar. Once completed, your asset appears immediately in the **Asset Vault & CDN** grid.
6. Each card has buttons to:
   - **Copy CDN URL** (for use anywhere).
   - **Copy `<video>` Embed Code** (preconfigured with autoplay, loop, muted, playsinline).
   - **Preview** (watch the video in high quality right on the page).
   - **Delete** (permanently delete from storage).

---

### Step 4: Link Videos to Your Portfolio Website
This is the magic feature! You no longer need to edit any code or JSON files manually to link videos to your portfolio website.

1. Click on the **Portfolio Linker (19 Slots)** tab at the top.
2. You will see:
   - **19 Video Slots**:
     - **13 Carousel Video Slots**: (e.g. *Aesthetic Visual Flow*, *Cinematic Brand Reel*, *Dynamic Motion Cut*, etc.)
     - **6 Content Repurposing Slots**: (e.g. *Podcast Cutdown*, *Twitter/X Hook*, *YouTube Shorts*, etc.)
   - **Top Counter**: Shows how many slots are linked and how many are still unlinked/empty.
   - **Unassigned Media List**: Highlights videos in your vault that haven't been assigned to any slot yet.
3. To assign a video to a slot:
   - Find the slot card (you can use the search bar or filter tabs: *All*, *Unlinked*, *Linked*, *Portfolio*, *Repurposing*).
   - In the slot card, click the dropdown menu **Select uploaded asset to link**.
   - Pick one of your uploaded videos from the list.
4. **Staging Activates Automatically**:
   - A glowing purple banner will appear at the top: `Staging Active: X slot(s) updated and ready to deploy`.
   - The slot card highlights in purple with a `Staged` badge.
   - You can link multiple slots in one session.
5. If you make a mistake, you can:
   - Change the dropdown to a different video,
   - Click the red **✕** icon on the slot to unlink it, or
   - Click **Discard** in the staging banner to reset all pending changes.

---

### Step 5: Preview, Commit & Auto-Deploy
Once you are happy with your slot assignments:
1. Click the glowing **Commit & Auto-Deploy** button in the staging banner (or **Review & Commit**).
2. A **Review Staged Changes & Deploy** modal appears:
   - Shows a clean comparison table: **Slot Title**, **Section**, **Previous Asset**, and **New Staged Asset**.
   - Pre-fills a clean Git commit message (e.g. *Update portfolio video links via My-Assets Linker Studio*), which you can edit if desired.
3. Click **Confirm Commit & Deploy**.
4. The dashboard:
   - Directly commits the updated configuration to `atomik-clone/src/data/portfolio-assets.json` in your `iamchiragrao` repository via the GitHub API.
   - Resets the staging state.
   - Shows a green success toast: `🚀 Changes committed! GitHub Actions is auto-deploying your site.`
5. GitHub Actions automatically starts building your portfolio website. Within 1 to 2 minutes, your live site at [iamchiragrao.github.io](https://iamchiragrao.github.io) will display the new videos!

---

## 🛠 Desktop Video Compression Tool (Optional)

If you export a massive 300MB+ raw video file from Premiere Pro, After Effects, or DaVinci Resolve and want to compress it down to a lightweight 10-15MB web-ready MP4 before uploading:

1. Open your terminal or file explorer to `c:\Projects\iamchiragrao\tools`.
2. Run `compress_and_upload.bat` or drag your video onto the script.
3. It uses FFmpeg with web-optimized settings (`H.264`, `AAC`, `-crf 23`, `faststart` for instant streaming) to reduce file size by 80-90% with zero noticeable loss in visual quality.
4. Alternatively, you can upload raw files up to 2 GB directly to the **Release Vault** without compression!

---

## 🔒 Security & Privacy

- **Your GitHub Token (PAT)** is stored strictly in your browser's private `localStorage`.
- It is **never** sent to any third-party server, analytics, or external API.
- All network requests go directly from your browser to `api.github.com`.
- **Secret Scanning Rule**: Never paste PATs directly into git commits or public chat rooms.

---

## 📋 Summary of Today's Technical Work

1. **Created & Configured `my-assets` Repository**:
   - Initialized public repository `iamchiragrao/my-assets` with GitHub Pages enabled.
   - Configured Anycast jsDelivr CDN endpoint mapping.
   - Created GitHub Release `v1.0-assets` for heavy files up to 2 GB.
2. **Decoupled Website Asset Configuration**:
   - Replaced hardcoded Cloudinary video strings across `Portfolio.tsx`, `VideoStack.tsx`, and `ContentRepurposing.tsx`.
   - Built centralized data schema `atomik-clone/src/data/portfolio-assets.json` (19 total slots).
   - Added elegant unlinked fallback cards so empty slots display cleanly without broken video errors.
3. **Built Full-Featured Web Management Studio**:
   - Modern glassmorphic dark-theme UI with zero npm dependencies (Vue 3 CDN + Tailwind CSS CDN).
   - Smart Auto-Route upload engine supporting drag & drop.
   - Real-time `XMLHttpRequest` progress tracking (30% to 100%).
   - Eliminated redundant network check 404 errors by caching file SHAs in memory.
   - Full staging system with diff inspection and one-click GitHub Actions auto-deployment.
4. **Verified Live End-to-End**:
   - Successfully uploaded `Info__Typo__Branding.mp4` (10.8 MB).
   - Confirmed 200 OK delivery on jsDelivr Edge CDN.
   - Verified GitHub Pages deployments for both `iamchiragrao.github.io` and `iamchiragrao.github.io/my-assets/`.
