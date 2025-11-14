# Local Setup Guide - Sign Language Recognition

This guide will help you run the Sign Language Recognition app **completely locally** without Firebase Storage.

## Quick Start

### 1. Install Dependencies (if not already done)
```bash
npm install
```

### 2. Start the Development Server
```bash
npm start
```

The app will open at `http://localhost:3000`

## How It Works

- **Model Loading**: Instead of fetching from Firebase Storage, the model is now loaded from `/sign_language_recognizer_25-04-2023.task` which is served from your local `public` folder.

## Project Structure

```
public/
  └── sign_language_recognizer_25-04-2023.task  ← Your model file
src/
  ├── components/
  │   └── Detect/
  │       └── Detect.jsx                         ← Main detection component
  ├── firebase.js                                ← Firebase config (only for auth)
  └── ...
.env.local                                       ← Environment variables
```

## Troubleshooting

### Model Not Loading
- Check browser console for errors
- Verify the model file exists at `public/sign_language_recognizer_25-04-2023.task`
- Ensure the path in `.env.local` matches the filename

### CORS Errors
- This shouldn't happen with local files, but if you see CORS errors, make sure you're accessing the app through `http://localhost:3000` and not `file://`

### Authentication Issues
- If you don't want to use Firebase auth, you can modify the code to bypass it
- Or set up a minimal Firebase project (free tier) just for authentication

## Next Steps

1. **Start the app**: `npm start`
2. **Click "Start"** in the Detect section
3. **Allow camera access** when prompted
4. **Start signing!** The model will recognize your signs in real-time

## Notes

- The model runs entirely in your browser using MediaPipe
- No data is sent to any server (except Firebase if you use authentication)
- Camera access stays local to your machine
- The model file is ~9MB and loads once when you first visit the Detect page

Enjoy your locally-running sign language recognition system! 🤟
