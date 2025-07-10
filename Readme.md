# CallMind — AI Voice Help Desk Assistant

**CallMind** is a real-time AI voice assistant built as a **demo project** for a client exploring AI-powered customer support and CRM solutions. It allows users to call a phone number and have a natural voice conversation with an intelligent assistant powered by OpenAI's GPT-4o Realtime API.

The assistant can listen, understand context, respond intelligently, and even handle user interruptions — all via a live phone call using Twilio Voice and Media Streams.

---

## 🎯 Project Objective

- Build an AI-powered help desk that responds to callers using real-time speech-to-text and text-to-speech.
- Simulate multi-turn, natural customer conversations over the phone.
- Demonstrate voice automation and AI assistance without human agents.

---

## 🧠 Tech Stack

- **Node.js + Fastify** — Server-side framework
- **Twilio Programmable Voice + Media Streams** — Telephony and real-time audio stream
- **OpenAI GPT-4o Realtime API** — Speech recognition, NLU, and voice responses
- **WebSockets** — Bi-directional audio streaming with low latency

---

## 📞 What You’ll Need

- A **Twilio account** — [Sign up here](https://www.twilio.com/try-twilio)
- A **Twilio phone number** with Voice capability — [Buy one here](https://help.twilio.com/articles/223135247)
- An **OpenAI API Key** — [Get access here](https://platform.openai.com/)
- [ngrok](https://ngrok.com/) or [cloudflared](https://developers.cloudflare.com/cloudflare-one/) for tunneling (if running locally)

---

## ⚙️ Setup Instructions

### 1. Install Packages

```bash
git clone https://github.com/suchael/call_mind_ai_help_desk
cd call_mind_ai_help_desk
npm install

### Update the .env file

Create a `/env` file, or copy the `.env.example` file to `.env`:

```
cp .env.example .env
```

In the .env file, update the `OPENAI_API_KEY` to your OpenAI API key from the **Prerequisites**.

## Run the app
Once ngrok is running, dependencies are installed, Twilio is configured properly, and the `.env` is set up, run the dev server with the following command:
```
node index.js
```
## Test the app
With the development server running, call the phone number you purchased in the **Prerequisites**. After the introduction, you should be able to talk to the AI Assistant. Have fun!

## Special features

### Interrupt handling/AI preemption
When the user speaks and OpenAI sends `input_audio_buffer.speech_started`, the code will clear the Twilio Media Streams buffer and send OpenAI `conversation.item.truncate`.