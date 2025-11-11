<div align="center">

# 🌙 Mooncord API Dev Studio

### Professional API Testing & Development Environment

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Node.js](https://img.shields.io/badge/Node.js-18+-green.svg)](https://nodejs.org/)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](#-contributing)

**The ultimate API testing tool with 44 free APIs, 8 beautiful themes, and powerful developer features.**

[Features](#-features) • [Quick Start](#-quick-start) • [Screenshots](#-screenshots) • [Documentation](#-documentation) • [Contributing](#-contributing)

</div>

---

## ✨ Features

### 🚀 Core Functionality

- **🎯 API Request Builder** - Full HTTP method support (GET, POST, PUT, PATCH, DELETE, HEAD, OPTIONS)
- **📊 Response Viewer** - Formatted JSON, headers, cookies, and raw response tabs
- **💡 44 Free API Examples** - Ready-to-use examples across 8 categories
- **📈 Real-time Analytics** - Track requests, success rate, and performance metrics
- **💾 Request Collections** - Save and organize your favorite API requests
- **📜 Request History** - Last 50 requests automatically tracked with performance data

### 🎨 Themes & Customization

- **8 Beautiful Themes** - Dark, Light, Ocean, Sunset, Forest, Cyberpunk, Dracula, Nord
- **Custom Selection Colors** - Each theme has unique text highlight colors
- **Persistent Preferences** - Your theme choice is saved across sessions
- **Smooth Transitions** - Instant theme switching with animations

### 💻 Developer Tools

- **Code Generator** - Export to JavaScript (Fetch/Axios), cURL, Python, PHP
- **Environment Variables** - Manage API keys and configuration
- **Request Tabs** - Organized Params, Headers, Body, Auth sections
- **Smart Defaults** - Intelligent fallbacks for missing elements

### 🔒 Privacy & Security

- **100% Client-Side** - All data stays in your browser
- **No Tracking** - We don't collect any personal data
- **Offline Capable** - Works without internet connection
- **Free & Open Source** - MIT License

## 🚀 Quick Start

### Installation

```bash
# Clone the repository
git clone https://github.com/tubbymctubbzz/mooncord.git
cd mooncord

# Install dependencies
npm install
```

### Running the Server

```bash
# Production mode
npm start

# Development mode (with auto-reload)
npm run dev
```

The server will start on `http://localhost:3000`

### First Steps

1. **Open your browser** to `http://localhost:3000`
2. **Click "Examples"** to browse 44 free API examples
3. **Select an API** to auto-fill the request builder
4. **Click "Send Request"** to test the API
5. **Save your favorites** for quick access later
6. **Try different themes** using the theme button in the spiral menu

## 📸 Screenshots

### API Request Builder
Beautiful, intuitive interface for building and testing API requests with full HTTP method support.

### Theme Selector
Choose from 8 stunning themes - each with custom colors and unique text selection highlights.

### Analytics Dashboard
Track your API testing performance with real-time statistics and success rates.

### Code Generator
Export your requests to 5 different languages with one click.

## 📚 Documentation

### API Request Builder

The request builder supports all HTTP methods and provides organized tabs for:

- **Params** - Query parameters with key-value editor
- **Headers** - Custom headers for authentication and content types
- **Body** - JSON, form data, or raw request bodies
- **Auth** - Bearer tokens, Basic Auth, and API keys

### 44 Free API Examples

Browse and test APIs across 8 categories:

1. **Testing** - JSONPlaceholder for development
2. **Fun** - Random dogs, cats, jokes, and quotes
3. **Utility** - IP info, UUID generation, user agents
4. **Data** - Countries, weather, Pokémon, SpaceX
5. **Cryptocurrency** - Bitcoin prices, exchange rates
6. **Entertainment** - Anime, movies, TV shows, Chuck Norris jokes
7. **Science** - NASA, number facts, universities
8. **Food & Drink** - Cocktails, recipes, coffee

### Themes

| Theme | Description | Primary Color |
|-------|-------------|---------------|
| 🌙 Dark | Classic dark theme | Indigo Blue |
| ☀️ Light | Clean bright theme | Indigo Blue |
| 🌊 Ocean | Deep blue nautical | Cyan |
| 🌅 Sunset | Purple & pink vibes | Pink |
| 🌲 Forest | Nature green theme | Green |
| 🤖 Cyberpunk | Neon futuristic | Magenta |
| 🧛 Dracula | Popular purple | Purple |
| ❄️ Nord | Arctic minimal | Arctic Blue |

### Code Generation

Generate code in 5 languages:
- JavaScript (Fetch API)
- JavaScript (Axios)
- cURL
- Python (Requests)
- PHP (cURL)

### Server API Endpoints

#### Instances

- `GET /api/instances` - List all instances
- `GET /api/instances/:id` - Get specific instance
- `POST /api/instances` - Create new instance
  ```json
  {
    "name": "My Test Instance",
    "config": {
      "port": 8080,
      "debug": true
    }
  }
  ```
- `PUT /api/instances/:id` - Update instance
- `DELETE /api/instances/:id` - Delete instance

#### Instance Control

- `POST /api/instances/:id/start` - Start instance
- `POST /api/instances/:id/stop` - Stop instance
- `POST /api/instances/:id/restart` - Restart instance

#### Logs

- `GET /api/instances/:id/logs?limit=100` - Get instance logs
- `POST /api/instances/:id/logs` - Add log entry
  ```json
  {
    "message": "Custom log message",
    "level": "info"
  }
  ```

#### Testing

- `POST /api/instances/:id/test` - Run test
  ```json
  {
    "testName": "API Connection Test",
    "testCode": "// test code here"
  }
  ```
- `GET /api/instances/:id/tests` - Get test results

#### Files

- `POST /api/instances/:id/files` - Upload file
  ```json
  {
    "filename": "config.json",
    "content": "{\"key\": \"value\"}"
  }
  ```
- `GET /api/instances/:id/files` - List instance files
- `POST /api/instances/:id/watch` - Enable file watching

#### Health

- `GET /api/health` - Server health check

## WebSocket Events

Connect to `ws://localhost:3000` for real-time updates:

### Client → Server

```json
{
  "type": "subscribe"
}
```

```json
{
  "type": "getLogs",
  "instanceId": "instance-uuid"
}
```

### Server → Client

```json
{
  "type": "connected",
  "instances": [...]
}
```

```json
{
  "type": "statusChange",
  "instanceId": "instance-uuid",
  "status": "running"
}
```

```json
{
  "type": "log",
  "instanceId": "instance-uuid",
  "log": {
    "timestamp": "2025-11-11T18:00:00.000Z",
    "level": "info",
    "message": "Log message"
  }
}
```

## Architecture

### Backend (Node.js + Express)

- **Express Server**: RESTful API endpoints
- **WebSocket Server**: Real-time bidirectional communication
- **Instance Manager**: In-memory instance state management
- **File Watcher**: Chokidar-based file monitoring
- **Storage**: File-based instance persistence

### Frontend (Vanilla JavaScript)

- **WebSocket Client**: Real-time updates
- **REST Client**: API communication
- **Responsive UI**: Modern, mobile-friendly interface
- **Modal System**: Clean UX for forms and data display

## Directory Structure

```
dev-server/
├── server.js           # Main server file
├── package.json        # Dependencies
├── README.md          # Documentation
├── public/            # Frontend files
│   └── index.html     # Web interface
├── instances/         # Instance storage (auto-created)
│   └── [uuid]/        # Individual instance directories
└── node_modules/      # Dependencies
```

## Configuration

Environment variables:

- `PORT` - Server port (default: 3000)

## Use Cases

1. **Testing Code Changes**: Create isolated instances to test different code versions
2. **Debugging**: Monitor logs and behavior in real-time
3. **Integration Testing**: Run automated tests against live instances
4. **Development**: Rapid iteration with file watching and hot reload
5. **CI/CD**: Programmatic instance management via API

## API Examples

### Create and Test an Instance

```javascript
// Create instance
const response = await fetch('http://localhost:3000/api/instances', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({
    name: 'Test Instance',
    config: { debug: true }
  })
});
const { instance } = await response.json();

// Start instance
await fetch(`http://localhost:3000/api/instances/${instance.id}/start`, {
  method: 'POST'
});

// Run test
await fetch(`http://localhost:3000/api/instances/${instance.id}/test`, {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({
    testName: 'Connection Test',
    testCode: 'console.log("Testing...")'
  })
});

// Get logs
const logsResponse = await fetch(`http://localhost:3000/api/instances/${instance.id}/logs`);
const { logs } = await logsResponse.json();
```

## Requirements

- Node.js 18+ (for ES modules and --watch flag)
- Modern web browser with WebSocket support

## 🤝 Contributing

We welcome contributions from the community! Here's how you can help:

### Ways to Contribute

- 🐛 **Report Bugs** - Found an issue? [Open an issue](https://github.com/tubbymctubbzz/mooncord/issues)
- 💡 **Suggest Features** - Have an idea? We'd love to hear it!
- 🔧 **Submit Pull Requests** - Code contributions are always welcome
- 📖 **Improve Documentation** - Help others understand the project better
- 🎨 **Create Themes** - Design new color schemes for the community
- 🌐 **Add API Examples** - Share useful free APIs

### Development Setup

```bash
# Fork and clone the repository
git clone https://github.com/tubbymctubbzz/mooncord.git
cd mooncord

# Install dependencies
npm install

# Run in development mode
npm run dev

# Make your changes and test thoroughly
# Commit with clear, descriptive messages
# Push to your fork and open a Pull Request
```

### Code Style

- Use meaningful variable names
- Add comments for complex logic
- Follow existing code patterns
- Test your changes before submitting

## 🚀 Deployment

### Free Hosting Options

You can deploy this server for **free** on several platforms:

#### 1. **Render** (Recommended)
- ✅ Free tier available
- ✅ Auto-deploys from GitHub
- ✅ Custom domains
- ✅ SSL included

```bash
# Add to package.json
"scripts": {
  "start": "node server.js",
  "build": "echo 'No build required'"
}
```

**Steps:**
1. Push your code to GitHub
2. Go to [render.com](https://render.com)
3. Click "New +" → "Web Service"
4. Connect your GitHub repository
5. Set build command: `npm install`
6. Set start command: `npm start`
7. Deploy! 🎉

#### 2. **Railway**
- ✅ Free $5 monthly credit
- ✅ Easy GitHub integration
- ✅ Automatic HTTPS

**Steps:**
1. Visit [railway.app](https://railway.app)
2. Click "Start a New Project"
3. Select "Deploy from GitHub repo"
4. Choose your repository
5. Railway auto-detects Node.js and deploys!

#### 3. **Fly.io**
- ✅ Free tier (3 shared VMs)
- ✅ Global deployment
- ✅ CLI-based deployment

```bash
# Install Fly CLI
npm install -g flyctl

# Login and launch
fly auth login
fly launch

# Deploy
fly deploy
```

#### 4. **Glitch**
- ✅ Completely free
- ✅ Live code editor
- ✅ Instant deployment

**Steps:**
1. Go to [glitch.com](https://glitch.com)
2. Click "New Project" → "Import from GitHub"
3. Paste your repository URL
4. Your app is live instantly!

#### 5. **Cyclic**
- ✅ Free tier
- ✅ Serverless deployment
- ✅ GitHub integration

### Environment Variables

For production deployment, set these environment variables:

```bash
PORT=3000
NODE_ENV=production
```

### CORS Configuration

If hosting frontend and backend separately, update CORS in `server.js`:

```javascript
app.use(cors({
    origin: 'https://your-frontend-domain.com'
}));
```

## 📋 Requirements

- **Node.js 18+** - For ES modules and modern JavaScript features
- **Modern Browser** - Chrome, Firefox, Safari, or Edge
- **No Database Required** - Everything runs client-side!

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

### What this means:
- ✅ Free to use for personal and commercial projects
- ✅ Modify and customize as needed
- ✅ Distribute and share
- ✅ No warranty provided
- ✅ Keep the license notice

## 🌟 Show Your Support

If you find this project useful, please consider:

- ⭐ **Starring the repository** on GitHub
- 🐦 **Sharing on Twitter** with #MooncordAPI
- 📝 **Writing a blog post** about your experience
- 💬 **Telling your friends** and colleagues

## 📞 Contact & Community

- **GitHub Issues** - Bug reports and feature requests
- **Discord** - Join our community for discussions
- **Twitter** - Follow [@MooncordAPI](https://twitter.com/MooncordAPI) for updates

## 🙏 Acknowledgments

- Built with ❤️ for developers who demand excellence
- Inspired by Postman, Insomnia, and the API testing community
- Thanks to all the free API providers featured in the examples
- Special thanks to all contributors and supporters

---

<div align="center">

**Made with 🌙 by the Mooncord Community**

[⬆ Back to Top](#-mooncord-api-dev-studio)

</div>
