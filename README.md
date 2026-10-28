# Direct Hotels

Find hotels anywhere and the link to book each one on its own website, with no
online travel agency in between. [Direct Hotels](https://www.direct-hotels.com)
is a free, non-commission directory of over 400,000 hotels in 230+ countries.
Each listing links to the hotel's own site, which the directory has fetched and
checked names the hotel. No hotel pays to be listed or ranked.

## What's in this plugin

- **The Direct Hotels MCP server** (`.mcp.json`): six tools, at
  `https://www.direct-hotels.com/api/mcp`. No account, key or sign-in.
  - `search_hotels`: hotels in a city, district or region, filterable by stars
    and amenities (pool, parking, pets, spa, …)
  - `get_hotel`: one hotel by name, id or page URL, with its rating, address,
    booking link and what its own website says, each fact with its source
  - `find_city`: covered cities matching a partial or other-language name
  - `check_coverage`: whether a place is covered, and the nearest covered
    cities when it isn't
  - `directory_info`: what the directory is and where coverage is thin
  - `suggest_hotel`: sends a hotel the directory is missing for review; it
    never edits a listing
- **A skill** (`skills/book-hotels-direct`): which tool to use for which
  question, how to read empty and filtered results, and how to cite sources.

## Install

In Claude, add it from the plugin directory. In Claude Code:

```
/plugin install direct-hotels --marketplace Nicositter88/direct-hotels-plugin
```

Or connect only the server, as a custom connector:
`https://www.direct-hotels.com/api/mcp`.

## Example prompts

- "Find me a boutique hotel in Marrakech I can book direct"
- "Pet-friendly hotels with a pool in Nice"
- "Tell me about Maison Proust in Paris. Does it have a spa?"
- "Any hotels in Pyongyang?"

## What it sends and stores

The plugin runs no local code. Tool calls go only to
`https://www.direct-hotels.com/api/mcp`. Direct Hotels logs the tool name, the
search term, the outcome and timing, never conversation content.
`suggest_hotel` stores the hotel name, city and website you send. See the
[privacy policy](https://www.direct-hotels.com/privacy).

The directory holds no prices, availability or bookings; those stay on each
hotel's website.

## Links

- Documentation: https://www.direct-hotels.com/mcp
- Support: hello@direct-hotels.com
- License: MIT
