# SACHIN AI FLOW — Wan 2.2 update

This update keeps the existing website design and replaces Gemini Omni video generation with Wan 2.2 through fal.ai.

## Features
- Text-to-video: Wan 2.2 5B
- Image-to-video: Wan 2.2 5B
- Hindi male/female voice preview using voices installed on the user's browser/device
- Existing Gemini photo-editing endpoint remains optional
- Existing PWA/mobile interface retained

## Free usage warning
Wan is an open model, but hosted GPU inference is not automatically free. fal.ai currently lists about US$0.15 per generated video for its Wan 2.2 5B text-to-video and image-to-video endpoints. Prices and credits can change. Do not assume unlimited free generation.

## Deploy to your existing Render service
1. Replace the existing repository files with the contents of this ZIP (keep the `public/` folder).
2. Commit and push to the same GitHub `main` branch. Render auto-deploy should start.
3. In Render → `sachin-ai-flow` → Environment, add `FAL_KEY` with your fal.ai API key.
4. Keep `FAL_KEY` private. Never put it in GitHub, `public/app.js`, or chat.
5. `GEMINI_API_KEY` is optional and is only used for AI photo editing. Video generation no longer calls Gemini Omni.
6. Wait for deployment, then open the Render URL and test Text to Video / Image to Video.

## API
- `GET /api/status`
- `GET /api/health`
- `POST /api/video` multipart fields: `prompt`, optional `image`, `ratio`
- `POST /api/image-edit` multipart fields: `image`, optional `prompt`

## Voice limitations
Hindi voice preview uses Android/browser Speech Synthesis. Male/female options select an installed Hindi voice where one is available. Device voice availability varies. This is a preview only; it does not create a downloadable audio track or merge speech into the MP4.

## Edit mode limitation
The existing Edit photo tool still uses Gemini Image. This update does not provide video-to-video editing; that requires a separate model endpoint.
