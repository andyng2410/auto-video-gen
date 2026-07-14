# BCT Global — Design Tokens (áp dụng vào video)

Trích xuất từ <https://bigcloudtech.global/> (logo SVG + CSS bundle Next.js) và ánh xạ vào
hệ motion-graphic 9:16 của repo. Theme mới: **`bct`** (`VIDEO_THEME=bct`).

## 1. Token gốc

| Token | Hex | Nguồn |
|---|---|---|
| Brand blue (logo) | `#3370FF` | `bct-logo.svg` — `rgb(51,112,255)` |
| Brand green (logo) | `#7FD858` | `bct-logo.svg` — `rgb(127,216,88)` |
| Primary blue (web) | `#2563EB` | blue-600, CTA chính |
| Primary blue dark | `#1D4ED8` | blue-700, hover |
| Navy | `#1E3A5F` | stop của gradient chữ ký |
| Navy deep / slate | `#0B1220` · `#0F172A` | nền tối |
| Ink (text) | `#111827` | gray-900 |
| Green (web) | `#22C55E` | green-500 |
| Teal (phụ) | `#14B8A6` | teal-500 |
| Surface sáng | `#F9FAFB` | gray-50 |
| **Gradient chữ ký** | `linear-gradient(135deg, #1E3A5F 0%, #2563EB 100%)` | navy → blue |

## 2. Ánh xạ vào hệ 2-accent của video

Hệ motion cũ (`dark-neon`) dùng **cyan + tím**. Logo BCT vốn đã là **xanh dương + xanh lá**,
khớp đúng cấu trúc 2 accent nên map 1-1:

| Vai trò | dark-neon (cũ) | → BCT |
|---|---|---|
| Nền | navy `#0a1628` | slate navy `#0B1220 → #1E3A5F` |
| Accent 1 (primary) | cyan `#22d3ee` | blue `#3370FF` / `#2563EB` |
| Accent 2 (secondary) | tím `#a855f7` | green `#7FD858` / `#22C55E` |
| Viền feature/callout | cyan→tím | blue→green |
| Outro | gradient tím | gradient chữ ký navy→blue, gạch chân green→blue |

TikTok follow button giữ đỏ `#fe2c55` (brand TikTok, không đổi).

## 3. Hai theme BCT (thiết kế "anti-AI-slop")

Cùng bộ token, khác nền. Cả hai bỏ hẳn: glow neon, glassmorphism, orb gradient
trôi, viền gradient cầu vồng, font Anton nén. Thay bằng: bề mặt đặc + hairline 1px,
bóng đổ thật (không phải quầng sáng), 1 thanh accent phẳng, **Inter** toàn bộ,
canh **lề trái editorial**, xanh lá dùng rất tiết chế làm điểm nhấn.

| Theme | Nền | Khi nào dùng |
|---|---|---|
| `bct` | navy tối phẳng `#0B1220→#1E3A5F` | feed TikTok/Shorts, dễ nổi bật |
| `bct-light` | trắng/slate như website | corporate B2B, sát brand nhất |

```bash
VIDEO_THEME=bct       npm run pipeline -- output/<slug>/script.json   # dark phẳng
VIDEO_THEME=bct-light npm run pipeline -- output/<slug>/script.json   # light
```

Token khai báo ở `:root` đầu mỗi file (`styles.bct.css` / `styles.bct-light.css`):
`--bct-blue`, `--bct-green`, `--brand-grad`, `--surface`, `--hairline`, `--elev`…

Scene hook (khi có ảnh nền) dùng **scrim gradient neo trái** kiểu lower-third bản
tin để chữ luôn đọc rõ trên mọi ảnh — không phải nền phẳng đè kín.
