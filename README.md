# Chicago Cityscape plugin for Claude

A Claude plugin for researching real estate with [Chicago Cityscape](https://www.chicagocityscape.com). It adds the Chicago Cityscape connector, so Claude can read Property Reports for any property in 13 counties in Illinois, Indiana and Wisconsin, and a skill that teaches Claude the Chicago Cityscape APIs: property reports, zoning rules, parcel boundaries, building permits, pending permits, financial incentives, and place boundaries such as wards and community areas.

## What's included

### Connector: Chicago Cityscape (MCP server)

A remote MCP server at `https://www.chicagocityscape.com/mcp`. You sign in once with your Chicago Cityscape account. Claude can then look up a property by address or PIN and read its Property Report (zoning, property class, taxes, permits, violations, sales, ownership, incentives and transit), compare up to 30 properties, list your My Faves and My Notes, and add a property to My Faves when you ask. It works in claude.ai, the desktop app, Cowork and Claude Code. How much of each report you see depends on your membership.

### Skill: chicago-cityscape-api

Documents all ten public Chicago Cityscape API endpoints: Property Report, Zoning, Parcels, Places, Sources, Query, Zoning Explorer, Search, Incentives Dictionary, and Pending Permits. Before calling anything, Claude asks a few short questions about what you are researching, then picks the right endpoint.

**Triggers on**: questions about API access, API keys, API endpoints, querying property data programmatically, or integrating Chicago Cityscape data into an application. You can also invoke it directly with `/chicago-cityscape-api`.

## Requirements

- **For the connector:** a Chicago Cityscape account. Sign up at [chicagocityscape.com](https://www.chicagocityscape.com).
- **For the API skill:** a Chicago Cityscape API key ([chicagocityscape.com/account.php?page=apikeys](https://chicagocityscape.com/account.php?page=apikeys)) and an environment with open internet access, such as Claude Code or a local terminal. The claude.ai web and desktop apps run tools behind a network allowlist that does not include chicagocityscape.com. There, Claude uses the connector for property lookups and the skill as reference only.

## What this plugin runs, sends, and fetches

- **Runs**: `curl` commands through the Bash tool, which Claude Code asks you to approve.
- **Sends**: requests only to `https://chicagocityscape.com` (and `www.chicagocityscape.com`). API requests carry your query parameters (an address, PIN, place, zoning class, or search term) and your Chicago Cityscape API key. Connector requests go to `https://www.chicagocityscape.com/mcp` with the tool's arguments (an address, PIN or county) and an OAuth token from your sign-in; the connector never sees your password or payment details.
- **Where the key comes from**: the skill tells Claude never to ask you to paste the key into the chat. Claude reads it from the `CITYSCAPE_API_KEY` environment variable, from a `.env` file loaded inside the same command, or from the macOS Keychain (item `cityscape-api`), and never prints it. The key goes only to chicagocityscape.com, the service that issued it.
- **Stores**: nothing locally. The plugin has no hooks or background processes, and saves no data outside the files you ask Claude to write. Its one MCP server is the remote Chicago Cityscape connector above; the only change it can make to your account is adding a property to My Faves when you ask. You can disconnect it at any time in Chicago Cityscape's My Account.

See the [Chicago Cityscape privacy policy](https://help.chicagocityscape.com/privacypolicy) for how chicagocityscape.com handles API requests.

## Installation

In Claude, find **Chicago Cityscape** in the plugin directory and add it.

To install from this repository in Claude Code instead:

```bash
git clone https://github.com/ChicagoCityscape/claude-code-skills.git
claude --plugin-dir ./claude-code-skills
```

## License

MIT. See [LICENSE](LICENSE).
