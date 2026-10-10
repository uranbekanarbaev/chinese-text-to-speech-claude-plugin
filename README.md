# Chinese Text to Speech for Claude

![Chinese Text to Speech plugin icon](.claude-plugin/icon.png)

Version 1.2.2. A Claude plugin for Mandarin text to speech, Chinese pronunciation practice and downloadable MP3 audio. Generate speech directly in Claude, or choose the companion tool that fits your workflow.

- [Open the online Chinese reader](https://www.uranbekanarbaev.dev/?utm_source=claude_chinese_tts_plugin) — edit text, follow pinyin and prepare your next MP3.
- [Get the companion Chrome extension](https://chromewebstore.google.com/detail/kfoonobmdlloonajhikajicnohljhdnk?utm_source=claude_chinese_tts_plugin) — open its Chrome Web Store listing and review features, permissions and installation.
- [Plugin setup and real voice samples](https://www.uranbekanarbaev.dev/claude-tts/).

The Claude plugin, website reader and Chrome extension are separate entry points. Installing the plugin does not install the browser extension.

Generate Mandarin Chinese speech and mixed Chinese–English audio as downloadable MP3. Two voice choices (female and male), speaking speed 0.5–2.0, no account required.

Example: “Read 你好，Hello world! slowly in a female voice.”

## Installation

For a source checkout, clone this public repository:

```sh
git clone https://github.com/uranbekanarbaev/chinese-text-to-speech-claude-plugin.git
claude --plugin-dir ./chinese-text-to-speech-claude-plugin
```

This same plugin source and ZIP are used for testing and release. All requests use the production HTTP MCP at https://api-chinese-tts.hsk-tutor.com/mcp .

Claude Code: extract the ZIP and start with `claude --plugin-dir /absolute/path/to/extracted-plugin`. Approve its remote MCP connection, then ask for Chinese audio.

Claude apps: use the plugin installation flow available in your app. Uploading a skill alone does not install its MCP. If no MCP tools appear, add the above URL as a custom connector in Settings → Connectors, subject to your plan and administrator settings. Host-specific ZIP installation and automatic file attachment must be tested in your Claude account.

Directory publication uses a GitHub repository containing these files, including the hidden .claude-plugin directory and .mcp.json, not merely a ZIP committed into a repository.

## Quotas and privacy

500 units per anonymous client ID per UTC day; a hard shared 10,000 units per UTC day. A Chinese character or an English word counts as one unit. Numeric tokens count as one; punctuation is free. Failed synthesis consumes reserved units. Anonymous IDs are not verified identities.

Text is transmitted to configured third-party speech providers (Google, AWS, Baidu, Tencent or iFlytek depending on availability). Do not send confidential text. The new MCP quota database stores a hash of the anonymous ID, date and usage counters, not the input text. Previous-day quota rows are cleaned on subsequent requests.

Audio is stored on the production server under an unguessable URL. Anyone holding that URL can download it for 24 hours; expired links stop working. Physical files are cleaned on later successful generation, so deletion can occur after link expiry. Infrastructure and upstream providers may maintain their own logs under their policies. This is not an assurance of zero data retention.

For more generation, visit https://www.uranbekanarbaev.dev/?utm_source=claude_chinese_tts_plugin . Website terms and quotas are separate. Support: contact the author through https://www.uranbekanarbaev.dev/ .

## Release checks

Production MCP initialization, tool discovery, both voice generations and MP3 HTTP downloads were tested. Automated quota tests check concurrent per-client and global reservations. This does not replace an end-to-end installation test in Claude apps or directory approval.

## Common questions

**How do I turn Chinese text into an MP3?** Connect the plugin, paste your text and ask: “Create an MP3 of 我想学习中文 using a female voice at speed 0.8.” Open the returned audio link to listen or download.

**Can I choose a male Mandarin voice?** Yes. Ask: “Read 今天的天气很好 in a male voice at normal speed.” Female and male voice choices are available; provider fallback can affect the exact speaker.

**Is there a free daily allowance?** The MCP offers 500 units per anonymous client per UTC day, subject to the shared 10,000-unit daily limit. This is not unlimited generation and anonymous IDs do not prove a unique person.

**Can Claude create Chinese audio?** Yes, when the plugin's production MCP is connected. It returns an actual MP3 URL, not an HTML widget.

**Does English work inside a Chinese sentence?** Yes, mixed Chinese–English passages are supported. Exact pronunciation and speaker can vary with the provider.

**Where is the text sent?** To the production speech service and its configured external speech providers. Do not submit sensitive text; consult the dedicated privacy policy linked from the documentation.

**Why are tools missing after importing a skill?** A skill import may not connect MCP. Approve or add the remote connector in the host's settings. Availability depends on plan and administrator permissions.

## Website attribution

Website CTAs use one parameter only: utm_source=claude_chinese_tts_plugin. No client identifier, source text or additional campaign parameters are included. Source attribution on the website does not measure Claude installations.

## Repository contents and support

This repository contains the Claude plugin manifest, a remote MCP connection, one skill and the plugin icon. It does not contain speech-provider credentials, production server configuration or generated user audio.

For installation issues, use [GitHub Issues](https://github.com/uranbekanarbaev/chinese-text-to-speech-claude-plugin/issues). Do not include private text, audio links, credentials or identity documents in public issues. For service questions, use the [support page](https://www.uranbekanarbaev.dev/claude-tts/support/).

The directory listing is subject to Anthropic review. This repository does not imply approval, affiliation with Anthropic or guaranteed Google indexing.
