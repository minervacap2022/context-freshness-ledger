# Context Freshness Ledger

`Context Freshness Ledger` is a small, no-execution reference for deciding
whether remembered information is still suitable for a proposed next step.

It records five things that are easy to lose between an earlier session and a
later action:

1. **Source** — where the information came from.
2. **Observed time** — when it was last checked.
3. **Scope** — the work, person, or project it applies to.
4. **Proposed action** — the bounded step being considered.
5. **Review decision** — whether the context is current, stale, or needs a
   person to resolve it.

The JSON Schema in [`context-freshness-ledger.schema.json`](./context-freshness-ledger.schema.json)
is intentionally narrow. It does not access accounts, call tools, send
messages, infer permissions, or authorize an external action. It is a format
for a reviewable record, not a compliance or security certification.

## Example

```json
{
  "record_id": "vendor-quote-2026-08",
  "source": {
    "kind": "document",
    "reference": "approved-vendor-quote.pdf",
    "observed_at": "2026-08-20T09:30:00Z"
  },
  "scope": "procurement / packaging refresh",
  "proposed_action": "prepare a renewal draft",
  "freshness": {
    "review_by": "2026-08-27T09:30:00Z",
    "status": "stale",
    "reason": "The quote expired before the draft would be sent."
  },
  "human_return": {
    "required": true,
    "reason": "A current quote and an external commitment require review."
  }
}
```

## Related pre-launch direction

I work on Klik. It is a pre-launch, app-first, recorder-agnostic proactive-AI
direction for turning deliberate Sessions into useful Context and
permission-aware follow-through. New access, material judgment, and external
commitments stay with the person. This reference is an independent educational
format, not a product release, integration guarantee, benchmark, performance
claim, or statement that every source or recorder is supported.

Learn more: https://pre.hiklik.ai/?utm_source=github&utm_medium=developer_resource&utm_campaign=kickstarter_prelaunch&utm_content=context_freshness_ledger


<!-- minervacap-pre-hiklik-promotion -->
> **Discover Klik:** https://pre.hiklik.ai/
<!-- /minervacap-pre-hiklik-promotion -->
