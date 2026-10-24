# MCP In 26 Minutes (Model Context Protocol) — Session Notes

## Video

- **Title:** MCP In 26 Minutes (Model Context Protocol)
- **URL:** https://www.youtube.com/watch?v=kOhLoixrJXo
- **Channel:** Tina Huang
- **Published:** 2025-10-15
- **Length:** 26m 23s

This is the reference video for our internal MCP onboarding session. Please watch it before the live session on Tuesday.

## Key Concepts from the Video

- **What MCP is:** The Model Context Protocol is an open standard, originally from Anthropic, for connecting AI applications to external tools, data sources and services. It defines a universal interface so any MCP-compatible application can use any MCP-compatible tool without writing a custom integration for each one — the video frames it as "USB-C for AI".
- **The problem it solves:** Before MCP, every application had to hand-write bespoke integration code for every tool it wanted to reach, which does not scale and creates maintenance burden. MCP replaces the N×M integration problem with one standard connector per tool.
- **The three roles:** An **MCP host** is the AI application or agent runtime (for example Claude Desktop, Cursor or Windsurf); an **MCP client** lives inside the host and connects it to servers; an **MCP server** is the piece that exposes capabilities to the host.
- **The three server primitives:** MCP servers expose functionality as **tools** (functions the model can invoke, e.g. web search or sending email), **resources** (data the model can read, e.g. file contents or database records) and **prompt templates** (reusable, standardized prompts for common tasks).
- **The communication life cycle:** The host/client and server exchange JSON-RPC messages over a transport. The client first discovers what the server offers (tools, resources, prompts), then the model invokes tools and results flow back into the application's context. Transports include `stdio` for local servers and HTTP-based remote transports (SSE).
- **Using existing MCP servers:** You can configure off-the-shelf community servers — such as web search, file system or Google Sheets/Forms servers — directly in your client application (e.g. a `claude_desktop_config.json` entry) rather than building anything yourself.
- **Building your own MCP server:** The video walks through two routes — a no-code approach using automation tooling, and a code approach (e.g. a Python server using the MCP SDK) — including testing the server locally with the MCP Inspector before wiring it into a host.

## Quiz

Please complete the attendance knowledge check before the session:

- **Quiz form (respondent link):** https://docs.google.com/forms/d/e/1FAIpQLSfHjaAjrgHktqi6WArckympiy8GFGiSCg8WVMzVR_E5EZ22Sw/viewform

## Further Reading

- **MCP specification organization on GitHub:** https://github.com/modelcontextprotocol
- Video companion code (Google Sheets/Forms MCP server): https://github.com/hellotinah/MCP
- Anthropic MCP course (DeepLearning.AI): https://www.deeplearning.ai/short-courses/mcp-build-rich-context-ai-apps-with-anthropic/
