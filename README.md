# qs-first-mcp

This repository provides a simplified implementation of Anthropic's Model Context Protocol (MCP) quickstart guide. 

The repo achieves this goal by creating and centralizing the setup of a MCP [tool](https://modelcontextprotocol.io/docs/concepts/tools#tools), in this case, a basic weather server using Python, connected to Claude for Desktop.

## System Requirements
- Python 3.10 or higher
- `uv` (download from Astral's [repo](https://github.com/astral-sh/uv))
- Claude for Desktop (download from [Anthropic's website](https://www.anthropic.com/claude-for-desktop))



## Setup
### 1. **Clone and install dependencies**

```bash
git clone git@github.com:SSGrady/qs-first-mcp.git
cd qs-first-mcp/weather
uv add "mcp[cli]" httpx
```

### 2. **Configure Claude:**
 - On VSCode (or Cursor/Windsurf) open:
  
  ```bash
  code ~/Library/Application\ Support/Claude/claude_desktop_config.json
  ```

 - next, go ahead and add:
 ```json
{
    "mcpServers": {
        "weather": {
            "command": "[UV_PATH]",
            "args": [
                "--directory",
                "~/qs-first-mcp/weather",
                "run",
                "weather.py"
            ]
        }
    }
}
```
#### 💡 You can find UV_PATH by running `which uv` 

### 3. **Restart Claude for Desktop**

#### 💡 If you fix any bugs, make sure to repeat step 3

## Usage

Try asking Claude about any USA weather:
- "What's the weather in Orlando?"
- "What are the active weather alerts in California?"

## More Info

- This uses the National Weather Service API (USA only)
- See [MCP debugging docs](https://modelcontextprotocol.io/docs/tools/debugging) for help with any errors