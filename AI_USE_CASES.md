# AI Use Cases (2026) — Wedding Concierge

## Agentic upgrade
Multi-channel orchestration:
- **Web chat** — Claude Sonnet 4.6
- **WhatsApp / SMS** — Twilio MCP → same Claude agent
- **Voice** — Whisper STT → Claude → TTS (Kokoro)
- **Seating optimiser** — constraint-solver (Z3 or OR-Tools) + Claude for the conflict-aware narrative
- **Menu personaliser** — Gemini multimodal (parse menu PDF + match allergens)
- **Payments** — Stripe MCP for deposits

## Stack (free/OSS)
- **LLMs:** Claude Sonnet, Gemini 2.x (multimodal menu), Grok (second-opinion)
- **ASR/TTS:** Whisper, Kokoro
- **Constraint solver:** OR-Tools (Apache 2.0), Z3 (MIT)
- **MCP:** Twilio, Stripe, Calendar
- **Eval:** Promptfoo on seating constraint satisfaction

## Prompt (seating optimiser)
```
Constraints: {dietary}, {family_conflicts}, {accessibility}.
Tables: {tables_with_capacity}.
Return JSON: [{table, guests:[names], constraint_cited}].
Prove each placement cites at least one constraint. Refuse to invent constraints.
```

## Limitations
Twilio / Stripe need accounts and webhooks. Voice channel needs a server.
