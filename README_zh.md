# BSP 3D Control

[English](README.md) | 中文

本项目是基于 [Quectel Pi 智能单板计算机](https://www.quectel.com.cn/quectel-pi/documentation-center)实现的手势识别远程视频控制演示。
系统通过摄像头采集手部图像，并使用 AI 手势识别算法，实现对视频播放、进度和音量的非接触式控制，带来自然直观的交互体验。

![](docs/assets/main.jpg)

## 功能特性

- 实时监控 GPIO 引脚并查看状态
- 交互式引脚图，映射至 Quectel Pi M2 扩展接口
- 实时显示信号状态和值
  - 逻辑电平（高 / 低）
  - 引脚方向和模式（输入 / 输出 / 复用功能）
  - 外设总线映射（I2C、SPI、UART、PWM、ADC）
- 硬件状态变化和信号触发时即时提供视觉反馈
- 直观的引脚选择和元数据查询，便于快速原型开发
- 直接在硬件层执行：无需外部调试器即可实现零延迟诊断

## 项目结构

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

- `src/app.py` — Flask 应用及 GPIO 状态处理
- `src/m2.html` — 开发板可视化界面
- `src/m2-*.png` — 界面使用的 Quectel Pi M2 开发板图片
- `install.sh` — 安装系统和 Python 依赖
- `docs/` — 项目图片和演示视频

## 硬件要求

- Quectel Pi M2 单板计算机
- GPIO 接线扩展板

### 软件要求

- 操作系统：Debian 13（Quectel Pi M2 出厂镜像，无需重新刷写）
- Python 3.9 或更高版本；可选使用 `venv`，且运行时无需第三方依赖
- 浏览器：内置浏览器；2D 视图需要 WebGL
- 当前用户必须属于 `i2c` 组；安装程序会检查此项并提供提示

## 🚀 安装与运行

1. 在开发板上安装 git，并将仓库克隆到 `~/projects/`：
```bash
sudo apt update
sudo apt install -y git
cd ~/projects
git clone https://github.com/Quectel-Pi/demo-bsp-3d-control.git
```

2. 进入项目目录并运行部署脚本：

```bash
cd ~/projects/demo-bsp-3d-control
./install.sh
```

3. 进入 `src` 目录，并使用 sudo 权限运行 `app.py`。访问 GPIO 数值和状态需要 sudo 权限。

```bash
cd demo-bsp-3d-control/src/
sudo python3 app.py
```
然后在浏览器中打开 http://localhost:5050

## 演示
▶ **[观看演示视频](docs/demo.mp4)**（约 60 秒）

## 📮 问题反馈

如果遇到问题，请在 [Quectel Pi 开发者论坛](https://forumschinese.quectel.com/c/quectel-pi/58)发布技术问题，我们的支持团队将为您提供帮助。欢迎提交有助于改进本项目的问题反馈和拉取请求。