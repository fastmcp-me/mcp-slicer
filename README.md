[![Add to Cursor](https://fastmcp.me/badges/cursor_dark.svg)](https://fastmcp.me/MCP/Details/1151/3d-slicer)
[![Add to VS Code](https://fastmcp.me/badges/vscode_dark.svg)](https://fastmcp.me/MCP/Details/1151/3d-slicer)
[![Add to Claude](https://fastmcp.me/badges/claude_dark.svg)](https://fastmcp.me/MCP/Details/1151/3d-slicer)
[![Add to ChatGPT](https://fastmcp.me/badges/chatgpt_dark.svg)](https://fastmcp.me/MCP/Details/1151/3d-slicer)
[![Add to Codex](https://fastmcp.me/badges/codex_dark.svg)](https://fastmcp.me/MCP/Details/1151/3d-slicer)
[![Add to Gemini](https://fastmcp.me/badges/gemini_dark.svg)](https://fastmcp.me/MCP/Details/1151/3d-slicer)

<img src="https://github.com/zhaoyouj/mcp-slicer/blob/main/docs/images/logo.jpeg?raw=true" width="160" alt="logo">

# MCP-Slicer - 3D Slicer Model Context Protocol Integration

[English](README.md) | [简体中文](README_zh.md)

[![Python Version](https://img.shields.io/badge/python-3.13%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![PyPI version](https://img.shields.io/pypi/v/mcp-slicer.svg)](https://pypi.org/project/mcp-slicer/)

MCP-Slicer connects 3D Slicer with model clients like Claude Desktop or Cline through the Model Context Protocol (MCP), enabling direct interaction and control of 3D Slicer. This integration allows for medical image processing, scene creation, and manipulation using natural language.

## Features

1. list_nodes: List and filter Slicer MRML nodes and view their properties

2. execute_python_code: Execute Python code in the Slicer environment

## Installation

### Prerequisites

- 3D Slicer 5.8 or newer
- Python 3.13 or newer
- uv package manager

**If you're on Mac, please install uv as**

```bash
brew install uv
```

**On Windows**

```bash
powershell -c "irm https://astral.sh/uv/install.ps1 | iex"
```

and then

```bash
set Path=C:\Users\nntra\.local\bin;%Path%
```

Otherwise installation instructions are on their website: [Install uv](https://docs.astral.sh/uv/getting-started/installation/)

**⚠️ Please install UV first**

### Claude for Desktop Integration

Go to Claude > Settings > Developer > Edit Config > claude_desktop_config.json to include the following:

```json
{
  "mcpServers": {
    "slicer": {
      "command": "uvx",
      "args": ["mcp-slicer"]
    }
  }
}
```

### Cline Intergration

```json
{
  "mcpServers": {
    "slicer": {
      "command": "uvx",
      "args": ["mcp-slicer"]
    }
  }
}
```

## Usage

### Check Claude Settings

<img width="1045" alt="Image" src="https://github.com/zhaoyouj/mcp-slicer/blob/main/docs/images/claude_check.png?raw=true" />
Make sure you see the corresponding slicer tools added to the Claude Desktop App

<img width="300" alt="Image" src="https://github.com/zhaoyouj/mcp-slicer/blob/main/docs/images/toolsButton.png?raw=true" />
<img width="300" alt="Image" src="https://github.com/zhaoyouj/mcp-slicer/blob/main/docs/images/tools_check.png?raw=true" />

### Open Slicer Web Server

1. Open the Slicer Web Server module,
2. ensure the required interfaces are checked,
3. then start the server

<img width="1045" alt="Image" src="https://github.com/zhaoyouj/mcp-slicer/blob/main/docs/images/start_slicer_web_server.png?raw=true" />

## Examples

### - list_nodes

> What Markups nodes are in the Slicer scene now, list their names, what is their length if it is a line, and what is its angle if it is an angle

<img width="1045" alt="Image" src="https://github.com/zhaoyouj/mcp-slicer/blob/main/docs/images/example_list_nodes_en.png?raw=true" />

### - execute python code

> Draw a translucent green cube of 8 cm in the Slicer scene, mark its vertices, and then draw a red sphere inscribed in it.

<img width="1045" alt="example_code_execute_en" src="https://github.com/zhaoyouj/mcp-slicer/blob/main/docs/images/example_code_execute_en.png?raw=true" />

## Technical Details

Utilizes existing Slicer Web Server interfaces. For technical details, please see [Slicer web server user guide](https://slicer.readthedocs.io/en/latest/user_guide/modules/webserver.html)

## Limitations & Security Considerations

- The `execute_python_code` tool allows running arbitrary Python code in 3D Slicer, which is powerful but potentially dangerous.

  **⚠️ Not recommended for production use.**

- Complex operations may need to be broken down into smaller steps.

## Contributing

Contributions are welcome! Feel free to submit Pull Requests.

## Disclaimer

This is a third-party integration project, not developed by the 3D Slicer team.
