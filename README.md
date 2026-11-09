# FORM — Calisthenics

Website tập Calisthenics cho người mới, giao diện bài học toàn màn hình. Có buổi tập ngày 1 và ngày 2, minh họa SVG động, nút bài trước/bài tiếp theo, đồng hồ tập/nghỉ và lưu tiến độ bằng localStorage trên từng trình duyệt.

## Chạy local

Yêu cầu Node.js 22.13 trở lên.

```bash
npm ci
npm run dev
```

## Build

```bash
npm run build
npm run preview
```

## Deploy Cloudflare Workers

Đã cấu hình Workers Static Assets trong `wrangler.jsonc`, Worker tên `farm`, custom domain `2k1.me`.

```bash
npx wrangler login
npm run deploy
```

`2k1.me` phải thuộc account Cloudflare đã khai báo. Domain gốc hiện có CNAME tới Cloudflare Tunnel: cần gỡ **riêng CNAME của `2k1.me`** trước khi gắn Worker custom domain. Giữ nguyên MX/TXT và các subdomain. Deploy sẽ tạo DNS và HTTPS cho custom domain.

Để deploy tự động qua Cloudflare Workers Builds: kết nối repo `npv2k1/farm`, chọn branch `main`, build command `npm run build`, deploy command `npx wrangler deploy` và root directory `/`. Việc cấp quyền GitHub cho Cloudflare thực hiện trong dashboard Cloudflare.

Không lưu API token trong repository. Nếu chạy CI, dùng secret `CLOUDFLARE_API_TOKEN` và `CLOUDFLARE_ACCOUNT_ID`.

## Công nghệ

React 19, TypeScript, Vite 8, Lucide và Cloudflare Workers Static Assets. Không cần backend hay cơ sở dữ liệu.
