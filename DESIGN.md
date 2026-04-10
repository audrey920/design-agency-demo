# DESIGN.md — Claude Code + Stitch 2.0 Demo

> 設計系統藍圖，供 Claude Code 延伸生成新頁面時保持設計一致性使用。
> Stitch Project ID: `16394899780282003985`

---

## 專案概覽

| 項目 | 值 |
|------|-----|
| 專案名稱 | Claude Code + Stitch 2.0 Demo |
| 裝置類型 | Desktop（1280px–2560px） |
| 色彩模式 | Dark Mode |
| 設計風格 | 科技感、深色、現代 |

**頁面結構：**
1. Hero & Navigation
2. Service Details
3. Works Portfolio
4. Testimonials
5. FAQ

---

## 色彩系統

### 基礎色盤

```css
/* Background Layers */
--color-bg:        #020617;  /* slate-950 — 最深背景 */
--color-surface:   #0f172a;  /* slate-900 — 卡片背景、次層 */
--color-elevated:  #1e293b;  /* slate-800 — 懸浮元件、border */

/* Text */
--color-text-muted:  #64748b;  /* slate-500 — 次要文字 */
--color-text-subtle: #94a3b8;  /* slate-400 — 說明文字、placeholder */
--color-text-base:   #f8fafc;  /* slate-50  — 主要文字 */

/* Accent */
--color-accent:      #0de7f2;  /* cyan — 品牌主色，來自 Stitch 設定 */
--color-blue:        #3b82f6;  /* blue-500 — 互動元素 */
--color-blue-light:  #60a5fa;  /* blue-400 — hover 狀態 */
```

### 使用原則
- 背景永遠使用 `#020617`，不使用純黑 `#000000`
- Accent `#0de7f2` 僅用於品牌強調、CTA、highlight，不過度使用
- 卡片統一用 glass-card 樣式，保持視覺層次感

---

## 字體系統

### 字型

```css
font-family: 'Space Grotesk', sans-serif;
```

> Google Fonts 引入：`https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&display=swap`

### 字級規範

| 用途 | 大小 | 字重 | 備註 |
|------|------|------|------|
| Hero 標題 | 4rem–6rem | 700 | 搭配漸層色或 accent |
| Section 標題 | 2.25rem–3rem | 600–700 | |
| 卡片標題 | 1.25rem–1.5rem | 600 | |
| 內文 | 1rem | 400 | line-height: 1.6 |
| 說明 / Caption | 0.875rem | 400 | color: slate-400 |
| 按鈕 | 0.875rem–1rem | 500–600 | uppercase 或 normal |

---

## 圓角系統

```css
--radius-sm:   0.25rem;   /* 預設，小元件 */
--radius-md:   0.5rem;    /* 卡片、輸入框 */
--radius-lg:   0.75rem;   /* 大型卡片、模態框 */
--radius-full: 9999px;    /* 標籤、徽章、圓形按鈕 */
```

---

## 元件規範

### Glass Card

```css
.glass-card {
  background: rgba(15, 23, 42, 0.6);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  border: 1px solid rgba(255, 255, 255, 0.05);
  border-radius: 0.75rem;
}
```

### 背景網格裝飾

```css
.grid-pattern {
  background-image: radial-gradient(rgba(59, 130, 246, 0.1) 1px, transparent 1px);
  background-size: 40px 40px;
}
```

### 按鈕

**Primary CTA（Get Started / Initiate Project）**
```css
/* 亮底深字 或 accent 邊框風格 */
background: #0de7f2;
color: #020617;
font-weight: 600;
padding: 0.75rem 1.5rem;
border-radius: 0.5rem;
```

**Secondary / Ghost**
```css
background: transparent;
border: 1px solid rgba(255, 255, 255, 0.1);
color: #94a3b8;
padding: 0.75rem 1.5rem;
border-radius: 0.5rem;
```

**Learn More（箭頭型）**
```html
<a>Learn More <span class="material-symbols-outlined">arrow_forward</span></a>
```

### Navigation

```
[Logo] ............. [Portfolio] [Services] [Testimonials] [FAQ] ........ [Get Started]
```
- 背景：`rgba(2, 6, 23, 0.8)` + `backdrop-filter: blur`
- 黏性定位（sticky top）
- 行動版需漢堡選單

### Service Card（服務卡片）

```
[ Icon ]
[ 標題 ]
[ 描述文字 ]
[ Learn More → ]
```
- 採用 glass-card 樣式
- Icon 使用 Material Symbols Outlined
- 四欄 Grid 排版：`grid-cols-2 lg:grid-cols-4`

---

## 圖示系統

```html
<link href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@24,400,0,0" rel="stylesheet" />
```

常用 Icons：
- `layers` — UI/UX Design
- `terminal` — 開發相關
- `search_insights` — SEO
- `speed` — 效能
- `arrow_forward` — CTA 連結

---

## 頁面佈局

### 容器寬度
```css
.container {
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 1.5rem;
}
```

### Section 間距
```css
section {
  padding: 5rem 0;  /* py-20 */
}
```

### 各頁面 Section 結構

| 頁面 | 包含區塊 |
|------|----------|
| Hero & Navigation | Navbar、Hero（標題 + 副標 + CTA + 裝飾背景） |
| Service Details | 服務介紹（4格 Grid）、功能列表 |
| Works Portfolio | 作品集卡片（Grid） |
| Testimonials | 客戶評價卡片 |
| FAQ | 手風琴式問答 |

---

## 延伸新頁面的注意事項

1. **永遠使用 dark mode**，背景從 `#020617` 開始
2. **Accent 色 `#0de7f2`** 僅用於強調，避免大面積使用
3. **新 Section** 統一用 `py-20`（5rem）間距
4. **卡片** 一律套用 `.glass-card` 樣式
5. **字型** 統一 Space Grotesk，不混用其他字體
6. **圖示** 統一 Material Symbols Outlined
7. **按鈕** 遵循 Primary / Secondary 兩種規格，不自創變體
