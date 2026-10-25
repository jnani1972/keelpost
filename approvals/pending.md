# Pending approvals

Items that need your decision. Agents add items to **Open**. You tick one box per item and, if you like, write a comment. Then ask the director to process approvals: it acts on your tick, moves the item to **Closed** and logs the decision.

- Only you tick boxes. Agents never tick, and never edit an item once you have commented.
- Items with `URGENT` in the title sit at the top of Open.
- `OVER LIMIT` in the title means the spend would pass a cap in `settings/spend-limits.md`. It cannot auto-ship even if you tick yes; the director asks you to raise the cap or cut the amount first.
- A tick of "no" with a comment tells the director whether to drop the job or brief it again.

## Item template (copy, do not tick)

```
### A-YYYYMMDD-NN | <short title, with URGENT or OVER LIMIT first if they apply>
- [ ] yes
- [ ] no
- On yes: <one line: what happens next>
- Waits because: <the rule, quoted from CLAUDE.md or settings/approvals.md>
- File: <work/... path, or ->
- Spend: <amount, currency and channel, or none>
- Asked by: <agent>, for <B-YYYYMMDD-NN or event command>
- Owner comment:
```

## Open

### A-20261026-01 | SAMPLE, delete me: reply to a 2-star review about a slow repair
- [ ] yes
- [ ] no
- On yes: the scheduler posts the reply in the review tool role, or writes it out as `[READY TO PASTE]`.
- Waits because: "any reply to a negative review or a complaint" (CLAUDE.md always-wait list)
- File: work/2026-10-26-reviews-slow-repair-reply.md
- Spend: none
- Asked by: reputation, for B-20261026-03
- Owner comment:

## Closed

<!-- The director moves decided items here, newest last, with the date decided added to the title line. -->
