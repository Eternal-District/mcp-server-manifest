
# District MCP Server

An MCP server for dining restaurant discovery, table reservations, and movie discovery — powered by District.

## Supported Features

### 🍽️ Dining

- 🔍 **Restaurant Discovery** – Tell it what you're craving and where you are — it finds the best options nearby.
- 📅 **Table Reservations** – Check open slots and book a table at your favourite restaurant, with exclusive offers included.
- 🍽️ **Booking Management** – Track your reservation and get confirmation, all in one place.

### 🎬 Movies & Entertainment

- 🎥 **Movie Search** – Find what's playing or coming soon — by genre, language, cast, or anything else you have in mind.
- 🏢 **Theatre Search** – Discover nearby theatres with screen formats (IMAX, 4DX, SCREEN X) and amenities.
- 🕐 **Showtime Search** – Get showtimes, seat categories, and ticket prices for any movie at any theatre.
- ⭐ **Movie Reviews** – Read critic reviews and ratings before you decide what to watch.

## Use Cases

### 🍽️ Dining

**Spontaneous Dining Discovery**
> "Find me the best-rated restaurants near Koramangala open right now"

Just say where you are and what you want — it finds top-rated restaurants nearby, instantly.

**Occasion-Based Restaurant Planning**
> "Find a romantic rooftop restaurant for a date night in Bandra, Mumbai"

Planning a date night or a birthday dinner? Describe the vibe — rooftop, cozy, outdoor — and it'll match you with the right place.

**Cuisine & Diet Exploration**
> "Show me vegan-friendly Italian restaurants near Indiranagar, Bangalore"

Want vegan? Italian? Both? Just ask — it'll find restaurants that match exactly.

**Last-Minute Table Booking**
> "Any tables available tonight for 2 near MG Road?"

Need a table tonight? Check what's open right now and book it — any active offers are included automatically.

**Group Outing Coordination**
> "Book a table for 8 at a restaurant with a private dining area near Cyber Hub, Gurugram for Saturday evening"

Going out with a large group? Find a place that fits everyone, check if there's a slot, and book — without the back and forth.

---

### 🎬 Movies & Entertainment

**Movie Discovery by Preference**
> "What Hindi action movies are playing near Whitefield, Bangalore this weekend?"

Tell it the language, genre, or actor you're in the mood for — it'll show you what's playing now or coming up soon.

**Premium Format Show Finding**
> "Find SCREEN X shows for Raja Shivaji near Connaught Place, Delhi"

Want to watch a specific movie in SCREEN X or IMAX? Find exactly which nearby theatres have it — no manual searching across theatres.

**Showtime & Seat Price Lookup**
> "What are the evening showtimes and ticket prices for Bhooth Bangla near Andheri, Mumbai?"

Know exactly when a movie is playing, which seats are available, and what they cost — before you even open a booking app.

**Critic Review Deep-Dive**
> "Is Dhurandhar The Revenge worth watching? Show me critic reviews"

Not sure if a movie is worth your time? Read what the critics say before you buy the ticket.

**Theatre Discovery**
> "Find theatres near Koramangala"

Find theatres near you and see what each one offers — screen formats, recliner seats, parking, food options, and more.

**Family & Kids Movie Planning**
> "Find UA13+ comedy movies playing near Jayanagar, Bangalore"

Planning a family outing? Pick an age rating and genre, and find a movie everyone will enjoy — with showtimes near you.

---

### 🗓️ End-to-End Evening Planning

**Full Evening Out (Movie + Dinner)**
> "Plan a movie and dinner evening near Bandra for 2 — good Hindi movie and a nice restaurant after"

Pick a movie, lock in a showtime, then find a good restaurant nearby for dinner after — and book the table too, all in one go.

**Weekend Group Outing**
> "Plan a Saturday afternoon for 4 people near Cyber Hub — movie and dinner"

Find a movie with afternoon shows, pick a spot for lunch or dinner nearby, and get the table booked — the whole Saturday sorted in one conversation.

---

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
