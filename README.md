# 🏭 Camunda Engine MCP Server

[![Production Ready](https://img.shields.io/badge/Production-Ready-green.svg)](PRODUCTION_READINESS_REPORT.md)
[![Docker](https://img.shields.io/badge/Docker-Supported-blue.svg)](https://hub.docker.com)
[![MCP](https://img.shields.io/badge/MCP-Compatible-purple.svg)](https://modelcontextprotocol.io)
[![Camunda](https://img.shields.io/badge/Camunda-7.19+-orange.svg)](https://camunda.com)

A **Model Context Protocol (MCP) server** that enables AI assistants to interact with **Camunda Platform** workflow engine. Provides **27 specialized tools** for complete workflow automation and process management.

**✅ PRODUCTION READY** - Fully tested, containerized, and ready for deployment.

## 🚀 Quick Start

### 1. Start the Server
```bash
git clone <repo-url>
cd camunda-engine-mcp
docker-compose up -d
```

### 2. Configure Claude Desktop
Add to your Claude Desktop MCP settings:

```json
{
  "mcpServers": {
    "camunda": {
      "command": "docker",
      "args": [
        "exec", "-i",
        "-e", "CAMUNDA_BASE_URL=https://your-camunda-instance.com/engine-rest",
        "-e", "CAMUNDA_USERNAME=your-username",
        "-e", "CAMUNDA_PASSWORD=your-password",
        "camunda-mcp-server",
        "node", "build/index.js"
      ]
    }
  }
}
```

### 3. Restart Claude Desktop
Completely close and restart Claude Desktop to load the MCP server.

### 4. Test Connection
Try these commands in Claude Desktop:
```
Show me all available processes in Camunda
```
```
Get the list of current tasks from Camunda
```
```
Deploy BPMN from file /workspace/bpmn/simple-process.bpmn
```

## 🎯 Features

- **27 MCP Tools** for complete Camunda workflow management
- **Process Management** - Deploy, start, monitor BPMN processes
- **Task Management** - Handle user tasks and forms
- **External Tasks** - List, inspect, complete, prioritize and unlock worker tasks
- **Large File Support** - Deploy big BPMN files via file paths
- **Production Ready** - Docker, monitoring, health checks
- **Real-time Integration** - Direct connection to live Camunda instances

## 📁 File Deployment

For large BPMN/form files, place them in directories:
```bash
./bpmn-files/your-process.bpmn    # → /workspace/bpmn/your-process.bpmn
./forms/your-form.form            # → /workspace/forms/your-form.form
```

Then use file paths instead of content:
```
Deploy BPMN from file /workspace/bpmn/your-process.bpmn
```

## 📚 Documentation

- **[Setup Guide](SETUP_GUIDE.md)** - Detailed configuration and all 27 tools
- **[Troubleshooting](TROUBLESHOOTING.md)** - Common issues and solutions
- **[Testing Guide](TESTING_GUIDE.md)** - Comprehensive testing framework
- **[Production Report](PRODUCTION_READINESS_REPORT.md)** - Production readiness details

## 🔧 Environment Variables

```bash
CAMUNDA_BASE_URL=https://your-camunda-instance.com/engine-rest
CAMUNDA_USERNAME=your-username
CAMUNDA_PASSWORD=your-password
```

## 🧪 Health Check

```bash
docker exec camunda-mcp-server npm run health-check
```

## 📞 Support

- **Issues**: Check [Troubleshooting Guide](TROUBLESHOOTING.md)
- **Setup**: See [Setup Guide](SETUP_GUIDE.md)
- **Testing**: Run `npm run health-check`

---

**Ready to automate your workflows with AI? Start with the Quick Start above!** 🚀