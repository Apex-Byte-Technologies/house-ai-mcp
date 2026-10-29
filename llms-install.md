# Installing the House AI MCP server

House AI is a remote MCP server. There is nothing to download or build.

1. Add a remote server named `house-ai` with the Streamable HTTP transport and the URL `https://mcp.houseaiapp.com/mcp`. In Cline's `cline_mcp_settings.json`:

   ```json
   {
     "mcpServers": {
       "house-ai": {
         "type": "streamableHttp",
         "url": "https://mcp.houseaiapp.com/mcp"
       }
     }
   }
   ```

2. Check it works without signing in: call `search_design_styles` with `{"space": "interior", "query": "japandi"}`. It returns the Japandi style.

3. For design, shop, history and credit tools, the user signs in to their House AI account when the client asks (OAuth). If sign-in isn't possible, the user creates a personal API token at https://www.houseaiapp.com/app/connector and you add it as a header instead of using OAuth:

   ```json
   "headers": { "Authorization": "Bearer <token>" }
   ```

   Never ask the user to paste the token into the chat; put it only in the settings file.

Docs: https://www.houseaiapp.com/connector
