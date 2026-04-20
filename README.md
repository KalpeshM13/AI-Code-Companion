# 🤖 GPT-2 Local Autocomplete

<div align="center">

**VS Code Extension for Local AI Code Completion**

_A lightweight VS Code extension that provides AI-powered code completion through a local Python backend._

[![Version](https://img.shields.io/badge/Version-0.0.1-orange.svg)](#)
[![VS Code Marketplace](https://img.shields.io/badge/VS_Code-Marketplace-blue?logo=visual-studio-code)](https://marketplace.visualstudio.com/)

</div>

---

## 📋 **About This Extension**

This is the **VS Code extension component** of GPT-2 Local Copilot. It provides the frontend interface for AI-powered code completion while keeping all AI processing local to your machine.

### **Key Features**

- 🎨 **Ghost Text UI**: Inline code suggestions as you type
- ⚡ **Real-time Completion**: Debounced requests with 300ms delay
- 🔄 **Smart Caching**: Reuses predictions for consecutive typing
- 🎯 **Multi-line Support**: Intelligent detection for functions and classes
- 📊 **Status Bar Integration**: Visual toggle for extension control
- 🔧 **Auto Server Management**: Automatically starts/stops Python backend

---

## 🛠️ **Technical Details**

### **Architecture**

```
VS Code Extension (TypeScript)
├── Inline Completion Provider
├── Status Bar Integration
├── Process Management
└── HTTP Client (Axios)
```

### **Requirements**

- **VS Code**: 1.80.0 or later
- **Python Backend**: Running on `http://127.0.0.1:8000`
- **Dependencies**: Axios for HTTP requests

### **Supported Languages**

- ✅ Python (optimized)
- ✅ JavaScript/TypeScript
- ✅ General programming languages

---

## 🚀 **Quick Start**

### **Development Mode**

#### **Step 1: Backend Setup**
```bash
# Install Python dependencies
pip install -r extension/requirements.txt
```

#### **Step 2: Extension Setup**
```bash
# Navigate to extension directory
cd extension

# Install Node.js dependencies
npm install

# Compile TypeScript
npm run compile
```

#### **Step 3: Development Mode**
```bash
# Open project in VS Code
code .

# Press F5 to launch Extension Development Host
# This opens a new VS Code window with the extension loaded
```

#### **Step 4: Packaging (Optional)**
```bash
# Install VS Code Extension Manager
npm install -g @vscode/vsce

# Package the extension
cd extension
vsce package

# Install locally
code --install-extension gpt2-local-autocomplete-0.0.1.vsix
```

---

### **Using the Extension**

1. **Start Backend**: Ensure Python server is running
2. **Launch Extension**: Press `F5` in VS Code
3. **Start Coding**: Open any code file and begin typing
4. **Accept Suggestions**: Press `Tab` to accept ghost text

---

## ⚙️ **Configuration**

### **Extension Settings**

Access via VS Code Settings (`Ctrl/Cmd + ,`):

```json
{
  "codeCompletion.serverUrl": "http://127.0.0.1:8000"
}
```

### **Status Bar**

- **$(zap) GPT-2: ON**: Extension active
- **$(circle-slash) GPT-2: OFF**: Extension disabled
- **Click** to toggle on/off

---

## 🔧 **Development**

### **Project Structure**

```
extension/
├── src/
│   └── extension.ts      # Main extension logic
├── out/                  # Compiled JavaScript (generated)
├── package.json          # Extension manifest
├── tsconfig.json         # TypeScript configuration
└── icon.svg              # Extension icon
```

### **Available Scripts**

```bash
npm run compile      # Build TypeScript to JavaScript
npm run watch        # Watch mode compilation
npm run pretest      # Run linting before tests
npm run lint         # ESLint code checking
```

### **Building for Distribution**

```bash
# Install VS Code Extension CLI
npm install -g @vscode/vsce

# Package extension
vsce package

# Publish to marketplace
vsce publish
```

---

## 🔌 **API Integration**

The extension communicates with the Python backend via HTTP:

### **Request Format**

```typescript
POST /predict
{
  "code_context": "def hello",
  "multiline": false
}
```

### **Response Format**

```typescript
{
  "completion": "_world():\n    return 'Hello World'"
}
```

### **Error Handling**

- Automatic retry on connection failures
- Graceful degradation when server is unavailable
- Detailed logging in VS Code Output panel

---

## 🐛 **Troubleshooting**

### **Extension Issues**

| Problem                      | Solution                                |
| ---------------------------- | --------------------------------------- |
| **Extension not activating** | Check VS Code version (1.80+)           |
| **No suggestions appear**    | Verify Python server is running         |
| **Status bar not visible**   | Restart VS Code or reload window        |
| **Compilation errors**       | Run `npm install` and `npm run compile` |

### **Debug Information**

- **Logs**: View → Output → Log (Extension Host)
- **Server Status**: Check `http://127.0.0.1:8000/docs`
- **Network**: Test with curl: `curl -X POST http://127.0.0.1:8000/predict -H "Content-Type: application/json" -d '{"code_context": "test", "multiline": false}'`

---

## 📊 **Performance**

### **Response Times**

- **Cache Hit**: ~10-50ms
- **GPU Inference**: ~50-200ms
- **CPU Inference**: ~200-800ms

### **Resource Usage**

- **Memory**: ~50MB (extension only)
- **Network**: Localhost HTTP requests
- **CPU**: Minimal background processing

---

## 🤝 **Contributing**

### **Code Contributions**

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

### **Extension Development**

- Follow TypeScript best practices
- Use ESLint configuration
- Test on multiple platforms
- Document new features

### **Reporting Issues**

- Use GitHub Issues for bugs
- Include VS Code version and OS
- Provide steps to reproduce
- Attach relevant logs

---

## 📄 **License**

(**MIT License**)[https://github.com/KalpeshM13/AI-Code-Companion/blob/main/LICENSE]

## 🔗 **Links**

- (**Main Repository**)[https://www.github.com/KalpeshM13/AI-Code-Companion]
- (**Issues**)[https://github.com/KalpeshM13/AI-Code-Companion/issues]
- (**Documentation**)[https://github.com/KalpeshM13/AI-Code-Companion#-gpt-2-local-autocomplete]
