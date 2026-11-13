# 手势粒子 · Hand Particle

手势交互粒子动画 —— 单文件完整实现。

## 功能

- 摄像头捕捉手掌，MediaPipe Hands 识别掌心坐标
- 手掌移动持续发射彩色粒子，跟随掌心流动
- 粒子半透明、色彩渐变、互相轻微吸引、缓慢飘散
- 深色纯黑背景 + 加法混合，粒子高亮发光

## 运行要求

需要联网 + 摄像头权限 + 安全上下文（HTTPS / localhost / 多数浏览器的 `file://`）。

若双击打开后一直无法识别，请改用本地服务器：

```bash
python -m http.server 8080
```

然后浏览器访问 http://localhost:8080

## 性能优化

- 多 CDN 容错：fastly → gcore → jsdelivr
- 摄像头授权与脚本/模型下载并行，缩短等待
- MediaPipe lite 模型 + 480x360 低分辨率，识别更快
- DPR 上限 1.5，HiDPI 屏下渲染更快更稳
