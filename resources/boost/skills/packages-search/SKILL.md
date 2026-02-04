---
name: package-search-laraplugins
description: Use when searching for plugins or packages. Allows using a mcp server to search for healthy to use plugins. 
---
## Package Search on Laraplugins

This package provides instructions on how to use the Laraplugins mcp server to search and verify Laravel packages and plugins for health status before adding them to  a project.
The server exposses the health data for the plugin too so that agent can choose halthy packages for te project or ask user which package to coose. 

### Tools available

- Plugins search: search Packages for Laravel with advanced filters.
- Plugin details: Inspect plugins detail including plugin health status.

### Mcp server
The mcp server can be configured as follows. 
The server exposes an streamable-http mco server at https://laraplugins.io/mcp/plugins

## Prerequisites
Install the mcp server for using this server. 

{
    "mcpServers": {
        "default-server": {
            "type": "streamable-http",
            "url": "https://laraplugins.io/mcp/plugins",
            "note": "LaraPlugins.io MCP Plugin Server (Streamable HTTP). Add this URL in your MCP client to enable search and plugin details."
        }
    }
}
