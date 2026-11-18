---
title: MCP
excerpt: 'MCP: Model Context Protocol'
hidden: false
---
The DigiTax Nigeria API Hub Model Context Protocol (MCP) server enables AI-powered code editors like Cursor and Windsurf, plus general-purpose tools like Claude Desktop, to interact directly with your DigiTax Nigeria API Hub API and documentation.

## What is MCP?

Model Context Protocol (MCP) is an open standard that allows AI applications to securely access external data sources and tools. The DigiTax Nigeria API Hub MCP server provides AI agents with:

* **Direct API access** to DigiTax Nigeria API Hub functionality
* **Documentation search** capabilities
* **Real-time data** from your DigiTax Nigeria API Hub account
* **Code generation** assistance for DigiTax Nigeria API Hub integrations

## DigiTax Nigeria API Hub MCP Server Setup

DigiTax Nigeria API Hub hosts a remote MCP server at `https://ng.docs.digitax.tech/mcp`. Configure your AI development tools to connect to this server. If your APIs require authentication, you can pass in headers via query parameters or however headers are configured in your MCP client.

<Tabs>
  <Tab title="Cursor">
    **Add to `~/.cursor/mcp.json`:**

    ```json
    {
      "mcpServers": {
        "dgtxng": {
          "url": "https://ng.docs.digitax.tech/mcp"
        }
      }
    }
    ```

    </Tab>
  <Tab title="Windsurf">
    **Add to `~/.codeium/windsurf/mcp_config.json`:**

    ```json
    {
      "mcpServers": {
        "dgtxng": {
          "url": "https://ng.docs.digitax.tech/mcp"
        }
      }
    }
    ```

  </Tab>
  <Tab title="Claude Desktop">
    Claude Desktop connects to remote MCP servers through the Connectors UI, not via `claude_desktop_config.json`.

    1. Open **Claude Desktop** and go to **Settings → Connectors**.
    2. Click **Add custom connector**.
    3. Enter a name (e.g. `DigiTax Nigeria`) and the URL:
       ```
       https://ng.docs.digitax.tech/mcp
       ```
    4. Save. To use it in a conversation, click **+** → **Add connectors** and enable **DigiTax Nigeria**.

  </Tab>
</Tabs>

## Testing Your MCP Setup

Once configured, you can test your MCP server connection:

1. **Open your AI editor** (Cursor, Windsurf, Claude Desktop, etc.)
2. **Start a new chat** with the AI assistant
3. **Ask about DigiTax Nigeria API Hub** - try questions like:
   * "How do I create an NRS e-invoice with DigiTax Nigeria?"
   * "Which party details are required before an invoice can be transmitted?"
   * "How do I issue a credit note against an existing invoice?"
   * "How do I get a callback when an invoice's status changes?"

The AI should now have access to your DigiTax Nigeria API Hub account data and documentation through the MCP server.

## Authentication

The DigiTax Nigeria MCP server reads live data from your account. Pass your API key as a request header:

```text
X-API-Key: <your-api-key>
```

See [API Prerequisites](ref:prerequisites-of-using-the-api) for how to obtain your key and configure it in your MCP client.
