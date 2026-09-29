# tg-bot-speech-to-text - quick start

Follow these steps to get the bot running even if you have never built a Telegram bot before.

## 1. Gather the required tokens
- **Create a Telegram bot token**  
  1. Open Telegram and search for `@BotFather`.  
  2. Start a chat and send `/newbot`.  
  3. Pick a name (e.g., `Speech To Text Bot`) and a unique username ending in `bot`.  
  4. BotFather will reply with an HTTP API token - copy it and keep it safe.
- **Create a Gemini API key**  
  1. Sign in at [https://aistudio.google.com/app/apikey](https://aistudio.google.com/app/apikey).  
  2. Click "Create API key" and follow the prompts.  
  3. Copy the generated key; you will need it shortly.

## 2. Configure your environment
- Duplicate the sample file: `cp .env.example .env`.
- Open `.env` in a text editor and fill in:
  - `AI_MODEL_API_KEY` - the Gemini key you just created.
  - `AI_MODEL` - production currently uses `gemini-3.5-flash-lite` (verified 2026-09-29).
  - `AI_MODEL_FALLBACK` - production fallback is `gemini-3.1-flash-lite`.
  - `TELEGRAM_BOT_TOKEN` - the token from BotFather.
  - `DEBUG` - set to `true` if you want verbose logging while debugging.

## 3. Install the prerequisites
- Make sure you have Python 3.10+ installed (`python3 --version`).
- Install project dependencies:  
  `pip install -r requirements.txt`
- Install FFmpeg (needed for format fallback):
  - macOS (Homebrew): `brew install ffmpeg`
  - Ubuntu/Debian: `sudo apt-get update && sudo apt-get install ffmpeg`
  - Windows: use the [FFmpeg download page](https://ffmpeg.org/download.html), unzip the release, and add the `bin` folder to your PATH.

## 4. Run the bot
- Start the bot with: `python3 bot.py`
- Leave the terminal window open; the bot stops when you press `Ctrl+C`.

## 5. Test the flow
- Open Telegram and find your bot by the username you created.
- Send any voice note, audio file, or forwarded WhatsApp audio.
- The bot immediately replies with "Processing audio..." and then edits that message with the transcript (and action items if any).
- Add a caption if you want to give extra instructions (e.g., "translate to English").

## 6. Where to check for errors
- All logs print to the same terminal window that runs `python3 bot.py`.
- Set `DEBUG=true` in `.env` to see detailed trace logs (file type/size, Gemini attempts, FFmpeg command, timings).

## 7. Quick fixes
- **"FFmpeg not found"** - install FFmpeg and restart the bot so it picks up the binary.
- **"Gemini rejected audio format"** - Gemini could not read the original file even after conversion; try re-sending as a WAV/MP3 recorded from your device.
- **Timeouts or network errors** - check your internet connection and retry; long audio clips may take longer to upload.
- **Permission denied while writing temp files** - ensure you run the command from a folder where you have write access.
- **Unauthorized/401 errors** - double-check the Gemini API key and confirm it has access to the chosen model.

You are ready to transcribe audios directly in Telegram!

## Repository and deployment

- GitHub: https://github.com/PersimmonChris/tg-bot-speech-to-text
- Main local checkout: `/Users/christian/Developer/tg-bot-speech-to-text`.
- Coolify app: `tg-bot-speech-to-text`, UUID `oduhuejw76pwbypk8y3wp10s`, branch `main`, Nixpacks.
- Edit locally, commit, and push to GitHub. Coolify builds from GitHub when a deployment is triggered; local edits alone do not change production. Auto-deploy is enabled in Coolify, but a successful deployment must still be verified after each push.
- The running container remains independent of the Mac checkout.
- A second, older checkout exists at `/Users/christian/Developer/telegram-bot-speech-to-text-course`; its remote points to the same renamed repository. Use the main checkout above for current work.
