
# District MCP Server

An MCP server for movie shows, restaurant tables, events, activities, sports courts and salon appointments, powered by District.

- **Endpoint:** `https://mcp-server.district.in/v2/mcp` (Streamable HTTP)
- **Sign-in:** District mobile number and OTP, or start as a guest and log in when you book
- **Works with:** Claude, ChatGPT, Cursor, VS Code and Claude Code
- **Website:** [studio.district.in/mcp](https://studio.district.in/mcp/)

## Tools

Everything runs through four core tools. Your assistant finds what it needs with `search`, then calls the tool that result names.

| Tool | What it does |
|---|---|
| `search` | Finds the District operations and recipes that answer the request. Always called first; each result says which tool to call next and with what arguments. |
| `execute` | Runs a read-only operation: shows, slots, menus, prices, offers and your bookings. It never books, pays or changes anything. |
| `act` | Runs an operation that changes something: holds seats or a court, books, cancels or saves to a list. It runs only after you confirm. |
| `pay` | Starts the UPI payment for a booking or bill, with the method you picked. It runs only after you confirm the amount and method. |

Supporting tools: `pay` comes with `payment_options` (the UPI QR to pay with) and `payment_status` (checks whether the payment went through). Signing in from the chat uses `generate_otp`, `resend_otp` and `validate_otp`.

## What it can do

It asks you before it books, pays or cancels.

### 🎬 Movies

Find what's showing, pick a show and seats, add popcorn, apply an offer and pay. All in the chat.

- 🔍 **Movies and showtimes** – What's showing near you, by language, genre or format, with show times, seat prices and how many seats are left.
- ⭐ **Movie and cinema details** – Cast, runtime, certificate, ratings and synopsis. For a cinema: its screens, amenities and policies.
- 🎟️ **Book movie seats** – Pick seats from the live seat map and hold them. Add food, apply a promo code or District Money, then pay with UPI.
- 🏷️ **Ticket offers** – Promo codes, bank offers and rewards for a movie, a cinema or the show you picked.

### 🍽️ Dining

Tell it what you're craving and where. It finds places, books a table and pays the bill when you're done.

- 🔍 **Find a restaurant** – Search by name or browse places to eat near you, with ratings, cost for two, opening hours, menus, reviews and offers.
- 📅 **Book a table** – See open slots for your party size, check the bill, then book. If the table needs an online payment, pay it with UPI.
- 💳 **Pay the bill** – Pay at the restaurant from the chat, with the best offer and your DineCoins if you have any.
- 📋 **Manage table bookings** – Check a reservation, or cancel it and see what's refunded.

### 🎭 Events & activities

Concerts, comedy, workshops and weekend plans. See dates and ticket prices, then book.

- 🔍 **Find something to do** – Concerts, comedy, parties, workshops and more near you. Browse by mood, or look up an artist or a venue.
- 🕐 **Dates and tickets** – An event's schedule, ticket types and prices. For activities, the open dates and time slots.
- 🎟️ **Book event tickets** – Hold the tickets you want in the cart, see the total and pay with UPI.

### 🎾 Sports

Find a turf or a court, see what's available and book it for as long as you want to play.

- 📍 **Find a court** – Turfs, badminton and pickleball courts, box cricket and more. See the sports, courts and prices at a venue.
- 🕐 **Available slots** – Open time slots and courts for a sport, on the date and for as long as you want to play.
- 📅 **Book a court** – Hold the court and slot, add equipment or a promo code, and pay with UPI.
- ❌ **Cancel a court booking** – See the venue's cancellation policy and your refund, then cancel.

### 💇 Salons

See services and prices, pick an available slot and book. Pay the bill from the chat after your visit.

- 🔍 **Services and prices** – A salon's service menu with prices, plus its location, hours, rating and offers.
- 🕐 **Appointment slots** – The dates and time slots that are open, and which stylists are in.
- 📅 **Book an appointment** – Price the services, then pay the booking amount with UPI. It comes off your bill at the salon.
- 💳 **Pay the salon bill** – After your visit, pay the bill from the chat. Any booking amount you paid is taken off.

### 👤 Your bookings

Ask about what you've booked. Your tickets, refunds, lists and reminders, without opening the app.

- 📋 **Your bookings** – All your District bookings, and the details of any one of them.
- 🎟️ **Movie tickets and refunds** – Your ticket and entry QR for a show, or how much comes back if you cancel. Cancelling a movie ticket is done in the District app.
- ➕ **Lists and reminders** – Save restaurants, events and more to your Hotlist or your own lists, and see your movie reminders.

## Recipes

A recipe is a set of steps for a multi-step task, such as booking movie tickets or paying a bill. `search` returns recipes along with operations. Each step names the [tool](#tools) it uses.

### Book

**Book movie tickets** (`recipe.book_movie_tickets`)
> "Book 2 seats for an evening show near Andheri tonight"

Pick the movie, the show and your seats. The seats are held while you add food or an offer, then you pay with UPI.
Find the movie → Pick a show → Choose seats → Hold them → Final price → Pay with UPI

**Book a table** (`recipe.book_table`)
> "Table for 4 at 8 pm on Saturday near Indiranagar"

Find the restaurant, pick a time and party size, and check the bill. If the booking needs no payment, it's confirmed straight away. If it does, you pay with UPI.
Find the restaurant → Open slots → Check the bill → Book → Pay if needed

**Book event tickets** (`recipe.book_event_tickets`)
> "2 tickets for a stand-up show in Bengaluru this Saturday"

Concerts, comedy, parties and festivals. Pick the show and ticket types, hold them in the cart and pay with UPI.
Find the event → Dates and tickets → Hold tickets → Pay with UPI

**Book an activity** (`recipe.book_activity`)
> "Find a pottery workshop next Sunday and book one spot"

Workshops, classes and experiences. Pick a date and a time slot, even beyond the next week, then hold tickets and pay.
Find the activity → Pick a date → Pick a slot → Hold tickets → Pay with UPI

**Book a sports court** (`recipe.book_play_slot`)
> "Book a badminton court near HSR Layout for an hour at 7 am tomorrow"

Turf, badminton, pickleball or box cricket. Pick the sport, date, duration, time and court, then pay.
Find the venue → Available slots → Hold the court → Pay with UPI

**Book a salon appointment** (`recipe.book_salon`)
> "Haircut and beard trim near Koramangala on Sunday morning"

Pick the services and an open slot with the best available stylist. You pay a booking amount now, and it comes off your bill at the salon.
Find the salon → Pick services → Available slot → Price it → Pay with UPI

### Pay

**Pay a restaurant bill** (`recipe.pay_bill`)
> "Pay my ₹1,850 bill here with the best offer"

After your meal, pay the bill from the chat. It looks for the best offer and uses your DineCoins if you want.
Find the restaurant → Price the bill → Pick an offer → Pay with UPI → Confirm it went through

**Pay a salon bill** (`recipe.pay_salon_bill`)
> "Pay my salon bill of ₹1,200"

After your visit, pay the salon or another District store from the chat. A booking amount you already paid is taken off.
Find the store → Price the bill → Pay with UPI

### Find

**Find an available court** (`recipe.find_play_slot`)
> "Any football turf available near Andheri tonight?"

See which sports a venue has and its open slots for a date. To book one, it moves on to the sports court recipe.
Find the venue → Sports and courts → Available slots

**Find a salon slot** (`recipe.find_salon_slot`)
> "When can I get a manicure near Bandra this week?"

Find a salon, the service you want and its open time slots.
Find the salon → Pick the service → Available slots

### Manage

**Show my movie ticket** (`recipe.show_movie_ticket`)
> "Show my ticket for tonight's movie"

Finds your booking and shows the show, seats, screen and the entry QR text.
Your bookings → Ticket and QR

**Check a movie refund** (`recipe.movie_refund_check`)
> "If I cancel my movie tickets for tomorrow, how much do I get back?"

Tells you if a ticket can still be cancelled and how much comes back. You cancel it in the District app.
Your bookings → Refund quote

**Cancel a table booking** (`recipe.cancel_table_booking`)
> "Cancel my table booking for Friday"

Checks the booking can still be cancelled and what's refunded, then cancels it once you confirm.
Your bookings → Can it be cancelled? → Cancel

**Cancel a court booking** (`recipe.cancel_play_booking`)
> "Cancel my badminton booking for tomorrow morning"

Checks the venue's cancellation policy and your refund, and cancels only after you agree.
Your bookings → Policy and refund → Cancel

**Save to a list** (`recipe.save_to_list`)
> "Save this restaurant to my Hotlist"

Saves a restaurant, event, movie, cinema, store or artist to your Hotlist or one of your lists.
Find it → Pick a list → Save

## Installation Guide

Your app opens District sign-in in the browser. Log in with your mobile number and OTP, or continue as a guest. Never put tokens in a config file.

⚠️ **OAuth redirect URIs:** Only the following redirect URIs are currently allowed for sign-in. Other apps can't sign in until District enables them, so write to [developers@district.in](mailto:developers@district.in) if you need one:
- `claude://claude.ai/settings/connectors`
- `https://chatgpt.com/connector_platform_oauth_redirect`
- `https://claude.ai/api/mcp/auth_callback`
- `https://insiders.vscode.dev/redirect`
- `https://oauth.pstmn.io/v1/callback`
- `https://vscode.dev/redirect`

### Claude

Add District as a custom connector. Availability depends on your Claude plan. No config file.

1. Open Claude and go to **Settings → Connectors**.
2. Choose **Add custom connector**.
3. Name it `District` and paste the endpoint: `https://mcp-server.district.in/v2/mcp`
4. Connect, and sign in with District when asked.

<b>Using manual configuration (Claude Desktop, available on the free plan)</b>

1. Open Claude and go to **Settings → Developer → Edit Config**.
2. Open `claude_desktop_config.json` in a text editor.
3. Add the following configuration:
    ```json
    {
        "mcpServers": {
            "district": {
                "command": "npx",
                "args": [
                    "mcp-remote",
                    "https://mcp-server.district.in/v2/mcp"
                ]
            }
        }
    }
    ```
4. Save and restart Claude.

### ChatGPT

Add District as a custom connector. Availability depends on your ChatGPT plan. No config file.

1. Open ChatGPT and go to **Settings → Apps & Connectors**.
2. Add a custom connector named `District` and paste the endpoint: `https://mcp-server.district.in/v2/mcp`
3. Sign in with District when asked.
4. Turn District on in a chat and ask.

### Cursor

Add this to `~/.cursor/mcp.json`, or to `.cursor/mcp.json` in your project. Then sign in to District from Cursor's MCP settings when asked, and ask in chat.

```json
{
  "mcpServers": {
    "district": {
      "url": "https://mcp-server.district.in/v2/mcp"
    }
  }
}
```

### VS Code

Works in VS Code and VS Code Insiders.

<b>One-click installation</b>

[![Install MCP](https://img.shields.io/badge/Install-DistrictMCP-E23744)](https://insiders.vscode.dev/redirect?url=vscode:mcp/install?%7B%22name%22%3A%22district%22%2C%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp-server.district.in%2Fv2%2Fmcp%22%7D)

<b>Manual installation</b>

Add this to your `mcp.json` file, start the server and sign in with District when asked.

```json
{
  "servers": {
    "district": {
      "type": "http",
      "url": "https://mcp-server.district.in/v2/mcp"
    }
  }
}
```

### Claude Code

Run this in your terminal, then run `/mcp` in Claude Code, pick `district` and sign in.

```bash
claude mcp add --transport http district https://mcp-server.district.in/v2/mcp
```

### Try it

Once connected, ask:

> "Find restaurants near me that are good for dinner."

## FAQ

**What is the District MCP server?**
It connects District to AI apps like Claude and ChatGPT. MCP (Model Context Protocol) is the open standard AI apps use to connect to tools. Once District is added, you can ask your assistant to find a movie, book a table or pay a bill on District.

**Do I need to log in?**
No. You can start as a guest and look around. To book, pay or see your bookings, log in with your mobile number and an OTP, either on the sign-in page or later from the chat.

**How do bookings and payments work?**
Before it books or pays, your assistant shows you what it's about to do and waits for your yes. You pay by scanning a UPI QR; cards, netbanking and wallets are in the District app. Cancellations go through only when your AI app asks you to confirm them; otherwise you cancel in the District app.

**How do I report a problem or share feedback?**
Use the feedback form at [studio.district.in/mcp](https://studio.district.in/mcp/#feedback) or write to [developers@district.in](mailto:developers@district.in). Include the prompt you used and what came back so we can look into it quickly.

## Disclaimer

- The connector is for personal use. We are not allowing third-party apps to be built on top of District MCP right now due to security and legal considerations. If you want District in your product, write to [developers@district.in](mailto:developers@district.in) and tell us what you're building.

- This is only for testing purposes and District disclaims any and all liabilities that may arise due to erroneous / non-functionality of the MCP integration.
