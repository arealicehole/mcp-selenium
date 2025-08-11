# MCP Selenium Server (Enhanced Fork)

[![MseeP.ai Security Assessment Badge](https://mseep.net/pr/angiejones-mcp-selenium-badge.png)](https://mseep.ai/app/angiejones-mcp-selenium)

> 🚀 **Enhanced fork of [@angiejones/mcp-selenium](https://github.com/angiejones/mcp-selenium)** with comprehensive testing, improved documentation, and production-ready configurations.

## 🎯 What is this?

A Model Context Protocol (MCP) server that enables AI assistants (like Claude, GPT-4, etc.) to control web browsers through Selenium WebDriver. This fork adds battle-tested configurations, detailed usage documentation, and real-world testing insights.

## ✨ Key Enhancements in This Fork

### 📊 Comprehensive Testing
- **Full test suite coverage** - All features tested on Linux environments
- **Detailed test report** - See [TEST_REPORT.md](./TEST_REPORT.md) for complete testing results
- **Real-world validation** - Tested against popular websites (Google, W3Schools, etc.)

### 📚 Improved Documentation
- **Practical usage examples** - Based on actual testing experience
- **Known limitations clearly documented** - No surprises in production
- **Best practices guide** - Avoid common pitfalls

### 🔧 Production-Ready Configurations
- **Optimized Chrome flags** for containerized environments
- **Headless mode configurations** that actually work
- **Error handling improvements** based on real usage

## 🎬 Video Demo (Original)

[![Watch the video](https://img.youtube.com/vi/mRV0N8hcgYA/sddefault.jpg)](https://youtu.be/mRV0N8hcgYA)

## 🚀 Quick Start

### For AI Assistants (Claude, etc.)

Add to your MCP client configuration:

```json
{
  "mcpServers": {
    "selenium": {
      "command": "npx",
      "args": ["-y", "@angiejones/mcp-selenium"]
    }
  }
}
```

### For Development

```bash
# Clone this fork
git clone https://github.com/arealicehole/mcp-selenium.git
cd mcp-selenium

# Install dependencies
npm install

# Run the server
npm start
```

## 🌟 Features

### Core Capabilities
- ✅ **Browser Management** - Start/stop Chrome, Firefox, Edge sessions
- ✅ **Navigation** - Navigate to any URL
- ✅ **Element Interaction** - Click, type, hover, drag & drop
- ✅ **Advanced Actions** - Double-click, right-click, keyboard input
- ✅ **Data Extraction** - Get element text, take screenshots
- ✅ **File Operations** - Upload files to web forms
- ✅ **Debugging** - Access browser console logs

### Tested & Verified Features

| Feature | Status | Notes |
|---------|--------|-------|
| Chrome Headless | ✅ Working | Use `--no-sandbox` flag |
| Firefox | ⚠️ Requires Installation | Not included by default |
| Edge | ⚠️ Requires Installation | Not included by default |
| Screenshots | ✅ Working | Returns base64 data |
| File Upload | ⚠️ Limited | File must be in browser context |
| Special Keys | ❌ Not Working | Only single characters work |
| Console Logs | ⚠️ Format Issues | Response validation errors |

## 💡 Usage Examples

### Basic Web Automation

```javascript
// Start a headless Chrome session
await startBrowser({
  browser: "chrome",
  options: {
    headless: true,
    arguments: ["--no-sandbox", "--disable-dev-shm-usage"]
  }
});

// Navigate to a website
await navigate({ url: "https://www.google.com" });

// Find and interact with search box
await sendKeys({
  by: "name",
  value: "q",
  text: "MCP Selenium Server"
});

// Take a screenshot
const screenshot = await takeScreenshot();

// Clean up
await closeSession();
```

### Advanced Interactions

```javascript
// Hover over dropdown menu
await hover({
  by: "css",
  value: ".dropdown-trigger"
});

// Double-click to edit
await doubleClick({
  by: "id",
  value: "editable-field"
});

// Right-click for context menu
await rightClick({
  by: "class",
  value: "context-menu-target"
});
```

## 🛠️ Configuration Tips

### For Docker/Containers

Always use these Chrome flags in containerized environments:

```json
{
  "headless": true,
  "arguments": [
    "--no-sandbox",
    "--disable-dev-shm-usage",
    "--disable-gpu",
    "--disable-web-security",
    "--disable-features=VizDisplayCompositor"
  ]
}
```

### For CI/CD Pipelines

```yaml
# Example GitHub Actions configuration
- name: Run Selenium Tests
  run: |
    npx -y @angiejones/mcp-selenium
  env:
    CHROME_FLAGS: "--no-sandbox --headless"
```

## 📋 Complete Tool Reference

### Browser Control
- `start_browser` - Launch browser session
- `navigate` - Go to URL
- `close_session` - Close browser

### Element Finding
- `find_element` - Locate element on page

### Element Interaction
- `click_element` - Click on element
- `send_keys` - Type text
- `get_element_text` - Extract text content

### Mouse Actions
- `hover` - Hover over element
- `drag_and_drop` - Drag element to target
- `double_click` - Double-click element
- `right_click` - Right-click for context menu

### Keyboard & Input
- `press_key` - Simulate key press
- `upload_file` - Upload file to input

### Debugging & Output
- `get_console_logs` - Retrieve browser console
- `take_screenshot` - Capture page screenshot

## ⚠️ Known Limitations

1. **Special Keys** - Keys like Tab, Enter, Escape don't work (use single characters only)
2. **File Upload** - Files must be accessible within browser's execution context
3. **Console Logs** - Response format may cause validation errors in some MCP clients
4. **Browser Installation** - Firefox and Edge require separate installation

## 🏆 Best Practices

1. **Always close sessions** - Prevent memory leaks with `close_session`
2. **Use headless mode** - Better performance and stability in production
3. **Add timeouts** - Prevent hanging on element searches
4. **Prefer CSS selectors** - More reliable than XPath
5. **Handle errors gracefully** - Wrap operations in try-catch blocks

## 🤝 Contributing

Contributions are welcome! This fork focuses on:
- Improving reliability and stability
- Adding comprehensive documentation
- Testing in various environments
- Fixing known issues

## 📄 License

MIT (same as original)

## 🙏 Credits

- Original author: [@angiejones](https://github.com/angiejones)
- Original repository: [angiejones/mcp-selenium](https://github.com/angiejones/mcp-selenium)
- This fork: Enhanced with real-world testing and production configurations

## 📞 Support

- **Issues**: [GitHub Issues](https://github.com/arealicehole/mcp-selenium/issues)
- **Original Project**: [angiejones/mcp-selenium](https://github.com/angiejones/mcp-selenium)

---

**Note**: This is an enhanced fork focused on production readiness and comprehensive documentation. For the original implementation, please visit the [original repository](https://github.com/angiejones/mcp-selenium).