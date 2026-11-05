# Chicago Cityscape API plugin

A plugin that teaches Claude how the [Chicago Cityscape](https://www.chicagocityscape.com) APIs work, so it can help you write your own code against them for Chicago and Cook County real estate data: property reports, zoning rules, parcels, permits, and places.

Want Claude to look up properties for you? Use the **Chicago Cityscape** connector instead. It needs no API key and works in every Claude app.

## What's included

### Skill: [chicago-cityscape-api](skills/chicago-cityscape-api/SKILL.md)

Documents all ten public Chicago Cityscape API endpoints: Property Report, Zoning, Parcels, Places, Sources, Query, Zoning Explorer, Search, Incentives Dictionary, and Pending Permits. Before calling anything, Claude asks a few short questions about what you are researching, then picks the right endpoint.

**Triggers on**: questions about API access, API keys, API endpoints, querying property data programmatically, or integrating Chicago Cityscape data into an application. You can also invoke it directly with `/chicago-cityscape-api`.

## Requirements

- To run the API calls yourself, a Chicago Cityscape API key ([chicagocityscape.com/account.php?page=apikeys](https://chicagocityscape.com/account.php?page=apikeys)).

## What this plugin runs, sends, and fetches

- **Runs**: nothing. This skill is documentation. It has no scripts, hooks, or MCP servers.
- **Sends**: nothing. The examples use the placeholder `YOUR_KEY`, and the skill never reads an API key from your environment or files. You run any API calls yourself, with your own key, in your own code or terminal.
- **Stores**: nothing.

See the [Chicago Cityscape privacy policy](https://help.chicagocityscape.com/privacypolicy) for how chicagocityscape.com handles API requests.

## Installation

Find **Chicago Cityscape API** in the plugin directory and add it.

## License

MIT. See [LICENSE](LICENSE).
