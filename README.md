# Sony-Film_Simulation
This is the Open Memories application, which allows users to add any film simulation they like in the form of LUTs (Look-Up Tables). It has been tested and confirmed to be fully compatible with Sony A6000.
# Film Simulation v1 — Free Edition
An embedded in-camera application for **Sony Alpha mirrorless cameras** (Sony A6000 / ILCE-6000 and PMCA-compatible bodies) that bridges the color science of the **Fujifilm X-T5** directly onto Sony's native hardware image processor (**BIONZ X ISP**).
Capture authentic, film-like JPEG photographs **Straight Out Of Camera (SOOC)** with zero computer post-processing required.
---
## 1. Overview & Architecture
* **Hardware-Level ISP Integration:** Unlike smartphone filter apps or RAW desktop post-processing presets, Film Simulation runs natively on the camera's internal operating environment. It maps 3D Look-Up Table (LUT) color profiles directly to Sony hardware registers via `CameraEx` APIs and a high-performance ARM native C core (`liblutcore.so`).
* **Instant In-Camera JPEG Rendering:** Live View previews and captured images are rendered by the camera's image processor in real time, saving finished film photos straight to your SD card.
* **Dual-Display Architecture (`ScreenMode`):** Takes full advantage of the camera's physical Eye Sensor:
  * **Rear LCD Screen (`EditorView`):** Functions as a clean, high-contrast parameter status dashboard without obscuring the live composition.
  * **Electronic Viewfinder (EVF):** Displays an uncluttered, full-screen Live View feed with real-time film color and a minimal single-line status HUD.
---
## 2. Key Features in the Free Edition
### 16 Built-in Iconic Film Simulation Presets
Pre-loaded with 20 calibrated color profiles reverse-engineered from Fujifilm looks:
* **Classic Chrome:** Muted tones, deep shadow contrast, and distinctive teal skies—tailored for street and documentary photography.
* **Classic Neg:** Emulates vintage Superia color film with punchy contrast and characteristic magenta/green shifts.
* **Provia (Standard):** Natural, faithful color balance suitable for everyday general photography.
* **Velvia (Vivid):** Rich, saturated colors and crisp contrast, engineered for landscapes, nature, and sunsets.
* **Astia & Pro Neg (Hi / Std):** Soft contrast gradations and optimized skin tones for portraiture.
* **Eterna (Cinema):** Flat, gentle cinematic look with wide dynamic range and smooth highlight rolloff.
* **Monochrome & Acros:** Deep, tonal black-and-white renditions with rich gradations.
* **Creative Looks:** *Filmstock 50, Fuji 3510, AeroLux, Bleach Bypass, Teal Orange Contrast, and Tension Green*.
### 6-Axis Hardware Color Depth Tuning
Adjust color saturation and intensity directly on the sensor across 6 independent channels:
* **Channels:** Red (R), Green (G), Blue (B), Cyan (C), Magenta (M), and Yellow (Y).
* **Adjustment Range:** Fully adjustable within $[-3 \dots +3]$ steps.
### In-Camera Shooting & Composition Tools
Shoot directly inside the application without returning to the default camera menu:
* **In-App Shutter Trigger:** Supports half-press (S1) for Autofocus lock and full press (S2) to capture and write JPEG photos directly to SD card.
* **Interactive Focus Picker & Zone AF:** Reposition your focus point across the frame using the D-pad and monitor your focus boundary via real-time graphical overlay (`FocusOverlayView`).
* **Live Exposure & Framing:** Real-time Live Histogram, multi-format composition grids (Rule of Thirds, square grid), live battery percentage readout, and exposure compensation indicators.
* **Creative Camera Controls:** Real-time White Balance (Kelvin & Amber-Blue / Green-Magenta tint shift), Saturation, Contrast, Sharpness, and Sony Dynamic Range Optimizer (DRO/HDR).
---
## 3. Quick-Start User Guide
### Launching the Application
1. Turn on your Sony A6000.
2. Press **[MENU]** $\rightarrow$ Navigate to the **[Application]** tab $\rightarrow$ Open **Application List**.
3. Select **Film Simulation Free**.

### Physical Button Controls & Key Mapping
* **[C1] Button:** Opens the quick **Film Simulation Picker** popup.
* **Control Wheel / D-Pad [UP / DOWN]:** Navigate between parameter rows on the LCD dashboard (Film Look, White Balance, Color Depth axes, Saturation, Contrast, Sharpness).
* **Control Wheel / D-Pad [LEFT / RIGHT]:** Increase or decrease the value of the active parameter tile.
* **Center [ENTER] Button:** Confirm selection / Commit changes.
* **[C2 / Trash] Button:** Quick-reset the highlighted parameter back to its preset default.
* **[MENU] Button:** Cancel active changes / Restore previous values.
* **Shutter Button:** Half-press (S1) to lock autofocus; full press (S2) to capture the photo.

### Shooting Workflow
1. Select your desired Film Simulation preset on the LCD (e.g., *Classic Chrome* or *Astia*).
2. Look through the **EVF**: the camera's eye sensor automatically activates Live View with real-time film colors.
3. Check composition and exposure using the EVF grid and live histogram.
4. Press the shutter button to shoot. Your film simulation JPEG is immediately saved to the SD card.

---

## 4. Free Edition Limitations vs. Premium Edition

| Feature | Free Edition (`v1.0.0`) | Premium Commercial Edition |
| :--- | :--- | :--- |
| **Price** | Free / Community | **$5 USD per camera (Lifetime License)** |
| **External LUT (.cube/.xmp) Import** | Disabled (Built-in presets only) | **Unlimited 3D `.cube` & `.xmp` loading from SD** |
| **Custom Recipe Storage** | Resets on preset switch | **Unlimited `.FSP` saves with In-Camera Soft Keyboard** |
| **Out-of-Bounds Notification** | Toast prompt: *"Vui lòng mua bản Premium"* | Clean, unrestricted UI |
| **Installation Method** | Manual APK sideload via PMCA | **Automated 1-Click EXE Installer (`.exe`)** |

> [!NOTE]
> When adjusting Color Depth beyond $\pm 3$ or accessing Tone Curve options in the Free Edition, the app displays:
> * On LCD: *"Vui lòng mua phiên bản Premium để mở khóa"* / *"Vui lòng mua bản Premium để tiếp tục"*
> * On EVF: `"PREMIUM ONLY"`

---

## 5. Why Upgrade to Premium? ($5 / Camera Body)

For just **$5 USD (one-time payment per camera serial number)**, unlock the complete potential of your camera:
1. **Full Hardware Dynamic Range $[-7 \dots +7]$:** Create deep vintage tones, bold cinematic greens, or delicate baby-soft skin tones impossible within the $\pm 3$ boundary.
2. **Custom Tone Curve Control (Highlights & Shadows):** Fine-tune highlight rolloff and shadow depth just like Fujifilm recipe cards.
3. **Unlimited 3D LUT Loading from SD Card:** Drop any commercial or Hollywood 3D `.cube` / Adobe `.xmp` LUT into `/FILMSIM/CUBE/` on your SD card for instant in-camera shooting.
4. **Custom Recipe Saving & In-Camera Virtual Keyboard:** Craft and name your own signature color recipes (e.g., `PORTRAIT_WARM`, `STREET_BW`) directly on the camera screen.
5. **Zero-Hassle 1-Click Installer (`.exe`):** Simply plug your camera in via USB and run your serial-licensed installer. No command-line tools or technical setup needed.

---

## 6. Technical Specifications & Verified Build Info

* **Package Name:** `com.filmsimulation`
* **Version Name:** `1.0.0-free` (Version Code: `100`)
* **Output APK:** `FilmSimulation_Free_v1.0.0.apk`
* **File Size:** 205,615 bytes
* **SHA-256 Checksum:** `db0cea792ff49ca8d1d8a18fbc175e911d5ba2c0143086b641ae35a9585f6554`
* **Certificate Signature (Pinned Lab Key):** `f33fc1421cbc7d3d08dbf684079ad39b320be7ac3cc0148b1d2ba0966e31e919`
* **Native C Engine:** `lib/armeabi/liblutcore.so`
* **Automated Test Results:**
  * `host_tests`: 88/88 PASS (0 fail)
  * `xmp_tests`: 26/26 PASS (0 fail)
  * `filmsim_tests`: 51/51 PASS (0 fail)
  * `safety_tests`: 88/88 PASS (0 fail)
  * `dex_scan`: 0 security issues / 0 prohibited APIs

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
