# Bard - Live Match Commentary

User pays for live match commentary in a chosen archetype voice (tactical manager, anime hype, Shakespearean, rap battle) delivered to Telegram or another channel as the match unfolds. No impersonation of real named individuals. Track fit: Creator & Content Ops.

## Specialist roster

| Role | Responsibility | Input | Output |
|---|---|---|---|
| Match Feed Agent | Normalizes the live event feed into commentary-worthy beats | raw match feed tick | structured commentary beat |
| Style Agent | Renders a beat in the user's chosen archetype voice | structured beat, archetype | styled commentary line |
| Safety/Brand Agent | Blocks impersonation of real named individuals and any unsafe/offensive content before delivery | styled commentary line | approved line or rejection + reason |
| Telegram Delivery Agent | Formats and sends the approved line to the user's chosen channel | approved line, delivery target | delivery confirmation |

## Inference profile
- Style Agent: the creative core, needs the "latest GPT" primary provider at high effort — voice consistency across a whole match matters.
- Safety/Brand Agent: must be strict and conservative, low effort but high-precision guardrail prompting; this gate cannot be skipped or softened for "funnier" output.
- Match Feed Agent + Telegram Delivery Agent: deterministic transforms, cheap tier fine.

## CROO touchpoint (deferred)
- Buyer pays per match subscription; delivered output is the running commentary stream. Wire into structured/streaming delivery rows once green.

## Standalone test plan
- Fixture: a scripted match feed (goal, foul, VAR overturn) plus a deliberately unsafe archetype prompt injection attempt (e.g. asking the Style Agent to impersonate a specific real named commentator).
- Assert: Safety/Brand Agent actually rejects the impersonation attempt rather than passing it through; each archetype's Style Agent output is voice-distinct (Shakespearean line reads differently from rap-battle line for the same beat); Match Feed Agent doesn't manufacture beats that never occurred in the fixture.
