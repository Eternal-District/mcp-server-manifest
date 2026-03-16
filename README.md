
# District MCP Server

An MCP server for dining restaurant discovery, table reservations, and movie discovery — powered by District.

## Supported Features

### 🍽️ Dining

- 🔍 **Restaurant Discovery** – Search for dining restaurants near you using semantic search, with smart filters for cuisine, rating, and more.
- 📋 **Restaurant Details** – Get comprehensive details about any restaurant including ratings, timings, address, reviews, and highlights.
- 📅 **Table Reservations** – Check available time slots and book a table at your favorite restaurants, with exclusive offers.
- 🍽️ **Booking Management** – Track your reservation status and get booking confirmations.

### 🎬 Movies & Entertainment

- 🎥 **Movie Search** – Discover movies currently playing in theaters or upcoming releases, filtered by genre, language, cast, and more.
- 🏢 **Theatre Search** – Find nearby theaters with details on amenities, screen types (IMAX, 4DX, Dolby Atmos), and distance.
- 🕐 **Showtime Search** – Get specific showtimes, seat availability, and pricing for any movie at any theater.
- ⭐ **Movie Reviews** – Get critic reviews and ratings for any movie to help you decide what's worth watching.

## Installation Guide

⚠️ **OAuth Redirect URI Warning:** Currently, we have only whitelisted the following redirect URIs for OAuth authentication. Please reach out to us to enable your client:
- `claude://claude.ai/settings/connectors`
- `https://chatgpt.com/connector_platform_oauth_redirect`
- `https://claude.ai/api/mcp/auth_callback`
- `https://insiders.vscode.dev/redirect`
- `https://oauth.pstmn.io/v1/callback`
- `https://vscode.dev/redirect`

### Install on VS Code

<b>One Click Installation</b>

[![Install MCP](https://img.shields.io/badge/Install-DistrictMCP-E23744)](https://insiders.vscode.dev/redirect?url=vscode:mcp/install?%7B%22type%22%3A%22http%22%2C%22name%22%3A%22District%20MCP%20Server%22%2C%22version%22%3A%220.0.1%22%2C%22description%22%3A%22MCP%20server%20to%20interact%20with%20District%20services%22%2C%22url%22%3A%22https%3A%2F%2Fmcp-server.district.in%2Fmcp%22%2C%22author%22%3A%22District%22%2C%22tags%22%3A%5B%22district-mcp%22%2C%22mcp%22%2C%22server%22%5D%2C%22categories%22%3A%5B%22mcp%22%5D%7D)

<b>Manual Installation</b>

Add this to your `mcp.json` file.

```json
{
    "servers": {
        "district-mcp-server": {
            "url": "https://mcp-server.district.in/mcp",
            "type": "http"
        }
    }
}
```


### Install on Claude

<b> Using Connectors (Requires claude subscription) </b>
1. Open Claude
2. Go to Settings -> Connectors -> Add custom connector
3. Use the URL: `https://mcp-server.district.in/mcp`
4. Save and Restart Claude


<b> Using Manual Configuration (Available on free plan) </b>
1. Open Claude
2. Go to Settings -> Developer -> Edit Config
3. Open `claude_desktop_config.json` in a text editor.
4. Add the following configuration:
    ```json
    {
        "mcpServers": {
            "district-mcp-server": {
                "command": "npx",
                "args": [
                    "mcp-remote",
                    "https://mcp-server.district.in/mcp"
                ]
            }
        }
    }
    ```

## Example Prompts

Get started with these example prompts to explore what the District MCP server can do:

### Dining
- "Find the best rated restaurants near Koramangala, Bangalore"
- "Show me Italian restaurants in Connaught Place, Delhi"
- "Restaurants with outdoor seating near Indiranagar, Bangalore"
- "Find a romantic restaurant for a date night in Bandra, Mumbai"
- "Show me restaurants with live music near Cyber Hub, Gurugram"
- "Book a table for 2 at a restaurant near Koramangala for Saturday"

### Movies
- "What movies are playing near Koramangala, Bangalore?"
- "Find theaters near Cyber Hub, Gurugram"
- "Show me showtimes for Goat in English near Koramangala"
- "What are the ticket prices for Border 2 near Indiranagar?"
- "Show me upcoming English movies near me"
- "Find comedy movies playing near Koramangala, Bangalore"

## Future Scope

Our vision is to make District MCP the ultimate destination for going-out discovery. We're actively working on expanding it with the following capabilities:

- 💳 **Quick Checkout for Movies** – Seamless movie ticket purchasing with integrated payments, enabling end-to-end booking directly through the MCP.
- 🎭 **Event Discovery** – Discover and explore events, concerts, activities, and experiences across cities.
- 🗺️ **Outing Planner** – Plan your complete outing — discover must-visit places, restaurants, and experiences near popular tourist attractions, all in one go.
- 🛒 **Unified Checkout** – A single, streamlined checkout experience spanning movies, dining, events, and activities — all in one flow.
- 🎾 **Sports Discovery** – Explore courts and sports hubs to play, compete, and stay active.


## Disclaimer
- We are not allowing any third party apps to be built on top of District MCP right now due to security and legal considerations. Please reach out to us for any integration discussions.

- This is only for testing purposes and District disclaims any and all liabilities that may arise due to erroneous / non-functionality of the MCP integration.
