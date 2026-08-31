# My AI Companion V3 — Gemini Free Tier

This version keeps the mobile-first My AI Companion UI and switches the secure backend from OpenAI to the Google Gemini Developer API.

## Why Gemini
Google currently offers a free tier for selected Gemini API models with free input/output tokens and Google AI Studio access. Free-tier limits apply and can change. See the official pricing page: https://ai.google.dev/gemini-api/docs/pricing

## Netlify setup

1. Keep the complete project structure. Do not upload `index.html` alone.
2. In Netlify, open **Project configuration → Environment variables**.
3. Add this exact **Key**:

   `GEMINI_API_KEY`

4. In the **Production** value field, paste the Gemini API key exactly as Google generated it.
5. Mark it as a secret and make sure the **Functions** scope is enabled.
6. Save the variable.
7. Trigger a fresh deployment: **Deploys → Trigger deploy → Deploy project without cache**.
8. Test:

   `https://YOUR-SITE.netlify.app/.netlify/functions/diagnose`

Expected result:

`{"ok":true,"status":200,"message":"Gemini backend is working."}`

## Create the Gemini key
Use Google AI Studio's API key page. Create a Gemini API key and keep it server-side in Netlify. Never put the key in `app.js` or send it to the browser.

## Remove the old OpenAI variable
After Gemini is confirmed working, you can delete the old `OPENAI_API_KEY` from Netlify. It is no longer used by V3.

## Features
- Mobile-first chat
- Text questions
- Browser voice input
- Spoken AI replies using browser text-to-speech
- English practice mode with focused grammar corrections
- Camera/live photo and gallery upload
- AI appearance/style feedback
- Outfit and hairstyle entry points
- Secure server-side Gemini API key

## Important free-tier note
The Gemini API free tier has model-specific rate limits. If a limit is reached, wait for the limit window to reset rather than adding billing. The app surfaces the actual Gemini error so it can be diagnosed without exposing the key.
