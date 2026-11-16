# BSP 3D Control

[中文](README_zh.md) | English

This project is a gesture-recognition–based remote video control demo implemented on the [Quectel Pi Smart Single-Board Computer](https://www.quectel.com.cn/quectel-pi/documentation-center).
The system captures hand images through a camera and applies AI-based hand gesture recognition algorithms to enable touchless control of video playback, progress, and volume, providing a natural and intuitive user interaction experience.

![](docs/assets/main.jpg)

## Features

- Real-time GPIO pin monitoring and status inspection
- Interactive pinout visualization mapped to the Quectel Pi M2 expansion header
- Live signal state and value readouts
  - Logic levels (High / Low)
  - Pin direction and mode (Input / Output / Multiplexed functions)
  - Peripheral bus mappings (I2C, SPI, UART, PWM, ADC)
- Instant visual feedback for hardware state changes and signal triggers
- Intuitive pin selection and metadata lookup for rapid prototyping
- Direct hardware-level execution: zero-latency diagnostics with no external debugger required

## Project Structure

```text
demo-bsp-3d-control/
├── docs/
│   ├── assets/
│   │   └── main.jpg
│   └── demo.mp4
├── src/
│   ├── app.py
│   ├── m2.html
│   ├── m2-back.png
│   └── m2-front.png
├── install.sh
├── LICENSE
├── README.md
└── README_zh.md
```

- `src/app.py` — Flask application and GPIO status handling
- `src/m2.html` — board visualization interface
- `src/m2-*.png` — Quectel Pi M2 board images used by the interface
- `install.sh` — installs the system and Python dependencies
- `docs/` — project images and demo video

## Hardware Requirements

- Quectel Pi M2 single-board computer
- GPIO terminal expansion board

### Software

- OS: Debian 13 (the Quectel Pi M2 factory image; no reflash needed)
- Python 3.9 or newer; `venv` is optional and there are no third-party runtime dependencies
- Browser: Built in browser; the 2D view needs WebGL
- The current user must belong to the `i2c` group; the installer checks this and prints a hint

## 🚀 Installation and running

1. On the board, install git and clone the repository into `~/projects/`:
```bash
sudo apt update
sudo apt install -y git
cd ~/projects
git clone https://github.com/Quectel-Pi/demo-bsp-3d-control.git
```

2. Enter the project and run the deployment helper:

```bash
cd ~/projects/demo-bsp-3d-control
./install.sh
```

3. Navigate to the src directory and run app.py to start the program with sudo permission. We need sudo to access gpio values and status.

```bash
cd demo-bsp-3d-control/src/
sudo python3 app.py
```
Then open the url in the browser http://localhost:5050

## Demo
https://github.com/user-attachments/assets/e9471b07-bac5-4fa0-bbe2-1f94c9006a3a

## 📮 Reporting issues

If you run into a problem, post a technical question in the [Quectel Pi developer forum](https://forumschinese.quectel.com/c/quectel-pi/58); our support team will help. Issues and pull requests that improve this project are welcome.

