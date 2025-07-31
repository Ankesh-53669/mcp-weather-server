# 🌤️ MCP Weather and Quotes Server

This is a lightweight MCP (Model Context Protocol) server built using [FastMCP](https://github.com/anthropics/fastmcp). It connects with **Claude for Desktop** and exposes useful tools like:

- 🌦️ US weather forecasts and alerts

---

## 📋 Features

| Tool           | Description                                             |
|----------------|---------------------------------------------------------|
| `get_forecast` | Fetches a 5-period weather forecast by coordinates      |
| `get_alerts`   | Lists current weather alerts for a US state             |


---

## 🧰 Prerequisites

- Python 3.10 or later
- [Claude for Desktop](https://www.anthropic.com/claude)
- [uv](https://github.com/astral-sh/uv) (Python package manager)
- Git

---

## ⚙️ Setup Instructions

### 1. 📥 Install Claude for Desktop

Download and install from:  
👉 https://www.anthropic.com/claude

Once installed, **open Claude once** to generate its configuration directory.

---

### 2. 📦 Install `uv` (one-time setup)

Open PowerShell and run:

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

Then **restart your terminal**, or run:

```powershell
$env:Path = "C:\Users\admin\.local\bin;$env:Path"
```

---

### 3. 📁 Clone the Repository

```bash
git clone https://github.com/your-username/mcp-weather-and-quotes.git
cd mcp-weather-and-quotes
```

---

### 4. 🐍 Set Up Python Environment

```bash
uv venv
.venv\Scripts\activate         # On Windows
# OR
source .venv/bin/activate        # On macOS/Linux

uv add mcp[cli] httpx
```

---

### 5. 🧠 Configure Claude to Detect the MCP Server

Open this file in VS Code or Notepad:

```powershell
code "$env:AppData\Claude\claude_desktop_config.json"
```

If the file doesn’t exist, create it. Then paste the following JSON configuration:

```json
{
  "mcpServers": {
    "weather": {
      "command": "C:\\Users\\admin\\.local\\bin\\uv.exe",
      "args": [
        "--directory",
        "C:\\Users\\admin\\mcp-weather-and-quotes",
        "run",
        "weather.py"
      ]
    }
  }
}
```

> 🔁 Make sure all paths are correct and absolute. Use double backslashes (`\\`) or forward slashes (`/`).

---

### 6. ▶️ Run the MCP Server

From the project directory, run:

```bash
uv run weather.py
```

This will start your MCP server using STDIO.

---

## 🧪 Using the Tools in Claude

1. Restart Claude for Desktop  
2. Click the **slider icon** (top-right) to open Tools  
3. You should see the following tools:
   - `get_forecast`
   - `get_alerts`


---

### 💬 Example Prompts to Try

- `"What's the forecast for 38.58, -121.49?"`
- `"Any active alerts in Texas?"`


Claude will automatically decide whether to call your tool and display the result.

---

## 📂 Project Structure

```
mcp-weather-and-quotes/
├── weather.py                # Main MCP server code
├── README.md                 # This file
└── .venv/                    # Virtual environment (optional)
```

---

## 🙏 APIs Used

- US Weather: https://api.weather.gov

---

## 📝 License

MIT License – use it, share it, extend it!