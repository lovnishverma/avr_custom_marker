# AR Smart Switch Controller 🎛️

A lightweight WebXR application that turns a physical paper marker into a virtual smart home switch. Built with **AR.js** and **A-Frame**, this project detects a custom marker via the device camera and sends control signals to a remote server to toggle appliances on or off.

## 🚀 Features

- **Instant AR Detection:** Uses a custom pattern marker (`pattern-nielit.patt`) to trigger events.
- **Smart Debouncing:** Prevents accidental toggling when the camera loses focus—includes a 2-second buffer before sending an "OFF" signal.
- **Real-time Feedback:**
  - **Visual:** 3D box changes color (Green = ON, Red = OFF).
  - **Status Overlay:** On-screen text indicates connection status (Scanning, Syncing, Device ON/OFF).
- **Error Handling:** Visual indicators if the server connection fails.
- **Mobile Optimized:** VR mode disabled for a clean, full-screen AR experience.

## 🛠️ Tech Stack

- **Frontend:** HTML5, CSS3, JavaScript (ES6+)
- **AR Engine:** [AR.js](https://github.com/AR-js-org/AR.js) + [A-Frame](https://aframe.io/)
- **Backend Communication:** Fetch API (talking to a Node.js/Glitch server)

## 📂 Project Structure

```text
📦 avr_custom_marker
 ┣ 📜 index.html           # Main application logic and AR scene
 ┣ 📜 pattern-nielit.patt  # Custom AR marker pattern file
 ┗ 📜 README.md            # Project documentation

```

## ⚙️ Setup & Installation

### 1. The Marker

You need the physical marker to trigger the switch.

1. Download the `pattern-nielit.patt` file from this repository.
2. Print the corresponding marker image (usually a thick black border with a custom inner design).
3. Place it on a flat surface.

### 2. The Backend (Glitch)

This frontend communicates with a Glitch server. Ensure your backend is running and supports **CORS**.

* **Endpoint:** `https://roomcontrol.glitch.me/toggle-app`
* **Required Query Param:** `?state=on` or `?state=off`

**Important:** Your server *must* include these headers to allow requests from GitHub Pages:

```javascript
res.header("Access-Control-Allow-Origin", "*");
res.header("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept");

```

### 3. Deploying to GitHub Pages

1. Go to your repository **Settings**.
2. Click on **Pages** in the left sidebar.
3. Under **Branch**, select `main` (or `master`) and `/root`.
4. Click **Save**.
5. Wait a few moments, and GitHub will provide your live URL (e.g., `https://lovnishverma.github.io/avr_custom_marker/`).

## 🖥️ Usage

1. Open the deployed GitHub Pages URL on a mobile device or webcam-enabled computer.
2. Allow camera permissions when prompted.
3. Point the camera at the **NIELIT Marker**.
* **Marker Found:** The 3D box appears, turns **GREEN**, and sends an "ON" request.
* **Marker Lost:** A 2-second timer starts. If the marker is not found again, the system sends an "OFF" request.



## 🐛 Troubleshooting

| Issue | Cause | Fix |
| --- | --- | --- |
| **Camera not opening** | HTTP instead of HTTPS | Ensure you are using the `https://` version of your GitHub Pages link. |
| **Box is Gray/Orange** | Connection Error | Check if the Glitch server is awake. Check the browser console for CORS errors. |
| **Flickering ON/OFF** | Poor Lighting | Use the app in a well-lit room. The built-in "Debounce" feature handles minor flickers. |
| **Marker not detecting** | White borders | Ensure the printed marker has a sufficient white border around the black square. |

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](https://www.google.com/search?q=https://github.com/lovnishverma/avr_custom_marker/issues).

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](https://www.google.com/search?q=LICENSE) file for details.

---

*Created by [Lovnish Verma*](https://github.com/lovnishverma)
