# Build Your Own Un-Crashable Local AI Chatbot in Google Colab

A minimal, bulletproof, single-file Python implementation of an interactive local AI chatbot interface hosted on Google Colab. This project leverages the open-source **Qwen2.5-1.5B-Instruct** model and **Gradio** to provide a completely free, self-contained chat interface running entirely on local GPU resources—bypassing API keys, third-party token rates, and common runtime memory crashes.

---

## Why This Project?

Most introductory guides for running large language models (LLMs) inside notebooks rely on hosted API endpoints or fragile structural parsers that break whenever Gradio updates its conversation history formats. 

This repository provides a robust architectural alternative by:
1. **Bypassing Gradio History Serialization:** Tracks conversation history using a native Python state manager to prevent parsing errors across package updates.
2. **Implementing Aggressive Memory Management:** Auto-trims long-context tokens to structurally insulate the environment against `CUDA Out of Memory` (OOM) crashes on standard free-tier T4 GPUs.
3. **Streaming Token Generation:** Uses asynchronous threading and string iterators to stream responses dynamically in real time.

For an exhaustive, line-by-line engineering breakdown of how this code operates under the hood, read the full technical companion write-up:
👉 **[Read the Full Technical Blog Post Here](https://evapatel123.hashnode.dev/stop-crashing-your-colab-the-easiest-one-file-python-chatbot-that-actually-works)**

---

## Features

- **Single-File Implementation:** The entire architecture fits within a single Python script or notebook cell.
- **100% Free & Open-Source:** Runs locally using Hugging Face transformers on free hardware tiers.
- **Robust State Retention:** Maintains sliding-window session history safely.
- **Live Link Generation:** Generates a shareable public proxy link (`.gradio.live`) to interact with your model globally.

---

## Quick Start

### 1. Hardware Prerequisites
Ensure your Google Colab instance is configured to use a GPU accelerator:
- Navigate to **Runtime** > **Change runtime type**
- Select **T4 GPU** (or any higher available hardware accelerator)

### 2. Dependency Installation
Run the following package layout block to prepare the environment:
```bash
!pip install gradio transformers accelerate
```
