# IELTS Visual Vocabulary Trainer — Google Images edition

Upload all files in this folder to the root of your GitHub Pages repository. The vocabulary, quiz, speaking practice and progress screens remain.

## Google Images integration
The vocabulary screen now offers **Xem ảnh Google**, which opens a Google Images search for the current word and topic. Wikimedia Commons is fully removed.

**Important limitation:** Google Images search results cannot legally/reliably be scraped and hotlinked directly from a static GitHub Pages app. Without a backend, the app displays its local illustrative emoji and a link to the live Google Images results. This is intentional, not an image-loading bug.

To display Google-sourced images automatically inside the app, create a backend proxy using Google's supported Programmable Search JSON API (image search), with your API key and search engine configuration stored **server-side**. Configure `GOOGLE_IMAGE_PROXY` near the top of `app.js` with an HTTPS endpoint that accepts `?q=...` and responds with `{ "items": [{ "imageUrl": "https://...", "sourceUrl": "https://...", "title": "..." }] }`. Your backend must allow CORS for your GitHub Pages origin and should enforce rate limits and safe-search. Review Google's current API availability, quotas, and terms. Source sites own the image rights.

Do not commit API keys to GitHub.

Speech scores remain text-transcription similarity, not clinical/phoneme-level pronunciation accuracy.
