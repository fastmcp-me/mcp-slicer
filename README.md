<img src="https://private-user-images.githubusercontent.com/107615029/425557131-ab8e86c3-0795-4a11-ad44-30e0b878f172.jpeg?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDI1NzM5ODIsIm5iZiI6MTc0MjU3MzY4MiwicGF0aCI6Ii8xMDc2MTUwMjkvNDI1NTU3MTMxLWFiOGU4NmMzLTA3OTUtNGExMS1hZDQ0LTMwZTBiODc4ZjE3Mi5qcGVnP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI1MDMyMSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNTAzMjFUMTYxNDQyWiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9ZDhlNjQ2ZDQzZmU2ZmQzZjQxNjIxZTY3OTQ4YzgzNmIxYzdhMzJmMzQ5YTJiYWU1ZGE2MWM5NTlhNDg2YTY4ZCZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QifQ.wzJaAyEXfbvE2MsDXLDzfjROfevmomRGwYThSyscKEE" width="160" alt="logo">

# MCP-Slicer - 3D Slicer Model Context Protocol Integration

[![Python Version](https://img.shields.io/badge/python-3.13%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![PyPI version](https://img.shields.io/pypi/v/mcp-slicer.svg)](https://pypi.org/project/mcp-slicer/)

MCP-Slicer 通过模型上下文协议(MCP)将 3D Slicer 与 例如 Claude Desktop 或 Cline 等模型客户端连接起来，使之能够直接与 3D Slicer 交互和控制。这种集成实现了用自然语言进行医学影像处理、场景创建和操作。

## Features

1. list_nodes: 用于列出和过滤 Slicer MRML 节点并查看其属性

2. execute_python_code: 允许在 Slicer 环境中执行 Python 代码

## Installation

### Prerequisites

- 3D Slicer 5.8 或更新版本
- Python 3.13 或更新版本
- uv 包管理器

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

**⚠️ 请先安装 UV**

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

### Open Slicer Web Server
先打开Slicer的Web Server模组，确保勾选所需的接口，再启动服务器
<img width="1045" alt="Image" src="https://private-user-images.githubusercontent.com/107615029/425557151-2b27644d-e6a8-4970-8e25-5cbf8011ae59.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDI1NzM5ODIsIm5iZiI6MTc0MjU3MzY4MiwicGF0aCI6Ii8xMDc2MTUwMjkvNDI1NTU3MTUxLTJiMjc2NDRkLWU2YTgtNDk3MC04ZTI1LTVjYmY4MDExYWU1OS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzIxJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMyMVQxNjE0NDJaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT00MTQ2Zjk0ZGZhODgyM2VkZjk2ZDM2NmVmZmJlY2Q1NTA0Y2MyNzA3MzkzZWJkY2JhYzM2NmIyZDE2ZDZkOGZmJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.rlJ0JDvmPcmtNLk4xgmSGqrKEWx6vMAbcXexzYDoFQk" />

## Technical Details

借助了 Slicer Web Server 现有接口，技术细节请查看 [Slicer web server user guide](https://slicer.readthedocs.io/en/latest/user_guide/modules/webserver.html)

## Limitations & Security Considerations

- `execute_python_code` 工具允许在 3D Slicer 中运行任意 Python 代码，这很强大但也可能存在潜在危险。

  **⚠️ 请勿在生产环境中使用。**

- 复杂操作可能需要分解为更小的步骤。

## Contributing

欢迎贡献！请随时提交 Pull Request。

## Disclaimer

这是一个第三方集成项目，不是由 3D Slicer 官方开发。
