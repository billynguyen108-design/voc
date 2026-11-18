# IELTS Visual Vocabulary Trainer — Google image API integration

This package contains the 1,000-word GitHub Pages app plus a Cloudflare Worker proxy for Google's Programmable Search JSON API (image search). **The image feature will not work until you configure and deploy the backend.** There is no secret API key in this ZIP.

## Step 1: Google configuration

1. Confirm that Google's Programmable Search JSON API is available to your Google Cloud account and review current pricing/quotas/terms (availability may change).
2. Create/configure a Programmable Search Engine with image search and web-wide search as appropriate. Obtain its **Search engine ID (cx)**.
3. Enable the relevant API in Google Cloud and obtain a Google API key; restrict its API scope. Never publish the key in GitHub.

## Step 2: Cloudflare Worker

1. Create a Cloudflare account and install Wrangler or use the Cloudflare Worker dashboard to create a Worker from `worker/worker.js`.
2. Set secrets `GOOGLE_API_KEY` and `GOOGLE_CX` in Worker settings (or `wrangler secret put GOOGLE_API_KEY` and `wrangler secret put GOOGLE_CX`).
3. Set `ALLOWED_ORIGIN` to your GitHub Pages origin (e.g. `https://yourname.github.io`) in `worker/wrangler.toml` or dashboard environment variables. If using a custom domain, use that origin instead.
4. Deploy the Worker. Test `https://YOUR-WORKER.workers.dev/images?q=apple%20fruit` and confirm it returns JSON with `items`.

## Step 3: GitHub Pages

1. In `config.js`, set `window.IMAGE_API_ENDPOINT = 'https://YOUR-WORKER.workers.dev/images';`.
2. Upload all **root** app files to your GitHub Pages repository (do not upload the `worker` folder to GitHub Pages unless you want to keep the source there).
3. Commit and refresh the app; if an old offline version persists, close/reopen the installed PWA or clear its site data.

## Behavior and caveats

- Word cards request the backend when opened, display a Google-returned image, and link to the originating website. If unavailable, the card falls back to an emoji and provides a Google Images search link.
- Google Search results are not guaranteed to be pedagogically accurate, available to hotlink, or licensed for reuse. Review rights and consider a curated image library for production.
- The Worker caches successful query results at the edge for 1 hour to reduce API calls. **A public Worker endpoint can still be abused and incur charges.** For production, add Cloudflare rate limiting, bot protection, usage caps, and Google Cloud quota/budget alerts. CORS is not an authentication mechanism.
- Existing vocabulary, quizzes, reading exercises, and progress remain. Speaking scores still measure recognized-text similarity, not phoneme-level pronunciation accuracy.

## Cập nhật Reading: không chấm khi học viên lấy hơi
- Nhấn **Bắt đầu đọc** để mở micro.
- Tạm dừng giữa các câu không tự chấm. Trình duyệt có thể tự ngắt nhận dạng khi im lặng; ứng dụng cố gắng mở lại phiên nhận dạng và ghép các phần đã nghe.
- Nhấn **Hoàn tất & chấm điểm** sau khi đọc xong để nhận điểm.
- Nhấn **Hủy lượt đọc** để bỏ kết quả.
- Giới hạn: Safari/iOS có thể tự ngắt hoặc từ chối tự khởi động lại nhận dạng; cần quyền micro và kết nối mạng. Chấm điểm vẫn là độ khớp văn bản, không phải đánh giá phát âm theo âm vị.
