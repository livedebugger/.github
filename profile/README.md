# Meowlyzer – VS Code AI Debug Assistant

a VS Code extension that helps developers debug faster by using Groq AI. 

It captures **code context**, **terminal logs**, learns about the **Project Structure** (goes through Config files to learn about the **Dependencies**), and sends them to **Groq’s LLM** which looks up the latest concerned tech stack docs, **builds context**, evaluates to provide real-time suggestions.

## Features

- AI-Powered Debugging: Get contextual suggestions using Groq AI.
- Smart Capture: Automatically captures:
  - Code around the active cursor
  - Recent terminal logs
  - Optional: screenshot OCR from a screen region (Wayland) for neovim or other text editors
- Live Suggestions Panel: See issues, suggestions, and fixes in a sidebar.
- To Implement: Peer Debugging Mode: Stream debugging session data to teammates.

## Architecture

1. VS Code Extension (Frontend)
   - Captures Editor + Terminal Context + Project Directory Context
   - Sends data to backend via WebSocket
   - Displays live suggestions

2. Backend (FastAPI)
   - Receives data from extension
   - Sends context to Groq LLM
   - Streams AI responses back

3. Optional: OCR Module (Rust CLI)
   - Triggered via keybinding
   - Captures screen region
   - Uses Tesseract for OCR
   - Sends result to backend

## Tech Stack

- VS Code API (TypeScript)
- FastAPI (Python)
- Optional: Tesseract + wl-clipboard (Rust CLI)
- Groq LLM (API)
