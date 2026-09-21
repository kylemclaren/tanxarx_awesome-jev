# Awesome Jev [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of resources, open-source clones, integrations, and engineering playbooks for **Jev** — TypeSafe AI's non-generative "System 1" decision model.

Jev doesn't generate text. Given a prompt and a set of typed candidates (a choice, a score, a yes/no), it returns a calibrated probability over the candidates in a single forward pass — no sampling, no JSON parsing, no hallucinated options. Since its release, a fast-moving ecosystem of integrations, open-source reproductions, and "System 1 / System 2" agent-architecture patterns has grown up around it. This list tracks it.

Every link below was resolved from its original source tweet/thread and verified to be a live, matching repository at the time it was added — see [CONTRIBUTING.md](CONTRIBUTING.md) for how entries are checked.

## Contents

- [About Jev](#about-jev)
- [Open-Source Reproductions & Clones](#open-source-reproductions--clones)
- [Coding Agents & Dev Tools](#coding-agents--dev-tools)
- [SDKs, Frameworks & Platform Integrations](#sdks-frameworks--platform-integrations)
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
- [typesafe.ai/blog/introducing-system-one-models-and-jev](https://typesafe.ai/blog/introducing-system-one-models-and-jev) - TypeSafe's own announcement post for System One models and Jev.
- [docs.typesafe.ai](https://docs.typesafe.ai/introduction) - Official API docs for the System One / Jev endpoint.

## Open-Source Reproductions & Clones

- [bespokelabsai/nimble](https://github.com/bespokelabsai/nimble) - "Bespoke Nimble": a 9B open reproduction on Qwen3.5, built in a day from 2,676 examples via LoRA. Trained with "contrastive data curation" (near-identical question pairs with one flipped fact) to teach evidence-reading over explanation-generation. Scored 90.12% vs. Jev's 93.21% on the team's own eval.
- [NandhaKishorM/laya](https://github.com/NandhaKishorM/laya) - Laya, the upstream Apache-2.0 Jev alternative: an RLCD-trained decision engine shipped as a PyPI package, later ported to Apple Silicon as laya-mlx below.
- [convaiinnovations/laya](https://huggingface.co/convaiinnovations/laya) - Laya's model weights on Hugging Face.
- [mizorewww/laya-mlx](https://github.com/mizorewww/laya-mlx) - Laya (an Apache-2.0 Jev alternative) ported to Apple Silicon via MLX: 60 decisions/sec at under 1GB RAM, demoed playing Snake from raw probability classification.
- [Heman10x-NGU/Verdict-open-jev](https://github.com/Heman10x-NGU/Verdict-open-jev) - "Verdict": a 151M-parameter ModernBERT + GLiClass head model returning calibrated probabilities and an explicit "insufficient evidence" outcome in one forward pass. Weights on [Hugging Face](https://huggingface.co/heman10x/rlcd-modernbert-151m).
- [Heman10x-NGU/openJev-verdict-2.0](https://github.com/Heman10x-NGU/openJev-verdict-2.0) - v1.4 inference-engine fixes for the 151M Verdict model (calibrator auto-loading, NLI-style candidate templating, a 512-token context cap) that raised its public JevBench score from 66.2 to 74.9, plus a newer "Verdict 2.0" architecture and an in-browser WebGPU engine.
- [jaredpalmer/kev](https://github.com/jaredpalmer/kev) - A tiny Jev-like model built on Qwen2.5-0.5B, trainable and runnable locally on a MacBook.
- [TianyuCodings/NanoJev](https://github.com/TianyuCodings/NanoJev) - Independent implementation: a Qwen3-0.6B parallel judgment model with public weights and training code.
- [logan-markewich/jeff](https://github.com/logan-markewich/jeff) - A self-hosted drop-in replacement for Jev, powered by GliFormer.
- [hr98w/jev-visual](https://github.com/hr98w/jev-visual) - An educational Jev-like visual-inference experiment on Apple Silicon, adding image input which Jev lacks.
- [ikermoel/open-alternative-jev](https://github.com/ikermoel/open-alternative-jev) - An open-source System-One-style decision layer over any open-weights LLM, benchmarked against Jev.
- [kshetrajna12/reflex](https://github.com/kshetrajna12/reflex) - A small open decision model on Qwen3.5 re-creating the Jev/System One API with vision input.
- [ekzhang/openjev-sglang](https://github.com/ekzhang/openjev-sglang) - A Jev-compatible API endpoint built on open models via SGLang (prefill-only), for self-hosting on GPU servers.
- [githubnext/localjev](https://github.com/githubnext/localjev) - A local Jev-compatible `/v1/systemone` bridge backed by DiffusionGemma.
- [TheoLeeCJ/SemIf](https://github.com/TheoLeeCJ/SemIf) - "Semantic ifs" from open models running on a single 3090 at home. Independent research, not affiliated with Jev/TypeSafe.
- [vinnylarouge/jevlike](https://github.com/vinnylarouge/jevlike) - Independent research evaluating mixed-length candidate sets as a Jev-style research baseline, not a drop-in clone.
- [sabeel111/OpenSourceJev](https://github.com/sabeel111/OpenSourceJev) - Independent research and experiments on small decision models, inference optimization, and parallel sampling in the Jev style.
- [vllm-project/vllm#57250](https://github.com/vllm-project/vllm/pull/57250) - A vLLM patch exposing Google's DiffusionGemma (26B MoE, 3.8B active) behind a Jev-compatible `/v1/systemone` endpoint, using parallel denoising instead of autoregressive generation and adding image input, which Jev lacks.

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
- [coldteadotai/abide](https://github.com/coldteadotai/abide) - Uses Jev to score every agent edit against project rules a linter can't express.
- [kbhuw/jev-sift](https://github.com/kbhuw/jev-sift) - Lets an agent use Jev to decide if a file, tool call, or page is worth reading before spending LLM tokens on it.
- [HexyeDEV/JevPR](https://github.com/HexyeDEV/JevPR) - An open-source GitHub PR review tool automated by Jev.
- [Braedennn/OpenJev](https://github.com/Braedennn/OpenJev) - A generic agent harness that routes every step through a Jev decision, pluggable with any LLM.
- [MagicBeansAI/jev-audit](https://github.com/MagicBeansAI/jev-audit) - Audits a codebase to find which existing LLM calls could be replaced by Jev.
- [kushals256/jevcache](https://github.com/kushals256/jevcache) - An OpenAI-compatible caching proxy that uses Jev to detect repeated same-intent requests and skip the billed call.
- [hqman/JevScout](https://github.com/hqman/JevScout) - A job-hunting skill: Jev finds a company's Careers pages and scores each role against a profile.
- [stas4000/jev-clerk](https://github.com/stas4000/jev-clerk) - A bookkeeping agent where Jev makes every step decision and a separate model periodically rewrites the playbook.
- [shantanugoel/ask-jev-skill](https://github.com/shantanugoel/ask-jev-skill) - A portable skill that lets any agent harness (demoed on Hermes) call Jev for a decision.
- [sutro-sh/jev-align](https://github.com/sutro-sh/jev-align) - An open-source CLI to calibrate Jev to custom decision criteria using GEPA.
- [caiovicentino/jev-align](https://github.com/caiovicentino/jev-align) - A separately built, differently-implemented calibrated alignment verifier for LLM responses/agent plans powered by Jev.
- [sumanmichael/jevlang](https://github.com/sumanmichael/jevlang) - A Python DSL for writing Jev-backed decision workflows as a natural-language "smart if".
- [vercel-labs/ai-cli](https://github.com/vercel-labs/ai-cli) - A terminal evaluation CLI defaulting to Jev, using its probability-weighted mean over an AI SDK schema.

## SDKs, Frameworks & Platform Integrations

- [danvega/jev-spring-boot-starter](https://github.com/danvega/jev-spring-boot-starter) - A Spring Boot 4 starter for Jev using RestClient and typed questions.
- [yusukebe/hono-jev-router](https://github.com/yusukebe/hono-jev-router) - Routes HTTP requests by meaning for the Hono framework, powered by Jev.
- [khmuhtadin/n8n-nodes-jev-classification](https://github.com/khmuhtadin/n8n-nodes-jev-classification) - An n8n community node for classifying and scoring text with Jev, with batching.
- [vercel-labs/jev-ai-sdk-form-router](https://github.com/vercel-labs/jev-ai-sdk-form-router) - Routes form submissions to the right destination using Jev and the Vercel AI SDK.
- [nandansrikrishna/jev-go](https://github.com/nandansrikrishna/jev-go) - A standalone Go CLI and MCP server for Jev with JSONL evaluation and resumable batches.

## Browser & Desktop Automation

- [browser-use/jev-ultrafast](https://github.com/browser-use/jev-ultrafast) - Passes a typed DOM snapshot to Jev instead of a screenshot to a vision model; the heavy LLM only fires for actual text input. Completed a Zurich→London Google Flights search in 7.1s.
- [awlevin/typesafe-computer-use](https://github.com/awlevin/typesafe-computer-use) - macOS automation for about $0.0002/step: OCR the screen, classify the next action with Jev, click.
- [droidrun/mobile-jev](https://github.com/droidrun/mobile-jev) - Android automation on top of Mobilerun, driving real devices via CLI while watching screen state and logs.
- [moritzkremb/jev-voice-browser](https://github.com/moritzkremb/jev-voice-browser) - Voice-controlled browsing: Jev resolves intent and target element in ~300ms per spoken word, Playwright acts.
- [kitze/unclutter](https://github.com/kitze/unclutter) - A WXT browser extension that uses Jev to identify and hide ad banners/popups from the page.
- [Sac-Y/Jev-cu](https://github.com/Sac-Y/Jev-cu) - A Codex skill where Jev picks the next UI action for computer use while a local policy gate blocks sensitive clicks.

## Data & Retrieval

- [realZachi/pg-jev](https://github.com/realZachi/pg-jev) - A PostgreSQL extension for filtering, classifying, and sorting rows with natural language — no vector DB required.
- [superagents-lab/jev-search](https://github.com/superagents-lab/jev-search) - Web search built on Jev for source selection, query understanding, and relevance ranking.
- [jexp/neo4jev](https://github.com/jexp/neo4jev) - Traverses a Neo4j graph by having Jev classify which neighboring relationship to follow next.
- [jerryjliu/docjev](https://github.com/jerryjliu/docjev) - OSS library that uses Jev plus LiteParse (and optional LlamaParse OCR) to classify documents and split multi-document packets by natural-language category rules; ~6x faster than GPT-5.6-luna at equivalent accuracy.
- [pinecone-io/using-typesafe-and-pinecone](https://github.com/pinecone-io/using-typesafe-and-pinecone) - Pinecone's reference integration reranking retrieved candidates against natural-language criteria with Jev instead of a long-context LLM call; ~5x faster and ~43x cheaper than Claude Opus 5 on the same 200-candidate rerank in their benchmark.
- [mgaitan/sqlite-jev](https://github.com/mgaitan/sqlite-jev) - A loadable SQLite extension and Python wrapper for asking Jev typed questions from SQL.

## Content, Media & Moderation

- [trungdq88/youtube-sponsor-detection](https://github.com/trungdq88/youtube-sponsor-detection) - Detects YouTube sponsor segments from live audio and transcript, powered by Jev.
- [ChetasLua/jevmeter](https://github.com/ChetasLua/jevmeter) - Scores every sentence of a video against a chosen angle and renders it as a scored highlight reel.
- [brainstormity/Jev-Moderation-Bot](https://github.com/brainstormity/Jev-Moderation-Bot) - Discord moderation for spam and phishing links.
- [gaborishka/jev-wrapped](https://github.com/gaborishka/jev-wrapped) - Judges a Telegram channel's year of posts with Jev and renders a "wrapped" summary card.
- [stas4000/jev-scroll](https://github.com/stas4000/jev-scroll) - A Chrome extension that labels every X/Twitter post with a Jev decision while scrolling.

## Simulation, Games & Hardware

- [fhshaik/typesafe-mario](https://github.com/fhshaik/typesafe-mario) - A Jev agent that plays Super Mario Bros. by reading structured emulator state instead of screenshots.
- [VBS2004/jev-plays-super-mario-bros](https://github.com/VBS2004/jev-plays-super-mario-bros) - A separate Jev-driven Mario agent, distinct implementation from the entry above.
- [standardagents/jevpilot](https://github.com/standardagents/jevpilot) - A playable Three.js driving simulator with a Jev-powered autopilot.
- [RomanSlack/jev-drone](https://github.com/RomanSlack/jev-drone) - A camera-only autonomous drone in MuJoCo, using a small Jev judgment model in the loop at 2.5Hz.
- [AboveColin/HA-Jev](https://github.com/AboveColin/HA-Jev) - Home Assistant integration: typed Jev answers exposed as sensors, plus actions and a conversation agent for Assist.
- [lhemerly/mcts-agent](https://github.com/lhemerly/mcts-agent) - Discriminative Monte Carlo Tree Search: Gemini plans, Jev scores and prunes the tree in milliseconds.
- [CPPAlien/playwithjev](https://github.com/CPPAlien/playwithjev) - A playable chess game against Jev with live typed inputs and probabilities.
- [trycua/cua](https://github.com/trycua/cua/tree/main/libs/cua-s1) - See `libs/cua-s1`: home of `cua-s1-form-v0`, a 706K-parameter, MIT-licensed specialist model that fills web forms from UI state in ~50ms.

## Finance & Trading

- [jarrodwatts/jev-trader](https://github.com/jarrodwatts/jev-trader) - Makes one AI trade decision per Monad block on Kuru MON-USDC; defaults to mock/dry-run without a configured private key.

## Benchmarks & Evaluation

- [iammrduncan/typesafe-ai-benchmark](https://github.com/iammrduncan/typesafe-ai-benchmark) - An LLM gateway that mimics TypeSafe's structured output contract, useful for benchmarking drop-in replacements against real Jev behavior.
- [goodrahstar/jev-column-race](https://github.com/goodrahstar/jev-column-race) - Races Jev against Gemini 3.8 Flash labelling 1,000 app reviews for sentiment/topic/bug/churn.
- [ickas/battleship-vs-jev](https://github.com/ickas/battleship-vs-jev) - A 228-test benchmark suite comparing Jev's decisions against scripted strategies at Battleship.

## Articles, Threads & Playbooks

Not every valuable Jev post ships a repo. These threads carry the architectural ideas driving the ecosystem above:

- [Ronin — the "100x Upgrade" playbook](https://x.com/DeRonin_/status/2100917158922387537) - You don't get the 100x by swapping your LLM for Jev; you get it by finding the calls that never needed a language model in the first place and deleting them.
- [Milon — "Jev is not a smaller LLM"](https://x.com/milonspace/status/2101495990725566640) - Restricts Jev to exactly three gating jobs: is this done, which tool next, does a human need to see it — everything else still goes to a model that can write.
- [lifcc — System 1 / System 2 agent bifurcation](https://x.com/mylifcc/status/2101504368746848492) - Argues production agents need a strict split: Jev handles millisecond-level routing, the heavy LLM stays dormant until deep reasoning is actually required.
- [Alcides Ticlla — the cost/latency gap, quantified](https://x.com/AlcidesTicllaCh/status/2101465729929220490) - The same classification task: $0.013880 in 8.566s on an LLM vs. $0.000081 in 0.114s on Jev, verbatim from Jev's own numbers.
- [てる (@rute1203d) — four domain playbooks](https://x.com/rute1203d/status/2100783005229011415) - Concrete patterns for support-ticket triage, search-result relevance, tool selection, and agent-memory gating.
- [dani_avila7 — Jev Model Router for Claude Code](https://x.com/dani_avila7/status/2101176629745561686) - Announces the `jev-model-router` mod (see [davila7/claude-code-templates](https://github.com/davila7/claude-code-templates) above) with the reasoning behind locking the main model at session start to preserve prompt caching.
- [sakevoid — Jev is judgment, not cognition](https://x.com/sakevoid/status/2101676640879190343) - A mental model for agent architecture: Claude/Codex handle cognition, Jev handles fast judgment calls, deterministic code enforces hard rules, and humans veto the irreversible ones.
- [me_barnyx — 5 rules before you wire Jev in](https://x.com/me_barnyx/status/2101630380067500350) - A practical checklist — separate deciding from generating, set confidence thresholds before shipping, log confidence against real outcomes, treat vendor benchmarks skeptically — illustrated via the fast-jev-compaction context-compaction pattern.
- [neural_avb — Jev isn't deterministic](https://x.com/neural_avb/status/2101736546391244854) - Shows identical prompts returning different output probabilities across repeated runs, and that reordering candidate choices measurably shifts them.
- [bourneshao — the fatal flaw in Jev](https://x.com/bourneshao/status/2101802361588945073) - Jev confidently returns wrong typed verdicts on multi-step arithmetic (summing invoice line items), arguing a typed answer still needs validation.
- [drummatick — does Jev really save the cost?](https://x.com/drummatick/status/2101714564404715872) - Benchmarks Jev against GPT-5 on the Banking77 intent-classification dataset: GPT-5 beats Jev by 3.2% accuracy at 32x the cost, plus a Jev+GPT-5 cascade test.
- [kcp_kn — Jev as an agent-eval judge](https://x.com/kcp_kn/status/2101506638288965918) - Reports on LangChain's Deep Agents experiment where Jev matched human pass/fail labels 100% across 500 trials with up to 913x lower quality-score variance than GPT-5.6 Terra, at roughly 1/80th the cost of Claude Sonnet 4.6.
- [reachmeviz — Laya vs. Jev, tested](https://viswakumar.com/blog/laya_system_one_model) - Hands-on comparison finding Laya's out-of-the-box zero-shot classification near-random despite matching Jev's published numbers on trained domains, concluding Jev's real moat is zero-training-overhead generalization.
- [NathanFlurry — "jev is just a really smart switch statement"](https://x.com/NathanFlurry/status/2100036101809619314) - A hype-free mental model: 2016-era ML classifiers with 2026-era intelligence, not a GPT/Claude replacement.
- [whereischarly — benchmark it against encoders, not LLMs](https://x.com/whereischarly/status/2100955287200907343) - Argues the fair comparison for Jev isn't frontier LLMs but boring open-weight encoder classifiers that have done zero marketing.
- [0xRicker — "Jev Engineering" as a control-system layer](https://x.com/0xRicker/status/2101705843200721203) - Frames state → decision → action → verification → next state as a distinct architectural layer most agent stacks are missing.
- [miu21590 — mid-task reasoning-effort routing](https://x.com/miu21590/status/2101857866378362926) - Uses Jev to change a coding model's reasoning effort during a run rather than picking a model up front, reporting 50% lower cost.

## Contributing

Contributions welcome! Please read the [contribution guidelines](CONTRIBUTING.md) first. In short: every entry needs a link that resolves to a real, live project that is actually about Jev — not just a name mentioned in a tweet.

## License

[![CC0](https://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, the maintainers have waived all copyright and related or neighboring rights to this work.
