# MCP Weather Server

A Model Context Protocol (MCP) server that provides real-time weather forecasts and alerts from the US National Weather Service API.

## Features

**Available Tools:**
- `get_alerts(state)` - Get active weather alerts for any US state
- `get_forecast(latitude, longitude)` - Get detailed 5-day weather forecast for specific coordinates

## Installation

### Prerequisites

Install UV package manager:

**macOS/Linux:**
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

**Windows:**
```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

### Setup

1. **Clone the repository:**
```bash
git clone https://github.com/yourusername/mcp-weather-server
cd mcp-weather-server
```

2. **Install dependencies:**
```bash
uv sync
```

Or manually:
```bash
uv add mcp httpx
```

## Usage

### Running Locally

Test the server:
```bash
uv run weather.py
```

The server will run in stdio mode and wait for MCP client connections.

### Connecting to Claude Desktop

1. **Open Claude Desktop config file:**

   **macOS:**
```bash
   code ~/Library/Application\ Support/Claude/claude_desktop_config.json
```

   **Windows:**
```powershell
   code $env:AppData\Claude\claude_desktop_config.json
```

2. **Add the weather server:**
```json
   {
     "mcpServers": {
       "weather": {
         "command": "uv",
         "args": [
           "--directory",
           "/ABSOLUTE/PATH/TO/mcp-weather-server",
           "run",
           "weather.py"
         ]
       }
     }
   }
```

   **Important:** Replace `/ABSOLUTE/PATH/TO/mcp-weather-server` with your actual path.

3. **Restart Claude Desktop**

   You should now see the weather tools (🔌 icon) in Claude Desktop.

### Connecting to Cursor IDE

1. Open Cursor Settings → MCP
2. Add the following configuration:
```json
   {
     "mcpServers": {
       "weather": {
         "command": "uv",
         "args": [
           "--directory",
           "/ABSOLUTE/PATH/TO/mcp-weather-server",
           "run",
           "weather.py"
         ]
       }
     }
   }
```
3. Restart Cursor

## Example Queries

Try asking Claude or Cursor:
- "What are the weather alerts in California?"
- "Get me the forecast for New York City (latitude 40.7128, longitude -74.0060)"
- "Are there any severe weather warnings in Texas?"

## Requirements

- Python 3.12+
- httpx
- mcp

## License

MIT

## Contributing

Pull requests are welcome! For major changes, please open an issue first.
