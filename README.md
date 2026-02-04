# Laraplugins-skills
A laravel boost skill to allow third party Agents and ides to connect to laraplugins and use it's plugin search functionality.

## Requirements

This project is meant to go with Laravel boost and as such is a dev dependency.

## Installation

To install this package, run the following command:

```bash
composer require danielpetrica/laraplugins-skills --dev
```

This will add the package to your project's dependencies and install it.

## Usage

After installation, boost will expose the plugin skills.
Until boost can install the Mcp server configuration you can install the mcp server manually as such: the place where to install it depends on your agent or ide. you can look at the boost generated mcp.json file in your project to know whereto place the  laraplugins-package-search entry.

```json
{
    "mcpServers": {
        "laraplugins-package-search": {
            "type": "streamable-http",
            "url": "https://laraplugins.io/mcp/plugins",
            "note": "LaraPlugins.io MCP Plugin Server (Streamable HTTP). Add this URL in your MCP client to enable search and plugin details."
        }
    }
}
```
