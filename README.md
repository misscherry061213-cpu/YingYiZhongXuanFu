# 英译中悬浮 (YingYiZhongXuanFu)

Android 屏幕英译中工具：截屏 OCR 识别英文 → 顶部悬浮窗显示简体中文译文。

## 功能

- **点击翻译**：截屏 → ML Kit OCR 识别英文 → 顶部浮窗显示简体中文
- **自动翻译**：定时检查画面，内容变化后自动更新译文
- **停止入口**：顶部悬浮窗 + 通知栏均可停止
- **翻译引擎**：优先 ML Kit 离线英→简中，失败时尝试在线备用

## 使用方法

1. 安装 APK 后打开 App
2. 授予「显示在其他应用上层」权限
3. （Android 13+）授予通知权限
4. 点击「启动翻译服务」，允许屏幕录制权限
5. 顶部会出现译文浮窗：
   - 点击「翻译」立即识别当前屏幕
   - 点击「自动」开启/关闭自动模式
   - 点击「停止」结束服务
6. 通知栏也有「立即翻译」和「停止」按钮

## 技术栈

- Kotlin
- MediaProjection（截屏）
- Google ML Kit Text Recognition（OCR）
- Google ML Kit On-Device Translation（离线翻译）
- WindowManager 悬浮窗
- Foreground Service + Notification

## 构建

### 本地构建

1. 用 Android Studio 打开本项目
2. 等待 Gradle 同步完成
3. 连接设备或模拟器，点击 Run

首次运行时 ML Kit 翻译模型会在 WiFi 下自动下载。

### GitHub Actions

推送到 `main` / `master` 分支后会自动编译 Debug APK，可在 Actions 页面下载 Artifact。

## 注意事项

- 需要 Android 8.0（API 26）及以上
- 截屏权限属于敏感权限，系统会每次询问（部分系统可记住）
- 自动模式会定期截屏，建议按需开启以节省电量
- 在线翻译备用接口仅作演示，生产环境请替换为正规 API

## 许可证

MIT
