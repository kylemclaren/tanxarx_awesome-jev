# Awesome Jev [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of resources, open-source clones, integrations, and engineering playbooks for **Jev** — TypeSafe AI's non-generative "System 1" decision model.

Jev doesn't generate text. Given a prompt and a set of typed candidates (a choice, a score, a yes/no), it returns a calibrated probability over the candidates in a single forward pass — no sampling, no JSON parsing, no hallucinated options. Since its release, a fast-moving ecosystem of integrations, open-source reproductions, and "System 1 / System 2" agent-architecture patterns has grown up around it. This list tracks it.

Every link below was resolved from its original source tweet/thread and verified to be a live, matching repository at the time it was added — see [CONTRIBUTING.md](CONTRIBUTING.md) for how entries are checked.

## Contents

- [About Jev](#about-jev)
- [Open-Source Reproductions & Clones](#open-source-reproductions--clones)
- [Coding Agents & Dev Tools](#coding-agents--dev-tools)
- [Browser & Desktop Automation](#browser--desktop-automation)
- [Data & Retrieval](#data--retrieval)
- [Content, Media & Moderation](#content-media--moderation)
- [Simulation, Games & Hardware](#simulation-games--hardware)
- [Finance & Trading](#finance--trading)
- [Benchmarks & Evaluation](#benchmarks--evaluation)
- [Articles, Threads & Playbooks](#articles-threads--playbooks)
- [Contributing](#contributing)
- [License](#license)

## About Jev

- [typesafe.ai](https://typesafe.ai) - TypeSafe AI's homepage.
- [typesafe.ai/Jev](https://typesafe.ai/Jev) - Product page for Jev.
- [Launch announcement](https://x.com/CompleteSkeptic/status/2099925682726002904) - Diogo Almeida (co-inventor of RLHF and InstructGPT at OpenAI) introduces Jev: a "System 1" model claimed to be 20-200x faster and 40-400x cheaper than generative frontier models for decision-shaped tasks. 32K context window; no image/audio input; cannot write code or prose by design.
- [typesafe-ai/skills](https://github.com/typesafe-ai/skills) - Official agent skills for building with the System One API. Install via `npx skills add typesafe-ai/skills --skill typesafe-ai`, or as a Claude Code plugin with `claude plugin marketplace add typesafe-ai/skills`.

## Open-Source Reproductions & Clones

- [bespokelabsai/nimble](https://github.com/bespokelabsai/nimble) - "Bespoke Nimble": a 9B open reproduction on Qwen3.5, built in a day from 2,676 examples via LoRA. Trained with "contrastive data curation" (near-identical question pairs with one flipped fact) to teach evidence-reading over explanation-generation. Scored 90.12% vs. Jev's 93.21% on the team's own eval.
- [mizorewww/laya-mlx](https://github.com/mizorewww/laya-mlx) - Laya (an Apache-2.0 Jev alternative) ported to Apple Silicon via MLX: 60 decisions/sec at under 1GB RAM, demoed playing Snake from raw probability classification.
- [Heman10x-NGU/Verdict-open-jev](https://github.com/Heman10x-NGU/Verdict-open-jev) - "Verdict": a 151M-parameter ModernBERT + GLiClass head model returning calibrated probabilities and an explicit "insufficient evidence" outcome in one forward pass. Weights on [Hugging Face](https://huggingface.co/heman10x/rlcd-modernbert-151m).
- [jaredpalmer/kev](https://github.com/jaredpalmer/kev) - A tiny Jev-like model built on Qwen2.5-0.5B, trainable and runnable locally on a MacBook.
- [TianyuCodings/NanoJev](https://github.com/TianyuCodings/NanoJev) - Independent implementation: a Qwen3-0.6B parallel judgment model with public weights and training code.
- [ekzhang/openjev-sglang](https://github.com/ekzhang/openjev-sglang) - A Jev-compatible API endpoint built on open models via SGLang (prefill-only), for self-hosting on GPU servers.
- [TheoLeeCJ/SemIf](https://github.com/TheoLeeCJ/SemIf) - "Semantic ifs" from open models running on a single 3090 at home. Independent research, not affiliated with Jev/TypeSafe.
- [vinnylarouge/jevlike](https://github.com/vinnylarouge/jevlike) - Independent research evaluating mixed-length candidate sets as a Jev-style research baseline, not a drop-in clone.

## Coding Agents & Dev Tools

- [TheoOliveira/pi-jev](https://github.com/TheoOliveira/pi-jev) - Semantic tool routing for the Pi coding agent: before each step, Jev scores whether a tool is relevant and gates activation at a 0.65 probability threshold.
- [jkudish/jev-mcp](https://github.com/jkudish/jev-mcp) - Packages Jev's judgments as standard MCP tools (verify claims, rank candidates, screen content for prompt injection).
- [devagrawal09/jev-review](https://github.com/devagrawal09/jev-review) - A staged code-review workflow and local dashboard built on Jev.
- [devagrawal09/stanley-code](https://github.com/devagrawal09/stanley-code) *(originally `jev-code`)* - Bounded Jev-gated workflows for coding agents.
- [0xNatoshi/jev-codex-router](https://github.com/0xNatoshi/jev-codex-router) - Per-turn model and reasoning-depth routing for Codex, driven by Jev.
- [gargpratyush/jev-router](https://github.com/gargpratyush/jev-router) - Routes each Claude Code task to the cheapest sufficient model.
- [thruwire/foreman](https://github.com/thruwire/foreman) - A "software factory foreman" for Codex: Jev decides whether to continue, accept, or stop.
- [EliaAlberti/jev-rules](https://github.com/EliaAlberti/jev-rules) - Jev picks which of your rule files apply to the current prompt, so Claude only sees the relevant ones.
- [kitze/skillbox](https://github.com/kitze/skillbox) - Self-hosted, versioned Agent Skills library with optional Jev-driven recommendations for which skill to load per turn.
- [itsmostafa/typesafe-mcp](https://github.com/itsmostafa/typesafe-mcp) - An MCP connector giving any agent direct access to Jev.
- [DevMortimer/pi-warden](https://github.com/DevMortimer/pi-warden) - Guardrails for the Pi agent: Jev judges irreversible/off-task tool calls, detects stuck loops, and flags unverified "done" claims.
- [perixtar/jev-e2e](https://github.com/perixtar/jev-e2e) - Natural-language end-to-end web app tests, powered by Jev and Playwright.
- [davila7/claude-code-templates](https://github.com/davila7/claude-code-templates/tree/main/cli-tool/components/mods/productivity) - See the `jev-model-router` and `jev-skill-suggestion` mods: per-turn model/effort routing and skill selection for Claude Code, installable with `npx claude-code-templates@latest --mod productivity/jev-model-router`.
- [tlangridge/Alloy](https://github.com/tlangridge/Alloy) - A local, multi-model panel for Claude Code that uses Jev to route tasks by complexity, model strength, and remaining subscription quota.

## Browser & Desktop Automation

- [browser-use/jev-ultrafast](https://github.com/browser-use/jev-ultrafast) - Passes a typed DOM snapshot to Jev instead of a screenshot to a vision model; the heavy LLM only fires for actual text input. Completed a Zurich→London Google Flights search in 7.1s.
- [awlevin/typesafe-computer-use](https://github.com/awlevin/typesafe-computer-use) - macOS automation for about $0.0002/step: OCR the screen, classify the next action with Jev, click.
- [droidrun/mobile-jev](https://github.com/droidrun/mobile-jev) - Android automation on top of Mobilerun, driving real devices via CLI while watching screen state and logs.
- [moritzkremb/jev-voice-browser](https://github.com/moritzkremb/jev-voice-browser) - Voice-controlled browsing: Jev resolves intent and target element in ~300ms per spoken word, Playwright acts.
- [kitze/unclutter](https://github.com/kitze/unclutter) - A WXT browser extension that uses Jev to identify and hide ad banners/popups from the page.

## Data & Retrieval

- [realZachi/pg-jev](https://github.com/realZachi/pg-jev) - A PostgreSQL extension for filtering, classifying, and sorting rows with natural language — no vector DB required.
- [superagents-lab/jev-search](https://github.com/superagents-lab/jev-search) - Web search built on Jev for source selection, query understanding, and relevance ranking.
- [jexp/neo4jev](https://github.com/jexp/neo4jev) - Traverses a Neo4j graph by having Jev classify which neighboring relationship to follow next.

## Content, Media & Moderation

- [trungdq88/youtube-sponsor-detection](https://github.com/trungdq88/youtube-sponsor-detection) - Detects YouTube sponsor segments from live audio and transcript, powered by Jev.
- [ChetasLua/jevmeter](https://github.com/ChetasLua/jevmeter) - Scores every sentence of a video against a chosen angle and renders it as a scored highlight reel.
- [brainstormity/Jev-Moderation-Bot](https://github.com/brainstormity/Jev-Moderation-Bot) - Discord moderation for spam and phishing links.

## Simulation, Games & Hardware

- [fhshaik/typesafe-mario](https://github.com/fhshaik/typesafe-mario) - A Jev agent that plays Super Mario Bros. by reading structured emulator state instead of screenshots.
- [standardagents/jevpilot](https://github.com/standardagents/jevpilot) - A playable Three.js driving simulator with a Jev-powered autopilot.
- [RomanSlack/jev-drone](https://github.com/RomanSlack/jev-drone) - A camera-only autonomous drone in MuJoCo, using a small Jev judgment model in the loop at 2.5Hz.
- [AboveColin/HA-Jev](https://github.com/AboveColin/HA-Jev) - Home Assistant integration: typed Jev answers exposed as sensors, plus actions and a conversation agent for Assist.
- [lhemerly/mcts-agent](https://github.com/lhemerly/mcts-agent) - Discriminative Monte Carlo Tree Search: Gemini plans, Jev scores and prunes the tree in milliseconds.
- [trycua/cua](https://github.com/trycua/cua/tree/main/libs/cua-s1) - See `libs/cua-s1`: home of `cua-s1-form-v0`, a 706K-parameter, MIT-licensed specialist model that fills web forms from UI state in ~50ms.

## Finance & Trading

- [jarrodwatts/jev-trader](https://github.com/jarrodwatts/jev-trader) - Makes one AI trade decision per Monad block on Kuru MON-USDC; defaults to mock/dry-run without a configured private key.

## Benchmarks & Evaluation

- [iammrduncan/typesafe-ai-benchmark](https://github.com/iammrduncan/typesafe-ai-benchmark) - An LLM gateway that mimics TypeSafe's structured output contract, useful for benchmarking drop-in replacements against real Jev behavior.

## Articles, Threads & Playbooks

Not every valuable Jev post ships a repo. These threads carry the architectural ideas driving the ecosystem above:

- [Ronin — the "100x Upgrade" playbook](https://x.com/DeRonin_/status/2100917158922387537) - You don't get the 100x by swapping your LLM for Jev; you get it by finding the calls that never needed a language model in the first place and deleting them.
- [Milon — "Jev is not a smaller LLM"](https://x.com/milonspace/status/2101495990725566640) - Restricts Jev to exactly three gating jobs: is this done, which tool next, does a human need to see it — everything else still goes to a model that can write.
- [lifcc — System 1 / System 2 agent bifurcation](https://x.com/mylifcc/status/2101504368746848492) - Argues production agents need a strict split: Jev handles millisecond-level routing, the heavy LLM stays dormant until deep reasoning is actually required.
- [Alcides Ticlla — the cost/latency gap, quantified](https://x.com/AlcidesTicllaCh/status/2101465729929220490) - The same classification task: $0.013880 in 8.566s on an LLM vs. $0.000081 in 0.114s on Jev, verbatim from Jev's own numbers.
- [てる (@rute1203d) — four domain playbooks](https://x.com/rute1203d/status/2100783005229011415) - Concrete patterns for support-ticket triage, search-result relevance, tool selection, and agent-memory gating.
- [dani_avila7 — Jev Model Router for Claude Code](https://x.com/dani_avila7/status/2101176629745561686) - Announces the `jev-model-router` mod (see [davila7/claude-code-templates](https://github.com/davila7/claude-code-templates) above) with the reasoning behind locking the main model at session start to preserve prompt caching.

## Contributing

Contributions welcome! Please read the [contribution guidelines](CONTRIBUTING.md) first. In short: every entry needs a link that resolves to a real, live project that is actually about Jev — not just a name mentioned in a tweet.

## License

[![CC0](https://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, the maintainers have waived all copyright and related or neighboring rights to this work.
