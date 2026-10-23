# SeeYourself

Put yourself in a short reel. The user uploads one selfie, picks a clip, and gets back a video with their own face, clearly labelled as AI-generated.

**Status:** early prototype by a solo founder. The face-swap runs through a GPU API; this repo contains the web app and a small serverless backend.

## How it works
1. `app.html` collects a selfie (resized in the browser), a consent tick, and a clip choice.
2. `api/swap.js` starts a face-swap job on Replicate using the selfie and the chosen clip.
3. `api/status.js` is polled every few seconds until the video is ready.
4. The result is shown with an AI-generated label, plus Download and Share.

## Why the video clips are not in this repository
- **Rights.** The reel clips are licensed or owned media. This code is open source, but the clips are not, so they are not redistributed with it. Use clips you own or have a licence for.
- **Size.** Video files are large binary files. They bloat the repository and make cloning slow, and GitHub limits file sizes.
- **Safety.** Keeping clips out of a public repo means nobody can copy the full library from GitHub.

To run the app, add your own `clip1.mp4`, `clip2.mp4` and `clip3.mp4` to the `clips/` folder (see `clips/README.txt`).

## Safety rules
- Own face only: the user must confirm before every swap.
- Every result is labelled AI-generated.
- Only clips the project owns or has licensed (no downloaded movie or social clips).
- An access code protects the API so strangers can't spend credits.

## Run it yourself
1. Put three MP4 clips in `clips/` named `clip1.mp4`, `clip2.mp4`, `clip3.mp4`.
2. Create a Replicate API token and set a spending limit.
3. Deploy to Vercel and add the environment variables in `.env.example`.

Never commit real keys. Secrets live only in the Vercel settings.

## Roadmap
- Voice in the user's own voice (voice-conversion API)
- A library of licensed clips and creator revenue share
- Personalised video for brands

## License
MIT
