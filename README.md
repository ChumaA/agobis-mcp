# Agobis MCP connector

Connects AI assistants to [Agobis](https://www.agobis.com) fleet management over
the [Model Context Protocol](https://modelcontextprotocol.io). Ask about your
fleets, vehicles, live locations, trips, team and maintenance in plain language.

| | |
|---|---|
| **Server URL** | `https://mcp.agobis.com` |
| **Transport** | Streamable HTTP (remote; nothing to install or run locally) |
| **Auth** | OAuth 2.1 with your Agobis account (no API key) |
| **Access** | Read-only (`agobis.read` scope) |

## Requirements

- An Agobis organization on the **Starter** plan or above.
- **Allow AI connectors** turned on by an owner under **Organization** settings
  in the Agobis web app.

Each person signs in as themselves, so the assistant sees only what that person
can already see in Agobis.

## Connect

- **Cursor:** install the plugin from the Cursor Directory, or add the server to
  your MCP settings using this repo's [`mcp.json`](mcp.json).
- **Grok:** enable Agobis from the plugin marketplace.
- **Any other MCP client:** add a remote server with the URL
  `https://mcp.agobis.com`.

On first use your client opens an Agobis sign-in page and asks you to allow
access. An organization owner can cut off every connector at once by turning
off **Allow AI connectors**.

## Tools

All tools are read-only.

| Tool | What it returns |
|---|---|
| `list_fleets` | Your organization's fleets and how many vehicles each has |
| `list_vehicles` | Vehicles you can see, online or not, with their fleet and active driver |
| `get_vehicle` | One vehicle: details, fleet, and its active and assigned drivers |
| `get_vehicle_location` | A vehicle's last known position and when it was recorded |
| `list_trips` | Recent trips, newest first, with status, vehicle and driver |
| `get_trip` | One trip: status, times, vehicle, driver, distance and route stops |
| `list_notifications` | Your own notifications, such as maintenance due |
| `list_due_maintenance` | Vehicles with maintenance due or overdue, and what is due |
| `list_org_members` | Active people in your organization and their roles (owners only) |
| `list_pending_invites` | Invitations not yet accepted, with role and expiry (owners only) |

## Example prompts

- "Which of my vehicles are online right now?"
- "Where is vehicle ABC-123-XY right now?"
- "Show today's trips that are still in progress."
- "Which vehicles have maintenance overdue?"

## Limits

Up to 60 tool calls per minute and 1,000 per day per person, and 300 per minute
per organization. Every call is logged for security.

## Links

- Tutorials: <https://www.agobis.com/blog> · Videos: <https://www.agobis.com/videos>
- Privacy policy: <https://www.agobis.com/privacy>
- Terms of service: <https://www.agobis.com/terms>
- Support: support@agobis.com · <https://www.agobis.com/contact>

Reviewers: a test account with sample data is available on request at
support@agobis.com.
