make a long description [ read me ] so i can put it in my github repository ,long description showing how to use and mor e

I'll base this on the actual setup steps in your existing docs so the GitHub README is accurate rather than invented.

AstroX
AstroX turns a normal AI chat tab into a hands-on Roblox Studio agent. A small browser extension adds a control bar to your favourite chat site, a local bridge carries commands to Roblox Studio, Blender, Figma and Blockbench, and the desktop app gives you one place to watch, approve and rewind everything the agent does.

No API key, no terminal, no cloud service. What the agent sees and changes is under your control.

How it works
AI chat tab (ChatGPT, DeepSeek, Claude, Grok, Gemini, Kimi, Qwen, …)
        │  AstroX browser extension
        ▼
Local bridge  ──► Roblox Studio   (Studio MCP: scripts, Luau, instances)
        ├──────► Blender          (add-on or headless scene building)
        ├──────► Figma            (frame import / export, tokens, SVG)
        ├──────► Blockbench       (models and texture atlases)
        └──────► Electron app     (Live View, WorkBench, History, Workshop)
The extension lives inside the chat page. You type a request, the model answers with tool calls, and the bridge executes them against Studio on your machine. The app shows captures, tool results and status; nothing is uploaded to AstroX.

Features
An agent you can steer
Plan mode — the agent submits a numbered plan before it builds. Edit, reorder or drop steps, then hit Run. Each step executes with a progress row; a failure pauses the plan for edit-and-resume instead of guessing.
@-mentions — attach exactly the context you want: @skill:folk-stud-ui, @script:ShopServer, @selection, @checkpoint:before-shop, @frame. The bridge resolves them into a labelled block the agent receives as the first feedback of the task.
Change journal + real undo — every mutating Studio call is recorded with what it touched, old values and a ChangeHistoryService waypoint. The bar shows the live count; one click walks Studio's own Undo back over the whole task.
Checkpoints — snapshot a subtree before risky work, then restore it from History (insert or replace, behind a confirmation).
Failure recovery — retry a step, edit the plan, or restore a checkpoint; no silent partial success.
A real place to work
Live View — the Studio viewport, refreshed while the tab is open.
WorkBench — edit SKILL.md, references and scripts with a size meter, dead-reference validation, and Preview what the agent receives using the real loader.
Notes & vault — scratchpad, long-term context, and an optional Obsidian vault connection.
Workshop — a community surface for skills and plugins: one-click Share, one-click Install, import/export of portable packages, and an optional public registry URL for a live feed.
Studios & Engines — UI/model/animation tooling plus measured connection status for Studio, Blender, Figma and Blockbench.
48 themes, quiet motion, and full Motion Off / reduced-motion support.
Local by design
Name-only accounts. Create an account with a name, open it with one click. No password, no cloud login, no bundled API keys. Each account owns its own skills, memory, notes and appearance.
Requirements
Windows or macOS
Roblox Studio with built-in MCP support
Microsoft Edge or Chrome
Python 3.9+ (the app finds py, python or python3 and installs the one library it needs on first launch)
Quick start
Get the app. Download AstroX.exe from the Releases page. It contains the desktop app, the bridge, the extension and the bundled skills.
Install the extension. Open edge://extensions or chrome://extensions, enable Developer mode, click Load unpacked, and select the astrox-extension folder next to AstroX.exe.
Enable Studio MCP. Open Roblox Studio with a place loaded → Assistant AI → … → Manage MCP Servers → Enable Studio as MCP Server.
Open AstroX. Double-click AstroX.exe. Create an account with just a name; the bridge starts with the app.
Start a session. Open a supported chat (DeepSeek is recommended), start a new conversation, click Start session on the AstroX bar, and describe what you want to build.
A step-by-step video walkthrough is available at
youtu.be
.

Supported chats: DeepSeek, ChatGPT, Claude, Grok, Gemini, Kimi, GLM, Qwen, Arena (Direct mode only), Meta AI, Vani, Notion AI chat, MiMo AI and FeatherRBLX. The bar appears only on those sites.

Using the bar
Start session attaches AstroX to the current chat; the bar then shows bridge health and engine status.
Type normally. Tool calls appear as compact cards with the command name, arguments and output; click one for the full payload.
Plan mode turns the next build into an approval step. Research mode lets the agent look things up before acting.
Cowork queues follow-up prompts or splits work across provider tabs.
The journal chip and undo button appear when Studio changes are recorded; Stop halts the current task.
Tip: be specific about the place and the asset. @selection plus a named skill is worth more than a long prompt.

Skills and the Workshop
Skills are folders with a SKILL.md and references/scripts that the agent loads on demand. Six are bundled; WorkBench lets you inspect and edit them, and validate that every referenced path exists.

The Workshop can share packages with other people. It works locally out of the box — Share packages a skill into your profile, Import/Export moves portable JSON. To get a live public feed, run the included workshop_registry.py (stdlib-only JSON store) and paste its URL into Settings → Workshop → Public registry. The registry implements GET /index.json, GET /api/package/<id> and POST /api/publish; see WORKSHOP_REGISTRY.md.

No registry is bundled. Anyone with the registry URL can publish, so review plugins before installing — plugin packages can add a local MCP server command, and AstroX asks for confirmation first.

Troubleshooting
Bridge offline — open AstroX.exe; the bridge launches with it. Check the app's status pill for the real reason, not a guess.
Studio shows "Attached, no place open" — open a place; the tool catalogue is advertised even with Studio closed.
Engine card says not started — the bridge probes engines on demand; it does not launch Blender, Bun, Studio or Blockbench by itself.
Gemini / Kimi behave inconsistently — model behaviour, not the extension. Remind the model to use the commands or start a fresh chat.
Arena — keep the mode on Direct; other modes are blocked.
Community — https://discord.gg/NEbSJtdx69
Known limits
The portable exe is unsigned; Windows SmartScreen may warn on first run.
Automated fixtures do not certify live provider DOM changes or account state — authenticated sending should be checked on the providers you use.
Accounts are a local profile switch, not a secret: anyone with access to your computer can open any account.
Public registries are self-hosted and open by design.
License
AstroX is free to use and closed source. Copyright © 2026 AstroX. You may use it, including in commercial Roblox games, configure it and keep private backups of your own copy. You may not copy, publish, mirror, redistribute, fork, sell or build derivatives from it. Anything you build with AstroX is yours. Full terms in LICENSE.

