<h1 align="center">Arsenal Browser</h1>

<p align="center">
  <strong>AI-Powered Developer Browser with Multi-Provider Support</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Electron-30.0.9-47848F?logo=electron" alt="Electron" />
  <img src="https://img.shields.io/badge/Platform-macOS%20|%20Windows%20|%20Linux-lightgrey" alt="Platform" />
  <img src="https://img.shields.io/badge/License-MIT-green" alt="License" />
</p>

---

## 🚀 Overview

Arsenal is a modern, AI-integrated browser built with Electron, designed for developers who want AI assistance while browsing. It features a sleek dark UI, multi-tab browsing, and a powerful AI sidebar that supports multiple providers including **Google Gemini**, **OpenAI GPT-4o**, and **DeepSeek**.

---

## ✨ Features

### 🌐 **Modern Tab-Based Browsing**
- Multi-tab interface with smooth tab management
- Back, forward, refresh navigation controls
- URL bar with smart search (auto-detects URLs vs search queries)
- Quick-access links to popular sites (Google, GitHub, YouTube, Stack Overflow)

### 🤖 **AI Assistant Sidebar**
- **Multi-Provider Support**: Switch between OpenAI, Google Gemini, and DeepSeek
- **Custom Model Selection**: Specify exact model versions (e.g., `gemini-2.5-flash`, `gpt-4o-mini`)
- **Multimodal Support**: Send images to AI for analysis (Gemini & GPT-4o vision)
- **IDE-Style Code Blocks**: Syntax highlighting with [highlight.js](https://highlightjs.org/) (Atom One Dark theme)
- **Copy Code Button**: One-click code copying from AI responses
- **Clipboard Integration**: Auto-detects copied text from webpages for quick AI queries

### 📎 **Smart Clipboard & Media**
- **Paste Images**: Paste screenshots directly from clipboard (`Cmd/Ctrl+V`)
- **File Attachments**: Click the attachment button to upload images
- **Webpage Copy Detection**: When you copy text on any webpage, a prompt appears to instantly send it to AI

### 🎨 **Dual Theme Modes**
| Mode | Description |
|------|-------------|
| 🛡️ **Green Mode** | Safe browsing with emerald accent colors |
| 🩸 **Blood Mode** | Privacy-focused mode with red theme and proxy simulation UI |

### ⌨️ **Keyboard Shortcuts**
| Shortcut | Action |
|----------|--------|
| `Cmd/Ctrl + D` | Toggle DevTools |
| `Enter` | Send AI message / Navigate to URL |
| `Shift + Enter` | New line in AI chat |

---

## 🔐 Security Architecture

### **API Key Storage**

| Aspect | Implementation |
|--------|----------------|
| **Storage Library** | `electron-store` |
| **Encryption** | AES-256 encryption |
| **File Name** | `arsenal-keys.json` |
| **Location (macOS)** | `~/Library/Application Support/arsenal-browser/` |
| **Location (Windows)** | `%APPDATA%/arsenal-browser/` |
| **Location (Linux)** | `~/.config/arsenal-browser/` |

### **Data Stored Locally**
```
keys.openai     → Encrypted OpenAI API key
keys.gemini     → Encrypted Gemini API key  
keys.deepseek   → Encrypted DeepSeek API key
models.openai   → Custom OpenAI model name
models.gemini   → Custom Gemini model name
models.deepseek → Custom DeepSeek model name
```

### **Security Considerations**

⚠️ **Current Implementation**:
- Encryption key is embedded in source code (basic obfuscation)
- API keys are stored locally and never transmitted except to respective AI providers
- No telemetry or analytics

✅ **Best Practices Followed**:
- Context isolation enabled (`contextIsolation: true`)
- Node integration disabled in renderer (`nodeIntegration: false`)
- Preload scripts for secure IPC communication
- Webview sandboxing with controlled permissions

🔒 **Recommended Enhancements** (for production):
- Use Electron's `safeStorage` API for OS-level encryption
- Implement a master password system
- Use OS keychain (macOS Keychain, Windows Credential Manager)

---

## 📦 Installation

### Prerequisites
- Node.js 18+ 
- npm or yarn

### Quick Start

```bash
# Clone the repository
git clone https://github.com/yourusername/arsenal-browser.git
cd arsenal-browser

# Install dependencies
npm install

# Run the browser
npm start
```

---

## 🛠️ Project Structure

```
arsenal-browser/
├── assets/
│   └── Arsenal-logo.png       # App logo
├── src/
│   ├── main.js                # Electron main process
│   ├── preload.js             # Secure IPC bridge
│   └── renderer/
│       ├── index.html         # Main UI
│       ├── style.css          # Styling (1200+ lines)
│       ├── renderer.js        # Frontend logic
│       └── webview-preload.js # Webview clipboard detection
├── package.json
└── README.md
```

---

## 🔧 Configuration

### Adding API Keys

1. Launch Arsenal Browser
2. Click the **☰ Settings** button (top-right)
3. Enter your API keys:
   - **OpenAI**: Get from [platform.openai.com](https://platform.openai.com/api-keys)
   - **Gemini**: Get from [aistudio.google.com](https://aistudio.google.com/app/apikey)
   - **DeepSeek**: Get from [platform.deepseek.com](https://platform.deepseek.com/)
4. Optionally specify custom model names
5. Click **Save Keys & Models**

### Custom Models

| Provider | Default Model | Example Alternatives |
|----------|--------------|---------------------|
| OpenAI | `gpt-4o-mini` | `gpt-4o`, `gpt-4-turbo` |
| Gemini | `gemini-1.5-flash` | `gemini-2.5-flash`, `gemini-1.5-pro` |
| DeepSeek | `deepseek-chat` | `deepseek-coder` |

---

## 🎯 Tech Stack

| Component | Technology |
|-----------|------------|
| Framework | Electron 30 |
| AI SDK | `@google/generative-ai` |
| Storage | `electron-store` (encrypted) |
| Syntax Highlighting | highlight.js |
| Styling | Pure CSS with CSS Variables |
| Fonts | Space Grotesk, Orbitron |

---

## 🚧 Roadmap

- [ ] Chrome password import (CSV)
- [ ] Bookmark sync
- [ ] Extension support
- [ ] Built-in ad blocker
- [ ] History search
- [ ] Download manager
- [ ] Picture-in-Picture mode

---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

##  Acknowledgments

- [Electron](https://www.electronjs.org/) - Framework
- [Google Generative AI](https://ai.google.dev/) - Gemini SDK
- [highlight.js](https://highlightjs.org/) - Syntax highlighting
- [electron-store](https://github.com/sindresorhus/electron-store) - Secure storage

---

<p align="center">
  Built with ❤️ by the Arsenal Team
</p>
