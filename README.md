# LiveKit + Groq Voice AI Assistant

**A complete starter template for building end-to-end voice AI assistants powered by Groq's lightning-fast inference and LiveKit's real-time infrastructure**

This template provides everything you need to get started building voice AI applications, including a modern Next.js user interface and a Python AI agent backend. Experience natural voice conversations with sub-second response times using Groq's optimized models and LiveKit's battle-tested real-time media platform.

## Live Demo

**Run this template locally** - Follow the setup instructions below to get your voice assistant running on your machine in minutes.

## Overview

This application demonstrates how to build a production-ready voice AI assistant using Groq API for ultra-fast speech processing and LiveKit for real-time audio streaming. Built as a complete, end-to-end template that you can fork, customize, and deploy.

### How LiveKit Works

LiveKit is a real-time communication infrastructure (think Zoom or Google Meet) that handles the complex networking, audio processing, and media routing between users and AI agents. Here's how the architecture flows:

1. **User speaks** → Audio captured by frontend client
2. **LiveKit routes audio** → Streams to your Python AI agent in real-time  
3. **AI agent processes** → Groq converts speech→text→LLM response→speech
4. **LiveKit streams back** → Audio response delivered to user instantly

This means you need **both components running simultaneously**:
- **AI Agent** (Python backend) - Processes voice using Groq models
- **Frontend Client** (React app) - Handles user interface and audio I/O

### LiveKit Account Setup

You'll need a free LiveKit Cloud account to handle the real-time media infrastructure:
1. Sign up at [LiveKit Cloud](https://cloud.livekit.io)
2. Create a new project
3. Get your API credentials from the project settings

**Key Features:**
- **Sub-second response times** with Groq's optimized inference
- **Real-time voice streaming** via LiveKit's infrastructure  
- **Production-ready** noise cancellation and turn detection
- **Modern React UI** with real-time transcription display
- **Efficient concurrent request handling** powered by Groq

## Architecture

**Tech Stack:**
- **Frontend:** Next.js 14, React, TypeScript, Tailwind CSS
- **Backend:** Python, LiveKit Agents SDK
- **AI Infrastructure:** Groq API (STT, LLM, TTS)
- **Real-time Media:** LiveKit Cloud

**AI Pipeline:**
- **Speech-to-Text:** Groq Whisper Large V3 Turbo
- **Language Model:** Groq Llama 3.1 8B Instant  
- **Text-to-Speech:** Groq PlayAI TTS
- **Voice Activity Detection:** Silero VAD
- **Turn Detection:** Multilingual model

## Quick Start

### Prerequisites

- Python 3.9 or later
- Node.js 18+ and npm
- Groq API key ([Get your free API key here](https://console.groq.com/keys))
- LiveKit Cloud account ([Sign up for free](https://cloud.livekit.io))

### Setup

#### 1. Clone the repository
```bash
gh repo clone janzheng/groq-livekit-template
cd groq-livekit
```

#### 2. Install LiveKit CLI (Optional but Recommended)

The LiveKit CLI provides convenient utilities for testing and managing your setup, including helping you get your project credentials:

**Install the CLI:**
```bash
# macOS
brew update && brew install livekit-cli

# Linux/Windows - see https://github.com/livekit/livekit-cli for other installation methods
```

**Authenticate with LiveKit Cloud:**
```bash
lk cloud auth
```

This allows you to use CLI commands without manually providing credentials each time, and gives you access to additional testing and debugging tools.

#### 3. Set up Python Environment (AI Agent)

**Install Python venv** (if not already installed):
```bash
# On macOS/Linux
python3 -m pip install --user virtualenv

# On Windows
py -m pip install --user virtualenv
```

**Create and activate virtual environment:**
```bash
# Create virtual environment
python3 -m venv livekit-env

# Activate it
# On macOS/Linux:
source livekit-env/bin/activate
# On Windows:
livekit-env\Scripts\activate
```

**Install Python dependencies:**
```bash
pip install \
  "livekit-agents[groq,silero,turn-detector]~=1.0" \
  "livekit-plugins-noise-cancellation~=0.2" \
  "python-dotenv"
```

**Download model files:**
To use the turn-detector, silero, or noise-cancellation plugins, you first need to download the model files:

```bash
python agent.py download-files
```

**Test your agent (optional):**
Start your agent in console mode to run inside your terminal:

```bash
python agent.py console
```

Your agent speaks to you in the terminal, and you can speak to it as well. This is a great way to test that everything is working before setting up the frontend.

#### 4. Set up Frontend Client

**In a new terminal tab, navigate to frontend:**
```bash
cd voice-assistant-frontend
```

**Install Node.js dependencies:**
```bash
npm install
```

#### 5. Environment Variables

**Create `.env` in the root directory (for the AI agent):**
```bash
# LiveKit credentials (get from LiveKit Cloud dashboard)
LIVEKIT_URL=wss://your-project.livekit.cloud
LIVEKIT_API_KEY=your-api-key
LIVEKIT_API_SECRET=your-api-secret

# Groq API key (get from Groq Console)
GROQ_API_KEY=your-groq-api-key
```

**Create `.env.local` in the `voice-assistant-frontend/` directory:**
```bash
# Same LiveKit URL as above
LIVEKIT_URL=wss://your-project.livekit.cloud
```

#### 6. Run the Application

**Terminal 1 - Start the AI Agent:**
```bash
# Make sure you're in the root directory and venv is activated
python agent.py dev
```

**Terminal 2 - Start the Frontend:**
```bash
# In the voice-assistant-frontend directory
cd voice-assistant-frontend
npm run dev
```

**Open your browser to `http://localhost:3000`** and start talking to your AI assistant!

### Testing Your Agent

You can also test the agent directly in your terminal without the frontend:

```bash
# Console mode - talk to agent in terminal
python agent.py console
```

## Customization

This template is designed to be a foundation for you to build upon. Key areas for customization:

- **Model Selection:** Update Groq model configuration in `agent.py`
- **Agent Personality:** Modify the system instructions in the `Assistant` class
- **UI/Styling:** Customize themes and components in `voice-assistant-frontend/components/`
- **Voice Settings:** Change TTS voice and speech parameters in the agent configuration

## Troubleshooting

**Common Issues:**

1. **"Connection failed"** - Check your LiveKit credentials and URL
2. **"Agent not responding"** - Ensure the Python agent is running in dev mode
3. **"No audio"** - Check browser microphone permissions
4. **Import errors** - Make sure virtual environment is activated and dependencies installed

## Next Steps

### For Developers
- **Explore the Voice AI Guide:** [LiveKit Voice AI Quickstart](https://docs.livekit.io/agents/start/voice-ai/)
- **Frontend Reference:** Based on [LiveKit Voice Assistant Frontend](https://github.com/livekit-examples/voice-assistant-frontend)
- **Create your free GroqCloud account:** Access official API docs, the playground for experimentation, and more resources via [Groq Console](https://console.groq.com)
- **Build and customize:** Fork this repo and start customizing to build out your own application
- **Get support:** Connect with other developers building on Groq, chat with our team, and submit feature requests on our [Groq Developer Forum](https://community.groq.com)

### For Founders and Business Leaders
- **See enterprise capabilities:** This template showcases production-ready AI that can handle realtime business workloads
- **Discuss Your needs:** [Contact our team](https://groq.com/enterprise-access/) to explore how Groq can accelerate your AI initiatives

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Credits

Created with ❤️ using [LiveKit](https://livekit.io) and [Groq](https://groq.com).

Frontend based on the [LiveKit Voice Assistant Frontend](https://github.com/livekit-examples/voice-assistant-frontend) example.
