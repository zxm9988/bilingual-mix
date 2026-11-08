# Bilingual Mix

Turn matching Mandarin or Japanese and English audio into one sentence-by-sentence listening track.

**[Try Bilingual Mix →](https://bilingualmix.com/en/)**

Bilingual Mix is a browser-based listening tool for language learners. Bring an audiobook, podcast or lesson in Mandarin or Japanese together with its English version. The tool aligns corresponding sentences, lets you choose language order and pauses, and exports a standard MP3 for listening on any device.

## Highlights

- Sentence-by-sentence bilingual listening
- Mandarin and Japanese learning workflows
- MP3 export
- No sign-up needed for the free trial
- Raw audio and transcripts are not stored by the service

## Remote MCP server

Bilingual Mix also runs as a remote [Model Context Protocol](https://modelcontextprotocol.io/) server, so AI agents can build alternating-language practice audio directly.

- Endpoint: `https://bilingualmix.com/mcp` (Streamable HTTP, stateless, protocol version `2025-06-18`)
- Landing page: [English](https://bilingualmix.com/en/mcp) · [中文](https://bilingualmix.com/zh/mcp) · [日本語](https://bilingualmix.com/ja/mcp)
- Machine-readable description: [`server.json`](server.json)

For MCP clients that accept remote HTTP servers:

```json
{
  "mcpServers": {
    "bilingual-mix": {
      "type": "streamable-http",
      "url": "https://bilingualmix.com/mcp"
    }
  }
}
```

Tools:

| Tool | What it does |
| --- | --- |
| `create_bilingual_audio` | Sentence pairs to one A→B alternating track, with a sentence timeline. `dry_run: true` quotes the cost without spending quota. |
| `align_audio` | Two audio URLs to transcribed, cross-language aligned sentence pairs with timestamps. |
| `translate_lines` | Fills in the other side when only one language's text is available (members). |
| `get_quota` | Sign-in state, minutes used and remaining, per-run limits. |
| `list_plans` | Plans and quotas. |

Anonymous calls get a free per-IP allowance (2 runs and 20 minutes a day, up to 10 minutes and 8 sentence pairs per run). When it runs out, the server replies `401` with a `WWW-Authenticate` resource metadata challenge; clients then sign in through OAuth 2.1 with PKCE (S256), including dynamic client registration, to use their account quota. Discovery documents are at `/.well-known/oauth-protected-resource` and `/.well-known/oauth-authorization-server`. A signed-in free account gets 4 runs and 40 minutes a day; a membership gets 500 minutes a month, up to 45 minutes and 30 sentence pairs per run.

## Learn more

- [English product page](https://bilingualmix.com/en/)
- [Chinese product page](https://bilingualmix.com/zh/)
- [Japanese product page](https://bilingualmix.com/ja/)
- [Japanese listening practice](https://bilingualmix.com/en/japanese)
- [Guides index](https://bilingualmix.com/en/guides/learn)
- [Comprehensible input guide](https://bilingualmix.com/en/guides/comprehensible-input)
- [How to make bilingual audio](https://bilingualmix.com/en/guides/make-bilingual-audio)
- [Chrome extension](https://bilingualmix.com/en/extension) ([Chrome Web Store](https://chromewebstore.google.com/detail/bilingual-mix-%E2%80%94-interleav/lhpmijmnjfjablpioilinpheggjdkfbp))
- [Pricing](https://bilingualmix.com/en/pricing)

<a href="https://boringcashcow.com/" target="_blank" rel="noopener"><img src="https://boringcashcow.com/img/badge/boringcashcow-badge-light.svg" alt="Bilingual Mix - Featured on BoringCashCow" width="200" height="54"></a>
