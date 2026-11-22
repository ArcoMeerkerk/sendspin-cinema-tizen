# Sendspin Cinema Player for Samsung Tizen OS 🎬🎵

A beautiful, minimalistic, cinema-inspired web player for **Music Assistant**. This application is designed specifically for Samsung Tizen smart TVs.

## ✨ Features
* **Cinema Aesthetic:** Dark, immersive background with a glowing progress bar.
* **Dynamic Colors:** Automatically extracts the dominant color from the album art and adapts the UI accent color (powered by Vibrant.js).
* **Plug & Play:** Easy setup right from the TV screen.

## 🚀 Installation Guide

### Option A: TizenBrew module (no Tizen Studio needed)
This repository is a TizenBrew *application module* (see `package.json`). Nothing is installed on the TV itself: [TizenBrew](https://github.com/reisxd/TizenBrew) downloads the files from this GitHub repository through the jsDelivr CDN every time you launch it, so the TV needs internet access and the repository must be public.

**Requirements:** a Samsung TV from 2017 or newer (Tizen 3.0+) and TizenBrew installed on it. If you don't have TizenBrew yet, follow the [official TizenBrew guide](https://github.com/reisxd/TizenBrew/blob/main/docs/README.md) (preferred method: TizenBrew Installer Desktop).

**1. Set up the TV for TizenBrew** (only if you haven't already)
1. On the TV open **Apps** and enter `12345` with the remote.
2. Switch **Developer mode** to **On**.
3. While installing TizenBrew from your PC, set **Host PC IP** to your PC's IP address.
4. After TizenBrew is installed, set **Host PC IP** to `127.0.0.1`, press **OK** and fully restart the TV (hold the power button until you see the Samsung logo). TizenBrew cannot launch modules until this is done.

**2. Add the module**
1. Open **TizenBrew** on the TV.
2. Open the **Module Manager** (the archive-box icon at the top right, or the GREEN button on the remote).
3. Choose **Add GitHub Module**.
4. Type `ArcoMeerkerk/sendspin-cinema-tizen` (just `user/repo`, TizenBrew adds the `gh/` prefix itself; use your own `user/repo` if you forked this project).
5. Confirm the input and leave the text field (for example press **Enter** on the on-screen keyboard and then **Return**). The module is added when the field loses focus, and **Sendspin Cinema** should now appear in the Module Manager. If it is listed as *Unknown Module*, the name is wrong or the repository is not public.

**3. Launch it**
1. Go back to the TizenBrew home screen (house icon) and select **Sendspin Cinema**.
2. On first launch enter the IP address of your Music Assistant server and a player name, then press **Enter** on the second field. These values are stored on the TV.
3. Optional: in TizenBrew **Settings** -> **Autolaunch Settings** you can pick Sendspin Cinema to start automatically whenever TizenBrew is opened.

**Updating / removing**
* Updates are picked up automatically; jsDelivr caches the default branch for up to 12 hours. Don't publish GitHub releases/tags unless you want to pin a version: once a release exists, jsDelivr serves the latest release instead of the branch and caches that for up to 7 days.
* To remove the module, select it in the **Module Manager** and confirm the prompt.

### Option B: Standalone `.wgt`
Because this is a custom web application, it can also be packaged and installed using Tizen Studio tools.

1. Ensure your Samsung TV is in **Developer Mode** and connected to your local network.
2. Build the signed `.wgt` package using the Tizen CLI or Tizen Studio IDE.
3. Deploy the application to your TV using the Device Manager.

## ⚠️ Important Note for Music Assistant
When you first launch the app, Music Assistant may hide the new player by default. 
1. Open your Music Assistant interface.
2. Go to **Settings** -> **Players**.
3. Find your newly registered TV (check Disabled/Hidden lists).
4. Uncheck **"Hide this player in the user interface"**.

## ☕ Support the Project
If this app made your home theater experience better, consider buying me a coffee! 

[![Ko-fi](https://img.shields.io/badge/Ko--fi-F16061?style=for-the-badge&logo=ko-fi&logoColor=white)](https://ko-fi.com/zonya2026)
