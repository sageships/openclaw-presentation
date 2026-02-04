---
marp: true
theme: default
paginate: true
backgroundColor: #1a1a2e
color: #eee
style: |
  section {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  }
  h1, h2 {
    color: #00d4ff;
  }
  code {
    background: #16213e;
    padding: 2px 8px;
    border-radius: 4px;
  }
  a {
    color: #00d4ff;
  }
  blockquote {
    border-left: 4px solid #00d4ff;
    padding-left: 20px;
    font-style: italic;
    color: #aaa;
  }
---

# 🦞 OpenClaw

### Your AI That Actually Lives on Your Computer

**Not a chatbot. A capable assistant with real access.**

---

# What is OpenClaw?

OpenClaw is an AI assistant that:

- 🖥️ **Runs locally** on your Mac/PC
- 📁 **Reads & writes files** in your projects
- 💻 **Executes terminal commands** 
- 🌐 **Browses the web** for you
- 📱 **Connects to Telegram/WhatsApp** so you can chat from anywhere

> Think of it as Claude, but with hands.

---

# Why is this different?

| Regular AI Chatbot | OpenClaw |
|-------------------|----------|
| Lives in a browser tab | Lives on your machine |
| Can only talk | Can read, write, execute |
| Forgets everything | Has persistent memory |
| You copy-paste code | It writes directly to files |
| Can't see your project | Understands your full codebase |

---

# 🚀 Setup Guide

### What you need:
- macOS or Linux machine
- Node.js v20+ installed
- An Anthropic API key (or Claude Max subscription)

---

# Step 1: Install OpenClaw

Open your terminal and run:

```bash
npm install -g openclaw
```

That's it. One command.

---

# Step 2: Run the Setup Wizard

```bash
openclaw onboard
```

This will:
1. Ask for your Anthropic API key
2. Set up a workspace folder
3. Create the background gateway service
4. Open the web UI

---

# Step 3: Connect Telegram (Optional)

```bash
openclaw configure --section telegram
```

1. Create a bot via @BotFather on Telegram
2. Paste the bot token when asked
3. Add your Telegram user ID (for security)

Now you can chat with your AI from your phone! 📱

---

# Step 4: Start Using It

**Web UI:**
```bash
openclaw ui
```

**Or just message your Telegram bot!**

The AI is always running in the background, ready to help.

---

# 🎯 Main Use Cases

---

# Use Case 1: Code Assistant

> "Create a React component that shows a loading spinner"

OpenClaw will:
- Create the file in the right location
- Write working code
- Even run it to test if you want

No copy-pasting. It writes directly to your project.

---

# Use Case 2: Project Automation

> "Set up a new Next.js project with TypeScript and Tailwind"

OpenClaw will:
- Run `npx create-next-app`
- Install dependencies
- Configure Tailwind
- Create initial folder structure

You watch. It builds.

---

# Use Case 3: Research & Learning

> "Explain how React Server Components work and show me an example"

OpenClaw will:
- Search the web (if Brave API configured)
- Read documentation
- Write example code you can actually run
- Explain in plain language

---

# Use Case 4: DevOps & Scripting

> "Check what's running on port 3000 and kill it"

```bash
# OpenClaw runs:
lsof -i :3000
kill -9 <pid>
```

System administration through natural language.

---

# Use Case 5: Memory & Context

> "What did we work on yesterday?"

OpenClaw maintains memory files:
- `MEMORY.md` — long-term knowledge
- `memory/YYYY-MM-DD.md` — daily logs

It remembers your projects, preferences, and decisions.

---

# 🔥 Real Examples

### How I've been using OpenClaw for the past week

---

# Example 1: Building a macOS App

**Me:** "Build a menubar app that shows all running dev server ports"

**What OpenClaw did:**
1. Created a Swift/SwiftUI project from scratch
2. Wrote code to detect running processes on common ports
3. Added features: open in browser, kill process, rename
4. Built the `.app` file
5. Created GitHub repo and pushed it

**Result:** [DevPorts](https://github.com/sageships/DevPorts) — a working macOS app in ~2 hours

---

# Example 2: Course Content

**Me:** "Add detailed explanations to Module 3 about how context selection actually works mechanically"

**What OpenClaw did:**
1. Read my existing course files
2. Researched how tools like tree-sitter work
3. Wrote technical explanations with code examples
4. Updated README with proper structure

**Result:** Professional course content I'd have spent a day writing

---

# Example 3: Fixing Crashes

**Me:** "Why was the gateway down for 7 hours?"

**What OpenClaw did:**
1. Analyzed log files automatically
2. Found network errors and crash patterns
3. Updated the launchd config for auto-recovery
4. Explained what happened and why

**Result:** Problem diagnosed and fixed in minutes

---

# Example 4: Workspace Automation

**Me:** "I need one click to open all my work repos in Cursor with terminals running"

**What OpenClaw did:**
1. Built a macOS app (SetWorkspace)
2. Reads config from `~/.setworkspace/config.json`
3. Opens multiple repos in Cursor
4. Runs terminal commands automatically

**Result:** My 5-minute morning routine → 1 click

---

# 💬 How the Workflow Feels

```
Morning routine:

1. Wake up
2. Send Telegram message: "What's on my calendar today?"
3. Get response while still in bed
4. "Start my dev environment"
5. Everything opens automatically
6. Start coding
```

The AI is always there. On my Mac. On my phone. Remembers everything.

---

# My Typical Commands

```
"Create a new component for X"
"What port is the backend running on?"
"Commit and push my changes"
"Search for how to do Y in React"
"Set a reminder in 2 hours to check Z"
"What did we decide about the database schema?"
```

Natural language → Real actions

---

# 🛠️ Power User Tips

---

# Tip 1: Memory Files

Create these in your workspace:

- `MEMORY.md` — What AI should always know
- `USER.md` — About you (timezone, preferences)
- `TOOLS.md` — Your specific setup (hosts, cameras, etc.)

The AI reads these every session.

---

# Tip 2: Skills

Skills are templates for complex tasks.

```bash
ls ~/.nvm/versions/node/*/lib/node_modules/openclaw/skills/
```

Weather, GitHub, Whisper transcription, and more.

You can also create custom skills!

---

# Tip 3: Heartbeats

OpenClaw can check in periodically:

```markdown
# HEARTBEAT.md

- Check my email for urgent messages
- Remind me of upcoming calendar events
```

It runs these checks automatically throughout the day.

---

# Tip 4: Sub-Agents

For complex tasks, OpenClaw can spawn background workers:

> "Research the best React state management libraries and write a comparison. Take your time."

A sub-agent runs in the background and pings you when done.

---

# 🔑 Key Configuration

```bash
# Where everything lives
~/.openclaw/
├── openclaw.json      # Main config
├── workspace/         # Your working directory
│   ├── MEMORY.md
│   ├── USER.md
│   └── memory/
└── logs/              # Debug logs
```

---

# Common Commands

```bash
openclaw ui           # Open web interface
openclaw status       # Check if running
openclaw logs         # View recent logs
openclaw configure    # Change settings
openclaw gateway restart  # Restart the service
```

---

# ⚠️ Things to Know

1. **It has real access** — Be thoughtful about what you ask
2. **Memory persists** — Delete sensitive info from memory files
3. **Costs money** — Uses Anthropic API (or Claude Max sub)
4. **Needs network** — Won't work offline

---

# 🎁 What You Get

✅ An AI that actually does things, not just talks
✅ Persistent memory across sessions
✅ Mobile access via Telegram
✅ Direct integration with your development environment
✅ Background workers for long tasks
✅ Customizable with skills and memory

---

# Getting Started Checklist

- [ ] Install: `npm install -g openclaw`
- [ ] Setup: `openclaw onboard`
- [ ] Connect Telegram (optional)
- [ ] Create USER.md with your info
- [ ] Start chatting!

---

# Resources

- **Docs:** https://docs.openclaw.ai
- **GitHub:** https://github.com/openclaw/openclaw
- **Discord:** https://discord.com/invite/clawd
- **Skills:** https://clawhub.com

---

# 🦞

## Start building with your AI

```bash
npm install -g openclaw && openclaw onboard
```

**Questions?**

---

