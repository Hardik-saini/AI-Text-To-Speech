# AI Text-to-Speech Platform

A text-to-speech web app that lets you generate realistic AI voice audio from text, with support for creating custom cloned voices.

## What it does

- Sign up / login with Clerk
- Type any text and convert it to speech
- Record or upload your own voice and use it to generate speech in that voice
- Keep track of your generated audio histroy
- Audio files are stored on Cloudinary

## Tech used

- Next.js + TypeScript for the frontend and backend (API routes, tRPC)
- Clerk for authentication
- PostgreSQL + Prisma for database
- Chatterbox TTS model, deployed on Modal (serverless GPU) for the actual voice generation
- Cloudinary for storing the audio files
- Sentry for error tracking

## Running it locally

1. Clone the repo and install dependancies:
npm install

2. Set up a .env.local file with your own keys for Clerk, database (Postgres), Cloudinary and the Chatterbox API.

3. The TTS model needs to be deployed seperately on Modal:
pip install modal
python3 -m modal setup
modal deploy chatterbox_tts.py

This gives you a url and you'll need to set up a few secrets in Modal for Hugging Face, the API key and Cloudinary.

4. Run the database migration:
npx prisma migrate dev

5. Start the app:
npm run dev

then just open localhost:3000

## Env variables needed

- Clerk keys (publishable + secret)
- Database URL
- Chatterbox API URL + key
- Cloudinary cloud name, API key, API secret

## Notes

This was a fun project to build to learn how to wire up an AI model with a normal web app - auth, database, storage and a GPU hosted model all talking to each other. took a bit of time to get the Modal deployment working properly but it was worth it.
