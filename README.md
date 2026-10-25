# Chicago Cityscape API plugin for Claude Code

A Claude Code plugin that teaches Claude how to use the [Chicago Cityscape](https://www.chicagocityscape.com) APIs, with your API key, to research real estate in Chicago and Cook County: property reports, zoning rules, parcel boundaries, building permits, pending permits, financial incentives, and place boundaries such as wards and community areas.

Looking things up in claude.ai, the desktop app or Cowork? Use the **Chicago Cityscape** plugin instead. It adds the Chicago Cityscape connector, which needs no API key and works in every Claude app. Its source is [ChicagoCityscape/claude-code-skills](https://github.com/ChicagoCityscape/claude-code-skills).

## What's included

### Skill: [chicago-cityscape-api](skills/chicago-cityscape-api/SKILL.md)

Documents all ten public Chicago Cityscape API endpoints: Property Report, Zoning, Parcels, Places, Sources, Query, Zoning Explorer, Search, Incentives Dictionary, and Pending Permits. Before calling anything, Claude asks a few short questions about what you are researching, then picks the right endpoint.

**Triggers on**: questions about API access, API keys, API endpoints, querying property data programmatically, or integrating Chicago Cityscape data into an application. You can also invoke it directly with `/chicago-cityscape-api`.

## Requirements

- A Chicago Cityscape API key ([chicagocityscape.com/account.php?page=apikeys](https://chicagocityscape.com/account.php?page=apikeys)) and an environment with open internet access, such as Claude Code or a local terminal. The claude.ai web and desktop apps run tools behind a network allowlist that does not include chicagocityscape.com. There, Claude uses the skill as reference only; use the Chicago Cityscape plugin's connector for property lookups.

## What this plugin runs, sends, and fetches

- **Runs**: `curl` commands through the Bash tool, which Claude Code asks you to approve.
- **Sends**: requests only to `https://chicagocityscape.com` (and `www.chicagocityscape.com`). API requests carry your query parameters (an address, PIN, place, zoning class, or search term) and your Chicago Cityscape API key.
- **Where the key comes from**: the skill tells Claude never to ask you to paste the key into the chat. Claude reads it from the `CITYSCAPE_API_KEY` environment variable, from a `.env` file loaded inside the same command, or from the macOS Keychain (item `cityscape-api`), and never prints it. The key goes only to chicagocityscape.com, the service that issued it.
- **Stores**: nothing. The plugin has no hooks, MCP servers, or background processes, and saves no data outside the files you ask Claude to write.

See the [Chicago Cityscape privacy policy](https://help.chicagocityscape.com/privacypolicy) for how chicagocityscape.com handles API requests.

## Installation

In Claude Code, find **Chicago Cityscape API** in the plugin directory (`/plugin`) and add it.

To install from this repository in Claude Code instead:

```bash
git clone https://github.com/ChicagoCityscape/claude-code-api-skill.git
claude --plugin-dir ./claude-code-api-skill
```

## License

MIT. See [LICENSE](LICENSE).
