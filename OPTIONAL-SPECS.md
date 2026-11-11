# Optional specs

Pick any of these, in any order, once the main path is done or alongside it. Each line says what it is and how you'll know it works.

**Ready as full guides, with checks,** in the store kit's `optional/` folder: 14 and 15. Check one with `make spec S=<n>` in `~/code/store`. The rest are ideas for now; ask your tutor to build a course around one when you want it.

1. **Session cleanup.** Expired sessions are deleted on a schedule.
   - *Works when:* orders survive the cleanup, and carts don't.
2. **Order history.** A visitor can list their past orders, and so can their agent.
   - *Works when:* each visitor sees only their own orders.
3. **Stock holds.** A cart reserves its stock for 15 minutes. It's a harder race: expiring holds against checkouts.
   - *Works when:* no unit is ever both held and sold.
4. **Discount codes with a limit.** A code that can be used 10 times.
   - *Works when:* under many simultaneous checkouts, it's never used an 11th time.
5. **Cancelling an order.** Stock is restored in one transaction.
   - *Works when:* cancelling twice is safe, and stock is restored once.
6. **Admin keys.** Admin routes and tools need a key, so a customer's agent can't reach them even if it's set up wrong.
   - *Works when:* every admin action without the key is refused.
7. **A log of who did what.** Every change records who made it: a page, an agent, or a script.
   - *Works when:* you can read back everything an agent did.
8. **A load test.** 100 buyers and 10 units.
   - *Works when:* exactly 10 orders are placed, every time.
9. **Search.** Filter by category and price range. How does a tool's design change when the agent has to search?
   - *Works when:* your evals score at least as well as before.
10. **Your own agent loop.** You use the Claude Agent SDK instead of Claude Code.
    - *Needs:* an API key, and it costs money.
11. **Order fulfilment as a workflow,** with Temporal.
    - *Works when:* a fulfilment survives a restart halfway through.
12. **A cloud deploy.** You run your container on AWS ECS Fargate.
    - *Needs:* an AWS account, and it costs money.
13. **A race-runner subagent.** A subagent runs the race test and its control, and reports back in three lines.
    - *Works when:* you can say what it saw that your main session didn't, and the other way round.
14. **Your own migration runner** (ready: `optional/14-your-own-migration-runner.md`). A `migrate.py` that records which migrations have run, with a checksum for each, and refuses to run when an applied file was edited afterwards. It's the classic way of keeping a database's schema in step with its code.
    - *Works when:* new files apply once, in order; an edited old file stops it with a clear message; two runs at once can't both apply the same file.
15. **Errors the browser can read** (ready: `optional/15-errors-the-browser-can-read.md`). When your API answers with a 500, the browser can't read its body, because the error handler sits outside the CORS layer. Move it inside, so every error reaches the page as its message.
    - *Works when:* a 500 from your API shows its one-line message on the page, not a blank network error.
