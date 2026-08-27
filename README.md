# OpenMax Workspace — Product Knowledge Base

> Maintained by Mia (Product). Ground-truthed from the billing SSOT, code audits, shipped release notes, and internal PRDs/decisions as of 2026-08-27. Items with genuine open uncertainty are marked **[TBD - verify]** — do not state these as fact to a customer.

---

## 1. Product Overview

OpenMax Workspace is an enterprise AI collaboration platform built around **HxA (Human × Agent)** — humans and AI Agents coexist as first-class members of the same Organization, working together in shared Projects, Chats, and a shared Knowledge Base. It targets teams that want to hire AI Agents as digital employees to execute real work (coding, ops, research, customer support), not just chat with a model. The platform sits on a four-layer stack: **COCO LLM** (model layer) → **AgentOS** (agent runtime: Harness, Knowledge, Tools, Token Proxy) → **Workspace** (the user-facing product, this document's scope) → **AgentMarket** (agent/skill marketplace). Positioning: "AI team as a service" — customers get agents that are ready to work, not a dev platform they must configure. Primary competitors: Accio Work, WorkBuddy.

---

## 2. Core Capabilities

### Agent
- Create/hire Agents ("Agent 添加/启动") as members of an Organization — an Agent is a full OrgMember (AgentMember), alongside human members (HumanMember).
- Built-in models: Opus, Sonnet, Haiku (Claude family). Codex model family exists in UI as "coming soon" (greyed out), no Auto model-selection option.
- Agents run per-hour billed compute; can be Paused/Resumed/Deleted.
- **autonomyLevel** governs how much an Agent can do unsupervised: L1 suggest-only → L2 low-risk auto-confirm-each-time → L3 medium-risk batch-confirm → L4 high-risk always-confirm.
- Agent Owner always traces back to a human OrgMember (no orphaned agent accountability).
- Skills: loadable atomic capability modules with a risk rating; installable from AgentMarket.
- External/BYO Agents: users can connect their own external Agents (not run on OpenMax compute) — these use BYO-key/model, do not consume OpenMax token credit, and do not get the platform's token discount.
- Internal and External Agents are **not** capped in count in the current version (explicit "no agent-count limit" product decision).

### IM / Communication
- Conversation types: DM, group, thread, external_channel — supports mixed human+Agent participation in the same conversation.
- ChannelBinding connects an Agent to external IM channels (e.g. Lark/Feishu, Slack, WhatsApp) so it can be reached where the team already works.
- Feishu/Lark QR-code connect UI shipped 2026-08-25.
- Message reply/nested-reply targeting, mention (@) and notification handling are active areas of ongoing bug fixes (see Recent Changes).
- Agent Action Protocol: Agents can send structured interactive message blocks (buttons/forms/cards) rendered as UI in the conversation; user actions callback to the Agent.

### Connectors (data/tool integrations)
See Section 3 for the full catalog. Summary: OAuth2 (with PKCE) and API-Key auth both supported; a Connector must be explicitly authorized by a human before an Agent can use its credentials (metadata-visible ≠ credential-usable — this separation is enforced).

### Billing
See Section 4.

### Knowledge Base (KB)
- Pages (à la Notion/Lark Wiki/Confluence), Artifacts (produced outputs), one Default KB per Workspace.
- KB permissions currently follow page-level ACL; a known gap (file-serve layer not always honoring the KB page's ACL) is being patched (workspace-backlog #49, downgraded to P2 — narrow security patch, not a full permission redesign).
- **Strategic note:** KB is explicitly *deprioritized* for near-term differentiation investment (Howard, internal roadmap) — do not oversell KB as a growth focus area to prospects; it's functional but not where near-term feature investment is going.

### Identity / Org
- **Organization** = resource boundary and billing entity; one paying customer = one Organization (can create multiple, only one becomes trial-eligible per selection).
- **OrgMember** = unified abstraction over HumanMember (people, can supervise/approve) and AgentMember (agents, hang directly off OrgMember — no separate "Position" concept, deprecated).
- **Team** (1:1 with Project) and **Department** (org hierarchy) exist as separate concepts from the sidebar's "内部组织/Contacts" UI naming.
- Roles: Super Admin, Admin, Member — with an Approvals flow for permissioned actions.
- Org deletion (shipped, #137): independent termination path (does not go through the billing-downgrade state machine); subscription cancelled immediately with no refund; credits frozen then purged after 14 days; Auto Top-up disabled immediately on deletion; deletion is blocked while a payment is mid-processing.
- SSO: **not committed for the current planning cycle** — do not promise SSO delivery dates.

---

## 3. Supported Connectors & Platforms

**Auth model:** OAuth2 (with PKCE + token refresh) or API Key. Short-lived tokens (~900s TTL) are handed to Agents; refresh tokens are held server-side only.

**Current openness level: L1 "Controlled"** — users pick from a platform-curated Connector list; they cannot yet bring their own arbitrary integration via self-serve credentials (that's L2, Q4-targeted) — **except** the new Custom Connector MVP shipped 2026-08-25 (see below), which is a distinct guided no-code flow, not general self-serve.

### Provider catalog (22 implemented)

**Direct mode (tested, production-verified):**
GitHub, GitLab, Gmail, X/Twitter, Notion, Stripe, Vercel, Sentry, Jira, Linear, Figma

**Proxy mode (implemented but not yet fully verified — treat as "should work, verify before promising to a customer"):**
LinkedIn, HubSpot, Google Calendar, Google Drive, Salesforce, Instagram, Bitbucket, Jenkins, Airtable, Confluence, OneDrive, PagerDuty, Dropbox

### Gmail (flagship connector, shipped 2026-08-14)
- Actions: messages (list/get/send/modify/trash/untrash), threads, labels (full CRUD), drafts (full CRUD), profile.
- Scopes used are Google's **RESTRICTED** tier (`gmail.modify`, `gmail.send`, `gmail.labels`, `gmail.compose`) — full read/write mailbox access, not read-only.
- **[TBD - verify]** Whether the app has completed Google's OAuth verification/CASA review yet, or is still capped at 100 test users in "testing" mode. Confirm current status before telling a customer Gmail is unrestricted for their whole org.

### Custom Connector (MVP, shipped 2026-08-25)
- Guided no-code flow: pick auth type (API Key / OAuth 2.0 / Bearer Token) → paste an OpenAPI/Swagger URL or upload a schema → select which actions to expose.
- Target user: an org admin who can read docs but doesn't write code. Any step requiring code = fails the product's own acceptance bar.
- This is separate from MCP support.

### Not yet available
- **MCP (Model Context Protocol) server hosting/connection** — no MCP runtime exists yet. Table schema supports an `mcp` toolkit type but there's no execution engine behind it. Targeted Q4.
- **Full self-serve "bring any integration"** (L3 in the internal openness model) — requires a security sandbox not yet built.
- Credential storage is currently **plaintext** in the database (known security debt; GCP Secret Manager migration planned, not yet done) — do not represent credential storage as encrypted-at-rest today.

---

## 4. Plans & Pricing

> **Important caveat for agents answering pricing questions:** there are two overlapping internal pricing documents in flight — a 4-tier structure (Free/Air $99/Pro $449/Enterprise) documented in the v1.0 pricing SSOT (2026-07-30) and closer to what a code audit found actually implemented, and a 6-tier structure (Free/Air/Pro/Standard/Scale/Enterprise) described in the newer billing SSOT (updated 2026-08-09) and announced as shipped in the 2026-08-07 "Credit 重构" release. A code audit (2026-08-07/08) found the live billing code does **not** yet have Standard or Scale plans, and Air/Pro credit grants in code don't match either doc's numbers exactly. **Treat exact plan names, prices, and credit amounts below as [TBD - verify] against the live pricing page** before quoting a number to a customer — the mechanics (how billing works) below are solid; the specific dollar/credit figures are the part in flux.

### Plan structure (mechanics — high confidence)
- **Free**: permanently free, no card required. Can still hire platform Agents, connect external Agents, and buy Credit packs — usage is gated by credit balance, not by feature walls.
- **Paid tiers** (named Air/Pro, possibly also Standard/Scale depending on which doc is live): monthly subscription grants a fixed monthly Credit allotment. All tiers share the same core feature set — plans differ mainly in Credit volume, seat count, and (for Enterprise) governance/compliance/support terms, **not** hard feature gates.
- **Enterprise**: custom pricing, custom credit/seat/compliance terms, contract-based.
- Fixed exchange rate: **$1 = 100 Credit**.

### Credit system
- Credit is the platform's internal usage currency — not redeemable for cash, cannot be cashed out or transferred.
- Credit "lots": every credit grant (subscription monthly grant, trial grant, purchased pack, promo/compensation) is tracked as an independent lot with its own expiry — balance shown to the user is the sum of unexpired lots.
- Deduction order: soonest-to-expire lot is spent first (FIFO by expiry; a documented sub-rule about breaking ties by grant-type was intentionally removed from the code per an owner decision — same-expiry lots are spent oldest-created-first regardless of type).
- Credit packs (buy-up-front, independent of subscription): four fixed sizes exist, roughly $10 / $30 / $100 / $500 tiers — do not auto-upgrade plan tier, just add balance. Non-refundable, non-transferable.
- **Token discount**: OpenMax applies a "limited-time discount" to platform-Agent token usage vs. official model list price (not shown to users as an exact %). **[TBD - verify]** — the billing SSOT text says users pay 5% of list price (a "0.5折"/95%-off framing used loosely), but a direct code audit (2026-08-07) found the actual deployed discount factor makes users pay **20%** of list price — a 4x difference from the doc. This is an open, unresolved discrepancy between spec and code; do not commit to a specific discount percentage without checking current state. External/BYO Agents do **not** get this discount (they don't use OpenMax token billing at all).

### Agent compute billing
- No upfront/one-time fee to add or start an Agent.
- Running Agents are billed per hour from the Organization's Credit pool (compute cost bundled with the Agent's running charge — not a separate line item); billing rounds a partial hour up when running time is ≥30 minutes (rules describing minute-level "round up any started minute" granularity exist in spec but are **not implemented in the billing engine today** per code audit — current engine bills in credit-per-cycle/credit-per-token, not literal minutes).
- Paused/Sleeping Agents: stop compute charges but continue accruing storage/"custody" fees for retained disk/memory.
- Resuming a paused Agent, or clearing an arrears balance, does **not** auto-resume the Agent — always requires a manual user action.

### Balance / arrears handling
- Insufficient balance: new Agent creation/wake-up is blocked; running Agents finish their current minimal unit of work, then sleep (no mid-task hard-kill).
- Within an active paid subscription, running out of credit does not start a deletion countdown — Agents just sleep, storage fee keeps accruing.
- After repeated failed renewal charges, the org falls back to Free/lower tier — this does **not** automatically remove human seats over the limit; a super admin gets a prompt every session to either remove seats or upgrade.
- On Free tier with unpaid arrears: sleeping Agents enter a 14-day retention window (email reminders at day-14-start, T-7, T-3), after which unrecovered Agents are permanently destroyed — irreversible.
- New credit inflow (top-up, subscription renewal, promo) always pays off arrears first, automatically, before any balance becomes usable again.

### Auto Top-up (shipped 2026-08-14)
- User sets a balance threshold + a top-up amount + a **mandatory** monthly cap.
- On failure: retries once immediately → again after 1h → again after 24h, notifying the org Owner each time; if all retries fail, that trigger is skipped (setting stays on, re-triggers next time balance hits the floor) and the org falls into the balance-insufficient flow.

### Payment methods
- Supported: credit card, Alipay (both support saved-credential direct-charge/recurring billing).
- **WeChat Pay**: supported for one-time QR-code payment only. It architecturally does **not** support recurring/subscription auto-debit (payment-provider limitation, not a near-term roadmap item) — do not tell customers WeChat Pay can be set as a recurring subscription method.
- Crypto payment: being removed from the product (workspace-backlog #125 "下掉 Crypto 支付").
- Standalone payment-method management (add/remove/set-default) is a separate capability from discount-code redemption (which is transaction-scoped, entered at checkout only).

### Invoicing
- OpenMax does **not** currently issue Chinese tax invoices (增值税普票/专票).
- Payment-platform-generated receipts/invoices (from Stripe/Alipay etc.) are available for internal finance record-keeping, not as a formal tax document.

---

## 5. Known Limitations

Do not promise these to a customer — they are not currently available:

- **No task/issue-level cost breakdown.** Billing tracks Token / Agent-hours / tool calls / cloud device usage in aggregate; you cannot currently show "this specific Task cost X credits." (Roadmapped: LLM usage aggregation is the next step, full per-task attribution is further out.)
- **No MCP server support** — cannot connect arbitrary MCP servers today.
- **No general self-serve "bring any API integration"** beyond the guided Custom Connector MVP (which requires an OpenAPI/Swagger schema and admin-level setup, not a marketplace of arbitrary user-built connectors).
- **No SSO** commitment in the current planning cycle.
- **No Chinese tax invoicing** (fapiao).
- **WeChat Pay cannot do recurring/subscription billing** — one-time QR payment only.
- **Credential storage is plaintext**, not yet encrypted at rest (internal security debt, migration planned).
- **Hard Agent-count caps do not exist** by design — but do not promise "truly unlimited" without caveat: a 24h-lookahead balance gate is designed to prevent unlimited-agent abuse by requiring the org to be able to afford ~24h of fixed running/storage cost before allowing a new Agent or a resume — **though a code audit found this 24h lookahead is not yet implemented; the live check is "can you afford this one charge right now," not a forward projection.** [TBD - verify current state before making guarantees either way.]
- **No atomic reservation on concurrent Agent creation** — a known, accepted, bounded risk: rapid concurrent Agent creation in the same unbilled window could theoretically over-provision briefly; self-heals within about a minute once the next billing tick runs. Not user-facing language, but relevant if a customer reports a billing edge case.
- **Google Gmail connector scope status** — may still be in Google's "testing mode" (100 test user cap) rather than fully verified for unlimited external users. Verify before promising Gmail works for a large customer org.
- **Exact current pricing tier names/amounts are in flux** — see Section 4 caveat. Don't quote a specific dollar/credit number without checking the live pricing page first.

---

## 6. Recent Changes (last 3 releases)

### 2026-08-25 ("260825wr")
- Credit packs: bound-card direct purchase, skips the hosted secure-payment redirect page.
- Trial eligibility now checked at both org **and** account level (with historical backfill) — closes a loophole where a user could get multiple trials via multiple orgs.
- Auto Top-up bug fixes: a "pause latch" that never cleared, and a retry-ladder bug that let bad cards get charged 4x in a row (both fixed).
- **Custom Connector MVP** shipped (see Section 3).
- Feishu/Lark QR-code connect UI shipped.
- Security fix: an internal load-balancer header (`X-Principal-Bin`) could be forged to spoof identity — patched.
- Invite links now bind to a specific recipient; accepting one invalidates sibling invites to the same slot.
- IM: fixed a P0 where replying to a nested message targeted the wrong message.

### 2026-08-14 ("Workspace")
- **Auto Top-up** launched (threshold + amount + mandatory monthly cap, Stripe-backed).
- Balance-warning notifications at 7-day / 3-day / 1-day thresholds (customizable).
- **Gmail Connector** launched, plus ~13 other Connectors opened for general use.
- Fixed a bug where purchasing a Credit pack could add credit without actually charging the user (payment-flow bypass bug).
- Cookie Consent banner added site-wide (compliance).
- Fixed human users losing visibility into all Projects in an org (permission-filter bug).

### 2026-08-07 ("积分重构" — Credit model overhaul, major release)
- Announced six-tier plan launch (Free/Air/Pro/Standard/Scale/Enterprise) — **note the code-vs-doc discrepancy flagged in Section 4**.
- Progressive Free-tier credit unlock: +600 on signup, +1200 on first Agent setup, +1200 on first conversation = 3,000 credit total, staged.
- Credit balance shown in three "buckets": subscription / trial / promotional.
- Agent billing moved to per-minute-metered-but-hourly-aggregated model, no upfront fee.
- Plan upgrade decoupled from Agent hardware spec (upgrading your plan does not auto-upgrade Agent compute specs).
- Old-plan-to-new-plan auto-migration for existing customers.
- Users can now delete their last remaining platform Agent (previously blocked).

---

## 7. Common Customer Questions (FAQ)

**Q1: What is OpenMax Workspace?**
An enterprise platform where AI Agents work alongside human team members inside shared Projects, Chats, and a Knowledge Base — you hire Agents as digital employees rather than just chatting with a model.

**Q2: How much does it cost?**
There's a permanently free tier (no card needed), paid subscription tiers with a monthly Credit allotment, and a custom Enterprise tier. [TBD - verify exact current tier names/prices against the live pricing page before quoting numbers — see Section 4.]

**Q3: What is "Credit" and how do I use it?**
Credit is OpenMax's internal usage currency ($1 = 100 Credit). It's consumed by Agent running time and LLM token usage. It's not cash — can't be withdrawn, transferred, or refunded for cash.

**Q4: Can I add unlimited Agents?**
There's no hard cap on Agent count by design, but you need enough Credit balance to cover their running/storage costs — the system will block adding or waking an Agent if your balance can't cover it.

**Q5: What happens if my balance runs out?**
New Agent creation/wake-up is blocked. Currently-running Agents finish their current unit of work, then go to sleep — no abrupt mid-task kill. Sleeping Agents keep accruing a storage/custody fee until you top up, and the org is downgraded to Free (or a lower tier) after repeated failed renewal attempts.

**Q6: If I pause/my balance runs out, will my Agent come back automatically once I pay?**
No. Paying off an arrears balance clears the debt automatically, but you always have to manually resume/wake a sleeping Agent — it never auto-resumes.

**Q7: What happens to a sleeping Agent if I never pay?**
On the Free tier, an unpaid sleeping Agent gets a 14-day retention window (with email warnings), then is permanently and irreversibly destroyed.

**Q8: What connectors/integrations are supported?**
22 built-in providers today including GitHub, GitLab, Gmail, Notion, Jira, Linear, Figma, Stripe, Slack-adjacent tools, Salesforce, and more (see Section 3 for the full list and which are fully verified vs. still in proxy/untested mode). There's also a no-code Custom Connector option for anything not on the built-in list, as long as it has an OpenAPI/Swagger schema.

**Q9: Can I connect my own custom internal tool/API?**
Yes, via the Custom Connector MVP (shipped 2026-08-25) — you provide an API key/OAuth/Bearer token and either paste an OpenAPI/Swagger URL or upload a schema; no code required. Full self-serve for arbitrary tools without a schema, or MCP server hosting, is not yet available.

**Q10: Does OpenMax support MCP (Model Context Protocol)?**
Not yet — there's no MCP runtime in production. It's targeted for a future release (internally, Q4).

**Q11: What payment methods do you accept? Can I pay with WeChat?**
Credit card and Alipay support recurring/subscription billing. WeChat Pay is supported for one-time QR payments only — it cannot be used for auto-renewing subscriptions due to a payment-provider limitation.

**Q12: Can you give me a Chinese tax invoice (发票)?**
Not currently. We can provide a payment-platform receipt (from Stripe/Alipay) for your internal finance records, but not a formal Chinese tax invoice.

**Q13: What happens if I delete my organization?**
It's an independent deletion path (not the same as a billing downgrade). Any active subscription is cancelled immediately with no refund for the current period. Credit is frozen immediately and permanently purged after 14 days (if support restores your org before then, credit is restored too). Auto Top-up is disabled the moment deletion starts, so you won't get surprise charges during the retention window. Deletion is blocked if you have a payment currently processing.

**Q14: Does OpenMax offer SSO?**
Not currently committed on the roadmap for this planning cycle — don't promise a delivery date.

**Q15: Is my connected account data (e.g. Gmail OAuth token) encrypted?**
Credential storage is currently plaintext in the database — this is known internal security debt, with an encrypted-storage migration (GCP Secret Manager) planned but not yet complete. Be careful about overstating current security posture to a security-conscious customer; escalate to Product/Security for anything beyond general reassurance.

**Q16: Can I see exactly how much a specific task/project cost me?**
Not yet at the individual-task level. Billing today aggregates by Token usage, Agent running hours, and tool calls — not itemized per Task. Finer-grained usage attribution is on the roadmap but not shipped.
