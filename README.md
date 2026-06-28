# 水杯圖示說明文件 (Water Cup Icon Guide)

本目錄包含了一個設計簡約的「水杯裡面有水」圖示，提供 **SVG (向量格式)** 與 **PNG (512x512 高解析度格式)** 兩種版本。這些圖示非常適合用於網頁的 Favicon、PWA (Progressive Web App) 以及打包成手機 App 時的啟動圖示。

## 📂 檔案清單
- **[water-cup.svg](file:///g:/%E6%88%91%E7%9A%84%E9%9B%B2%E7%AB%AF%E7%A1%AC%E7%A2%9F/google%20IDK/water-cup-icon/water-cup.svg)**: 向量格式圖示。可無限放大不失真，適合現代網頁 Favicon。
- **[water-cup-512x512.png](file:///g:/%E6%88%91%E7%9A%84%E9%9B%B2%E7%AB%AF%E7%A1%AC%E7%A2%9F/google%20IDK/water-cup-icon/water-cup-512x512.png)**: 512x512 像素 PNG 格式圖示。適合用作 App 圖示、PWA splash 畫面或舊版瀏覽器相容圖示。

---

## 🌐 網頁 HTML 設定方式

在您的網頁 HTML `<head>` 標籤中，加入以下程式碼即可顯示此圖示：

```html
<!-- 現代瀏覽器優先使用 SVG 向量圖示 -->
<link rel="icon" type="image/svg+xml" href="path/to/water-cup.svg">

<!-- 針對不支援 SVG 的舊版瀏覽器使用 PNG -->
<link rel="alternate icon" type="image/png" href="path/to/water-cup-512x512.png">

<!-- iOS Safari 桌面捷徑圖示 (Apple Touch Icon) -->
<link rel="apple-touch-icon" href="path/to/water-cup-512x512.png">
```

---

## 📱 行動版網頁 / PWA (Progressive Web App) 設定

如果您想讓網頁在手機上可以「加入主畫面」並像 App 一樣顯示，您需要建立一個 `manifest.json` 檔案：

```json
{
  "name": "我的水杯 App",
  "short_name": "水杯 App",
  "start_url": ".",
  "display": "standalone",
  "background_color": "#f0f9ff",
  "theme_color": "#0ea5e9",
  "icons": [
    {
      "src": "path/to/water-cup-512x512.png",
      "sizes": "512x512",
      "type": "image/png",
      "purpose": "any maskable"
    }
  ]
}
```
並在 HTML 中引入它：
```html
<link rel="manifest" href="manifest.json">
```

---

## 📦 打包成手機 App (iOS / Android) 建議圖示尺寸

如果您後續要使用 **Capacitor**、**Cordova**、**Flutter** 或 **React Native** 將網頁打包成手機 App，系統會要求您提供不同解析度的圖示。

建議使用 `water-cup-512x512.png` 作為來源，並使用圖示生成工具（例如 [App Icon Generator](https://appicon.co/) 或 `cordova-res` / `@capacitor/assets`）自動裁切出以下常用規格：

### 🤖 Android 常用尺寸
Android 需要圓形與適應性圖示 (Adaptive Icons)，主要存放在 `res/mipmap-...` 目錄中：
- **mdpi**: 48x48 px
- **hdpi**: 72x72 px
- **xhdpi**: 96x96 px
- **xxhdpi**: 144x144 px
- **xxxhdpi**: 192x192 px
- **Play Store 圖示**: 512x512 px (即本目錄下的 PNG 版本)

### 🍎 iOS 常用尺寸
iOS 圖示定義在 `AppIcon.appiconset` 的 `Contents.json` 中：
- **iPhone Notification**: 20pt (40x40, 60x60 px)
- **iPhone Settings**: 29pt (58x58, 87x87 px)
- **iPhone Spotlight**: 40pt (80x80, 120x120 px)
- **iPhone App Icon**: 60pt (120x120, 180x180 px)
- **iPad App Icon**: 76pt (152x152 px) & 83.5pt (167x167 px)
- **App Store 圖示**: 1024x1024 px (可將 SVG 放大匯出為 1024x1024 PNG 使用)
