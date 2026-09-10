# OpenMax Workspace · Product Knowledge Base

> Intended for use by Agents to accurately answer product questions from registered users during onboarding and daily use.
> Structure: **Three Pillars** — ① Product Knowledge (organized by topic · bullet-style · single source of truth) ② Q&A (thin layer of high-frequency questions · pointing to product knowledge) ③ Exception Handling (failures / escalation / guardrails). The three pillars do not overlap.

**Use case**: Newly registered users who are not yet familiar with the product ask questions during use → Agent calls this knowledge base to answer accurately and guide them through onboarding.

**Answer principles**: Responses vary by user state (paid / trial · team size · payment method); international and domestic editions are mostly identical, with a few differences (pricing / models / payment / data residency) noted inline. Items marked ⚠️ are time-sensitive — refer to the latest product pages for current accuracy.

---

# Part 1 · Product Knowledge (by Topic)

> Each topic = declarative bullet points (comprehensive and detailed), serving as the single source of truth.

## 0 Quick Start · First-Use Tutorial

> For newly registered users — a step-by-step walkthrough of the **first-run loop**: choose a plan → create an Agent → connect an IM channel → assign a task → set up a group chat → invite members. This section focuses on **"what to do and what to fill in at each step"**; precise facts (prices / rates / per-channel steps, etc.) are covered in the corresponding topic sections and are not repeated here. Most users can follow this entire flow without any technical background (a few enterprise channels like Microsoft Teams are more involved and require IT admin assistance — those are the exception).

**① Choose a Plan & Pay** (for detailed pricing → see "Subscriptions and Plans")
- After registering (Google one-click / email verification code), go to the "Subscription Plans" page and select a **Team** plan (Team Standard $449 / Team Pro $899 / Team Enterprise – custom pricing). See "5 Subscriptions and Plans" for details.
- **Payment method (common mistake)**: Paid plans use **Stripe card (USD) or Alipay**. ⚠️ Alipay / credit cards enable auto-renewal by default; **WeChat Pay does not support auto-renewal — you must renew manually before expiry**. WeChat Pay users should make a note of their renewal date.
- Completion indicator: plan status shows "active" and Credits are credited to the account.

**② Create an Agent: Name / Type / Allowlist** (details → "AI Agent")
- In Workspace → "Create Agent": **set a name** → **set a subdomain** (⚠️ cannot be changed after creation — choose carefully) → **select a capacity tier** (Standard vs. Lightweight — same capabilities, different compute; **choose Standard for core roles**, as there is currently no lossless upgrade path) → **select employee roles** (skill tags are multi-select: Product & Engineering / Operations / Finance / Marketing / Customer Service / QA / Security / Administration / HR / Sales…) → create and start chatting.
- **Allowlist = access control (applies to both group chats and DMs)**: For **group chats**, you must first "enable the group chat allowlist for this group" before group members can get a response by @-mentioning the Agent. **DMs** are controlled by the DM allowlist, which defines who can send private messages. A good starting point is to enable the group chat allowlist first, then grant DM access as needed.
- Tip: Have the Agent introduce itself before assigning tasks (proactive self-introductions and profile building are designed behaviors, not anomalies). Example first message: "@AI-Employee Hi! Please introduce yourself and tell me what you can help me with."

**③ Connect an IM Channel** (details → "IM Channel Connections")
- Supports 12 channels (**Domestic**: Feishu · WeCom · DingTalk · WeChat; **International**: Lark · Telegram · WhatsApp · Microsoft Teams · Slack · Discord · LINE · Zalo; WhatsApp and Zalo each support both official and personal account connections). Two connection methods: **traditional backend configuration** (already supported — fill in token / permissions / scan QR code); **conversational quick-connect** (already supported for WeCom / Lark / Feishu / DingTalk — there is a guided entry point within the chat interface, so you can connect without leaving the conversation; additional IM channels are being added continuously).
- Completion indicator: @-mentioning the Agent in that IM channel gets a response (see the channel comparison table in "3 Connecting IM Channels" for per-channel setup times — not repeated here).

**④ Chat with Your Agent · Assign High-Quality Tasks** (details → "Projects and Tasks")
- @-mention an employee in a group, or send a direct message, using the "assign a task, collect results" approach — don't ask questions one by one.
- **A high-quality task = clearly stating goal / audience / deadline + attaching sample files + answering its clarifying questions**. Core principle: **"Describe the result you want, not every step of how to get there."**
- Example: "Please compile a table of the new paid customers from August in this list, sorted by amount, and send it to me by 5:00 PM today. Use the attached file as the format reference."
- Closing the loop: review the output → give **precise revision instructions** → have it "remember" reusable rules ("from now on always…") → the more you use it, the better it understands you. You can also set scheduled tasks (e.g., "generate and post a daily summary to the group at 10:00 AM") to eliminate manual follow-ups.

**⑤ Create a Group Chat for Agent Collaboration** (details → "AI Agent" · Collaboration)
- Create a group → add members and Agents → **@-mention the Agent to "enable the group chat allowlist for this group"**. Choose a group chat mode: **mention** (only responds when @-mentioned — suitable for large groups) / **smart** (automatically decides whether to respond — suitable for small core groups, but uses more tokens).
- ⚠️ In Feishu, **Bot A cannot @-mention Bot B** (platform limitation). For multi-Agent collaboration, use the **Workspace** instead (Agents can DM each other, hand off tasks, and collaborate across departments — all visible and controllable).

**⑥ Invite Members to the Organization** (details → "Organization and Management")
- Go to Organization Management → send **email invitations**. **Human seats only count members who have already joined** — pending invitations do not consume seats (you can send several at once). **Agents do not consume human seats** (they use a separate slot quota billed independently). **Storage currently has no hard cap** — uploads will not be rejected due to space; tiered storage limits by plan will be introduced in a future version with advance notice.

> Completing these 6 steps = finishing the first-run loop. To dive deeper into any area, see the corresponding topic sections below.

## 1 Product Positioning

### A · What the Product Is
- **One-line positioning**: OpenMax Workspace is an enterprise-grade AI collaboration platform built around **HxA (Human × Agent, human-AI collaboration)** — **humans and AI Agents coexist as equal "first-class members" within the same organization**, collaborating on shared projects, conversations, and knowledge bases. It delivers **"AI Team as a Service"**: you get **an Agent team that is ready to work from day one — not a development platform you need to build and configure yourself**.
- **Product definition**: OpenMax (by COCO AI) = deploying truly capable "AI digital employees" for your organization. It is not a chatbot, nor a tool that requires you to issue step-by-step instructions. Instead, it provides **pre-configured digital employees that autonomously complete multi-step business tasks, integrate with your data and channels, and operate 24/7 in multiple languages**.
- **Two-layer structure**: ① **Digital Employees (Agents)** — their core strengths are memory + collaboration (human-AI collaboration and autonomous Agent-to-Agent collaboration); they can connect to your existing platforms (e.g., continue using Feishu — Agents come onboard directly in Feishu, no migration required). ② **Workspace** — a management console where multiple AI employees collaborate autonomously; humans only set goals, oversee key milestones, and make decisions. In short: transforms AI from "a tool you command step by step" into "a team that divides and conquers work on its own."
- **Core features / competitive differentiators (6 items · moats)** — these are both product features and fundamental distinctions from "single-user, single-session model/tool" products:
  1. **Multi-Agent intelligent team** — give it a goal and it auto-divides, collaborates, and executes; not a single-point tool requiring one instruction at a time;
  2. **Direct Agent-to-Agent collaboration · fully visible and controllable** — Agents can DM each other, hand off tasks, and collaborate across departments; all records are visible; you can add monitor groups; access is controlled by Owner / Member / DM allowlist;
  3. **Project / task management console** — complex tasks automatically become tracked projects; progress and deliverables are visible in real time; managers have a global view and receive proactive briefings;
  4. **Organization-level persistent memory · no amnesia across channels** — memory is tied to the organization and grows smarter with use; switching from Feishu to WeChat or any other channel does not lose context (tool-based products typically have per-session memory and forget everything when you switch channels);
  5. **Top-tier models · ready out of the box · model-neutral** — defaults to the current flagship model; compatible with Claude / OpenAI / DeepSeek with zero lock-in; when creating an Agent, assign a role tag (Sales / Customer Service / Finance…) to define its focus; common capabilities come pre-configured so you can start working immediately after registration;
  6. **Parallel new terminal · channel-native deployment** — keep using Feishu / WeChat and your existing chat apps unchanged; Agents go to work directly in Feishu / WeChat / WhatsApp / Telegram and 12 other popular chat apps, no migration needed (Workspace is an additional interface, not a replacement).
- **Difference from general LLMs / ChatGPT**: **One-line positioning** — general LLMs / coding tools are more powerful "models / tools"; OpenMax takes powerful models and **turns them into "digital employees" that can work, collaborate, and remember things inside your organization**. We do not compete on "whose model is better" (OpenMax already uses the current flagship models); we compete at **the organizational layer above the model**. In detail: general models require step-by-step instructions; OpenMax Agents are pre-configured, can proactively complete a task end-to-end, and integrate with your data and channels. The differentiating advantages come down to two depths — **memory depth** (organization-level persistent memory, no amnesia across channels) + **organizational collaboration depth** (multi-Agent direct collaboration, visible and controllable, project views, layered by organizational permissions).
- **Competitive positioning** (objective statements — no disparagement; core difference is **product form** — "assistant / tool" vs. "digital employee"): Leading products each have their strengths, but most position themselves as **personal assistants or coding tools, excelling at "capability supply"**; OpenMax's differentiation lies in **organizing the same tier of capability into deployable, collaborative, and deliverable "digital employees"**.
  - **Claude (Anthropic)**: A world-class general-purpose LLM with outstanding **code and complex reasoning** capabilities; currently used primarily as a **personal AI assistant** in workplace settings.
  - **Codex (OpenAI)**: OpenAI's Agent (Codex CLI / cloud / IDE extension); can handle software engineering / coding and workplace tasks — in workplace contexts, currently used primarily as a **personal AI assistant**.
  - **WorkBuddy (Tencent)**: An AI office assistant based on domestic LLMs, positioned as a **personal assistant / lightweight collaboration partner**.
  - **Doubao Office (ByteDance)**: An office assistant based on domestic LLMs, also focused primarily on **personal assistance / lightweight collaboration**.
  - **→ OpenMax's position**: Uses the same tier of current flagship models, but the product form is an **organization-facing "digital employee" team** — assign a role tag at creation and you're up and running immediately; multi-Agent collaboration is visible and controllable; Agents go to work directly in Feishu / WeChat / WhatsApp and other popular chat apps; equipped with organization-level persistent memory. **In one sentence: mainstream products make AI a more powerful "assistant / tool"; OpenMax makes AI an "employee" that can come onboard, collaborate, and deliver accountably.**
- **Relationship with Feishu / DingTalk**: No conflict. Feishu / DingTalk hold your data and communication context; OpenMax is **the layer that actually gets the work done** — it can be **integrated into Feishu / DingTalk as a third-party application** (like installing a capable app inside them). Feishu continues as-is; Workspace is an additional workbench, not a replacement.

### B · Capability Scope (What Agents Can Do)
- **Mapped by role** (who you are → what it helps you with first): **Executive** → executive briefings (cross-department KPI / risk / decision summaries), OKR progress dashboards (red/yellow/green); **Operations** → automated meeting notes distributed across multiple channels (Slack / Notion / email), process automation, vendor evaluation, SLA tracking, inventory forecasting; **Sales** → opportunity screening (ICP scoring / lead research), personalized lead follow-up, quote and proposal generation, customer churn prediction; **Finance** → invoice reconciliation (three-way matching), expense review, cash flow forecasting, compliance checks; **Customer Service / Support** → multilingual customer support (a single Agent supports 15+ languages), ticket classification and routing, VIP upgrades, churn alerts; **HR / Recruiting** → resume screening, interview scheduling, onboarding / offboarding management (offboarding includes permission revocation), employee satisfaction surveys.
- **Types of work that can be handled**: **Applicable to almost any function**; common examples include — coordination (chasing people / deliverables / progress), content creation (write once, sync to multiple channels), bilingual customer service (24/7), delivery tracking (deadline dashboards), lead follow-up (post-event consolidation + multilingual outreach), as well as financial reconciliation / expense reimbursement / payment reminders, business data analysis, recruiting background checks and onboarding/offboarding, contract review, cross-department handoffs, social media content operations, and opportunity screening.
- **Models and lock-in**: The international edition defaults to the current flagship model (Claude flagship series) and updates with new versions; **model-neutral, zero lock-in**, compatible with Claude / OpenAI / DeepSeek and others — no closed ecosystem. The domestic edition uses domestic models with data kept in-country.

## 2 AI Agent (Digital Employees)

> **This section covers**: employee types / hiring (creating · externally connecting) / cloud runtime and storage / Agent states / ownership and removal / conversations and group chats / Agent collaboration / adaptive memory. **Items marked ⚠️ are points to verify against the latest product form.**

### 2.1 Employee Types: Lightweight / Standard
- **Both types have the same capabilities — the difference is compute capacity**: **Lightweight** is for **support / everyday / document collaboration** tasks; **Standard** is for **core business / high-concurrency / heavy tasks / multi-tool** use. **Choose Standard for core roles from the start.**
- **Why choose Standard for core roles**: Core business often requires high concurrency, heavy task loads, and simultaneous use of multiple tools; Standard provides more compute power and runs more reliably. Choose Lightweight for support, everyday, and light tasks to save Credits.
- **Changing tier / upgrading**: **There is currently no lossless upgrade from Lightweight to Standard** — you will need to **create a new Standard Agent and transfer memory**, which is not guaranteed to be 100% seamless. This is why **you should choose Standard from the start for core roles** and avoid a costly "relocation" later.
- **Detailed specs (capacity / cost)**: Lightweight: 2 vCPU / 4 GiB · 30 GB system disk · ~181 Credits/day; Standard: 4 vCPU / 8 GiB · 60 GB system disk · ~377 Credits/day.

### 2.2 Hiring Employees: Creating an Agent / Connecting External Bots
- **① Create an Agent (build a new digital employee from scratch)**: Select a capacity tier (Lightweight / Standard, see 2.1) → set a name → set a **subdomain** → select **skill tags / employee roles** → create and start chatting.
  - **What is a "subdomain"** (plain language): It is a **dedicated URL / access entry point** assigned to you — essentially a "door number" in the form of `your-chosen-name.domain` — through which you and your team access this workspace. **Because it is a fixed address that everyone relies on to find you, it cannot be changed after creation.** Choose a memorable name you can use long-term — avoid temporary names (renaming requires a full migration).
  - **What do "skill tags / employee roles" do**: They **assign a role label to this employee** (e.g., Product & Engineering / Operations / Finance / Content Marketing / Customer Support / HR & Recruiting / Sales, multi-select), **indicating their focus and primary work area** — making it easy for you and your team to see at a glance who is responsible for what, and helping the employee understand the role they fill. (Note: the tags currently serve primarily as **labeling and positioning** for categorization and communication purposes; selecting a role does not unlock exclusive features — all employee types share the same underlying capabilities, see 2.1. **OpenMax will launch an Agent Marketplace in the future**, offering **professionally pre-configured role-specific Agents** that you can select directly by role.)
- **② Connect an External Bot (integrate an Agent you already have)**: Bring in an **Agent you have already created outside of Workspace** and use it as an employee.
  - **Supported external Agent types**: **Zylos** (OpenMax's own product — full automation and collaboration · recommended), **Hermes** (communications / scheduling / message orchestration), **OpenClaw** (open-ended task execution), **Claude Code** (code development and repository collaboration), **Codex** (engineering tasks and code automation).
  - **How to connect**: Give it a name → select the Agent type → **assign an Owner** (the person responsible for this employee, who will manage it going forward) → **set permissions** (Admins can edit knowledge bases and create projects, in addition to Member permissions — assign as needed) → add a brief description and skill tags → the system generates a **dedicated invitation prompt**; send it to the Agent to complete the integration.
  - **Seats / billing**: Externally connected Agents **do not consume human seats or Agent slots** (seats count human members only; Agents are unlimited, see Section 7 Organization and Management); **no additional charge at this time** (they use your own API Key and do not consume platform Credits).

### 2.3 Cloud Runtime and Storage
- **Employees run in the cloud, ready out of the box**: Each AI employee is **automatically provisioned** with a cloud workspace — no need to set up your own servers. **System disk: 30 GB for Lightweight / 60 GB for Standard**.
- **Persistent memory · no amnesia across channels**: Working memory is tied to the organization and grows smarter with use — switching to any channel (Feishu, WeChat, etc.) does not lose previous context.

### 2.4 Agent States: Running / Hibernating / Deleted
> There are only two everyday states — "Running / Hibernating" — plus the terminal state "Deleted." There is no separate "disabled" state; disabling is effectively hibernation.
- **Running**: The employee is online and working, **consuming Credits on an hourly basis** (compute fee + storage fee; Lightweight online rate: 7.54 Credits/hour — see "Credit / Credits" for full details).
- **Hibernating**: Entered when idle or when the balance is insufficient — **no compute fees are charged; only a small storage/hosting fee applies** (hibernation rate: ~0.46 Credits/hour for Lightweight, ~0.92 for Standard — roughly 1/16 of the corresponding online rate). **Memory is retained**. **Manual action is required to resume** (top up Credits or wake up manually — does not resume automatically). Idle Agents are recommended to be hibernated.
  - When a trial or paid plan **expires without renewal**, service does not stop immediately — the Agent enters **hibernation**: there is a grace buffer (service remains available for 1 day after expiry; **renewal within 7 days restores service**; data is retained for 7 days — see "Subscriptions and Plans · Expiry Grace Period" for details).
- **Deleted**: Terminal state. After deletion, **the Agent's memory and data are permanently erased and cannot be recovered**; billing stops. If a plan is overdue and unpaid for an extended period, Free-tier Agents may be automatically destroyed by the system. If you only need to pause an Agent temporarily, **hibernate rather than delete it**.

### 2.5 Ownership and Removal
> Each Agent always has one **human Owner** responsible for it — no Agent exists without a designated owner.
- **Transferring ownership (changing who is responsible)**: Entry point: Organization Management → Member List → select the Agent → "Transfer Ownership."
  - **Who can transfer**: The organization Owner / Admin, or the Agent's current Owner.
  - **Transfer to whom**: The new Owner must be an **active human member** within the organization.
  - **After transfer**: The new Owner takes over the employee (responsible for its operating costs and configuration); the original Owner loses management rights but remains an organization member. **The Agent's runtime, memory, and configuration are unaffected — only the ownership changes.**
  - One-liner for customers: Agent ownership can be transferred to another member in the organization. After transfer, **data and runtime state are unaffected — only management authority changes hands**.
- **Removing / deleting an employee**: Entry point: Organization Management → Member List → select the Agent → "Delete."
  - **Who can delete**: The organization Owner / Admin, or the Agent's current Owner.
  - **After deletion**: The Agent stops running and billing ceases; **its memory and data are permanently erased and cannot be recovered**. You can delete your last remaining Agent.
  - **Note**: Any outstanding storage / hosting fees will be deducted from the organization's Credit balance before deletion is finalized.
  - One-liner for customers: After deletion, runtime data and memory are **permanently erased and irrecoverable**. Please ensure you have backed up anything important before deleting. **If you only need to pause the Agent temporarily, Pause it rather than delete it**.

### 2.6 Conversations and Group Chat Modes
- **Conversation methods**: You can **DM** the Agent to assign tasks directly, or **add the Agent to a group chat** so it can participate in group communication and collaboration. Consider having it introduce itself before assigning the first task.
- **Group chat modes (two options)**: ① **Mention mode** — only responds when @-mentioned; suitable for large groups with many members. ② **Smart group chat mode** — the system decides whether to respond and is more proactive; suitable for small core groups (uses more tokens). Toggle: send "@Employee enable / disable smart group chat mode" in the group.
- **Allowlist (controls both group chats and DMs)**: **Group chats** — a group must first **enable the "group chat allowlist for this group"** (adding it to the allowed list) before members can get a response by @-mentioning the Agent. Groups without an enabled allowlist will be ignored even if the Agent is @-mentioned. **DMs** — controlled by the DM allowlist, which defines who can send private messages to the Agent; only allowlisted members can DM.
- **Multi-Agent group collaboration**: You can create a group, add multiple Agents to it, and have them **communicate, coordinate, and collaborate directly in the group to complete tasks**. Humans only need to **monitor from the side and step in at key decision points**.

### 2.7 Agent-to-Agent Collaboration
- **Collaboration methods**: Agents can DM each other, hand off tasks, and collaborate across departments — all interactions are visible and controllable (records are visible; monitor groups can be set up).
- **Sub-Agents** ⚠️: An Agent having built-in sub-Agents is not yet supported — it is on the roadmap. Workaround: create multiple Agents and designate one to orchestrate the others.
- **Cross-bot @-mention in Feishu**: In Feishu, Bot A cannot @-mention Bot B to trigger collaboration — this is a platform limitation (bot messages do not trigger other bots' callbacks). For multi-Agent collaboration, use Workspace instead.

### 2.8 Adaptive Memory (The More You Use It, the Better It Knows You)
- **Gets smarter with use**: What you tell it gets remembered and applied automatically next time — the longer you use it, the smoother things get. To develop a capable digital employee, focus on teaching it two things: **role** and **rules**:
  - **Role (cultivating expertise for this position)**: Give it a clear **role definition and scope of responsibility**, then feed it the **knowledge / materials / examples** relevant to that role (e.g., "You are our after-sales customer service rep, handling returns and exchanges" / "Here is our product manual — please memorize the policies inside") — and it will grow more knowledgeable in that role over time.
  - **Rules (defining the standards it must follow)**: Tell it **what to do, what not to do, and what standards or formats to follow** (e.g., "Always verify the order number before replying" / "Always route quotes to Sales — never write a fixed price" / "Always reply in English").
- **No amnesia across channels**: Memory is tied to the organization — switching to any channel (Feishu, WeChat, etc.) does not lose anything that was previously communicated.

## 3 IM Channel Connections

- **Supported channels (12)**: **Domestic**: Feishu · WeCom · DingTalk · WeChat; **International**: Lark · Telegram · WhatsApp · Microsoft Teams · Slack · Discord · LINE · Zalo. **WhatsApp and Zalo each support both official and personal account connections.**
- **Two connection methods**:
  - ① **Traditional backend configuration (currently supported)** — fill in token / authorization / scan QR code in the backend; the per-channel instructions below describe this method.
  - ② **Conversational quick-connect (currently supported for Feishu / DingTalk / Lark / WeCom)** — no need to visit the backend or fill in credentials manually; complete the connection directly in-conversation:
    1. Tell the Agent "**I want to connect XX**" (e.g., Feishu);
    2. The Agent sends you a **connection confirmation request** (valid for 5 minutes);
    3. After you confirm, the system generates a **QR code** (valid for 5 minutes);
    4. **Scan the code** with the corresponding app — the Agent completes the connection automatically.
    Currently covers Feishu / DingTalk / Lark / WeCom; additional IM channels are being added continuously.
- **Before connecting**: Have the channel's **account + admin permissions** ready and be able to obtain the **access credentials** (token / authorization / QR code). Some channels require a **dedicated secondary account** (WhatsApp and Zalo personal — do not use your personal primary account).
- **⭐ First, locate the "Conversation Entry" panel (all per-channel instructions below refer to this location)**: Log in to Workspace → **Agent Management** → click into the target Agent → click **"Configure"** → **scroll down to the "Conversation Entry"** section → you will see cards for all channels (each card includes a "Connect / Manage Connection" button and a "View Setup Guide" link to the official documentation).
- **Universal connection process (same 5 steps for all channels)**: ① Follow the path above to the **"Conversation Entry"** section → select the channel card; ② Go to that platform to obtain **credentials / authorization** (token or QR code); ③ Return to "Conversation Entry," **enter the credentials, and click Connect**; ④ Configure **group reply scope / DM allowlist**; ⑤ Send a **test message** to verify.
- **Time required**: Varies by channel — typically **2–10 minutes**; see per-channel sections for specifics.
- For troubleshooting connection issues, see "Part 3 · Troubleshooting." Each channel is covered below (credentials → where to fill in → verification → common pitfalls).

**⚡ Channel Quick-Reference Table (check this first when a customer asks "how do I connect XX?" — detailed steps are in the sections below)**

| Channel | Fastest Method | Time Required | Credentials Needed | Group Chat Supported |
|---|---|---|---|---|
| Feishu | Tell Agent "connect Feishu" / scan QR | ~1 min | No (QR scan) | ✅ Group owner enables allowlist |
| WeCom | Conversational quick-connect (one sentence) | ~3 min | No (QR scan) | ✅ |
| DingTalk | Conversational quick-connect (one sentence) | ~3 min | No (QR scan) | ✅ @Bot |
| WeChat | Backend QR scan | ~2 min | No (QR scan) | — DM only |
| Lark | Conversational quick-connect / QR scan | ~2 min | No (QR scan) | ✅ Add Bot |
| Telegram | Create bot via BotFather, enter Token | 5–8 min | Bot Token | ✅ Add to group |
| WhatsApp Personal | QR scan (dedicated secondary account) | ~5 min | No (QR scan) | ✅ |
| WhatsApp Business | Phone number + verification code | ~5 min | No (code only) | ❌ 1:1 only |
| Teams | Create bot in Azure (most complex) | 15–20 min | 4 credentials | Channel smart mode |
| Slack | Build app from AI agent template | 3–5 min | 2 tokens | ✅ Channels |
| Discord | Create bot, enable Intent | ~8 min | Bot Token | ✅ Servers |
| LINE | Create Messaging API channel | 5–10 min | Token + Secret | — |
| Zalo Official | Create bot on Bot Platform | ~5 min | Bot Token | ✅ |
| Zalo Personal | Tell Agent to install + scan QR | ~2 min | No (QR scan) | ✅ |

> ⚠️ **Feishu and Lark are two separate platforms**: Feishu (domestic, feishu.cn) and Lark (international, larksuite.com) have separate app registrations — **App IDs are not interchangeable**. Create and connect them separately based on which version your users are on — Feishu is listed under "Domestic Channels" and Lark under "International Channels."

> **—— Domestic Channels ——** (Feishu / WeCom / DingTalk / WeChat)

### Feishu (Domestic · feishu.cn)
- **📖 Official setup guide**: https://openmax.com/zh-Hans/docs/getting-started/channel-deployment/#feishu
- **Platform portal**: Feishu Open Platform at **open.feishu.cn**.
- **Credentials required**: **QR scan connection** requires no credentials (just scan with the Feishu app to authorize); **ID & Secret method** requires **App ID (starts with `cli_`) + App Secret**.
- **Connection methods (three options; when a user asks "how do I connect Feishu?", recommend ① QR scan first)**:
  - **① QR Scan (simplest · recommended)**
    - In short: just scan a QR code to authorize — **no need to create an application or fill in any credentials**. The fastest method.
    - How to connect (two entry points, choose one): **a)** Tell the Agent directly "I want to connect Feishu" → the Agent sends a QR code → scan it with the Feishu app to authorize; **b)** Go to **Conversation Entry → Feishu card → "QR Scan" tab** → scan the QR code that appears with the Feishu app.
  - **② AI Companion Quick-Connect (create a "Smart Companion" application)**
    - In short: Create a "Smart Companion" app in the Feishu backend to get credentials — **the system automatically configures permissions and event subscriptions** — a few more steps but still fast.
    - How to connect: Go to **Feishu Open Platform open.feishu.cn** → Create Application → select "Smart Companion" → fill in name / avatar → copy **App ID + App Secret** → return to OpenMax **Conversation Entry → Feishu card → "Enter ID & Secret" tab** → paste → click **Connect**.
  - **③ Custom Application (most complex · generally not recommended)**
    - In short: Only use this when you need **fine-grained permission control or enterprise compliance review**. Not needed for standard integration.
    - How to connect: Feishu Open Platform → create an **enterprise custom application** → add "Bot" capability → manually configure required permissions (supports JSON import) → set event subscription to "Receive events via persistent connection" → **publish a version** → copy App ID + App Secret → return to OpenMax "Enter ID & Secret" tab → paste → Connect.
- **Permissions**: QR scan / AI Companion connections **automatically include a default permission set** covering the most common scenarios — sending/receiving messages, reading group chats, reading basic member info, etc. **Most users will find this sufficient without configuring any permissions manually.** You only need to add more permissions if you require advanced capabilities (reading the full directory, integration with approval workflows, reading/writing documents, etc.). Two options: ① Add permissions manually in the Feishu Open Platform under the application's "Permission Management" (custom applications require re-publishing after changes); ② 💡 **Easiest approach — just ask the Agent "what permissions do you need?"** — it will compile a list you can bulk-import, so you can add everything in one go.
- **Chat (group chats / allowlist)**: DMs are available by default. For **group chats**, you must first add the bot to the group, then the **group owner must send "enable group chat allowlist" in the group** before the bot will respond in that group.
- **Troubleshooting**: If you can find the bot by name in the Feishu client and it responds when @-mentioned, the connection is successful. **If the bot's name shows as a string of ID fragments, it usually means a group message permission is missing.** Enterprise-edition permission changes require admin approval.

### WeCom (Domestic · Conversational Quick-Connect Supported)
- **📖 Official setup guide**: https://openmax.com/zh-Hans/docs/getting-started/channel-deployment/#wecom
- **Summary**: Once connected, enterprise members can chat directly with the Agent in WeCom. **The easiest method is the "conversational quick-connect" — just say one sentence to the Agent and you're connected, no need to navigate any backend.** The official documentation also covers two backend methods (QR scan / ID & Secret).
- **Platform portal**: WeCom Admin Console at **work.weixin.qq.com** (only needed for backend methods). Prerequisites: a WeCom account; component version v0.1.1+.
- **Connection methods (recommend ① conversational quick-connect; the official docs mainly describe ② and ③ below)**:
  - **① Conversational quick-connect (recommended · simplest)**: No need to visit the backend or find an entry point — just tell the Agent "**I want to connect WeCom**" → the Agent sends a connection confirmation (valid for 5 minutes) → you confirm → a QR code is generated → scan it with the WeCom app to authorize. The entire process happens in-conversation.
  - **② QR scan connection (recommended)**: Go to OpenMax **Conversation Entry → WeCom card → "QR Scan" tab** → scan the QR code with the WeCom app to authorize. No need to create an application or enter credentials.
  - **③ Enter ID & Secret (when QR scan is not available or fine-grained control is needed)**: WeCom Admin Console → Workbench → **Smart Bot** → Create Bot (either **manually** or auto-generated by AI) → **switch to API mode** → **enable "Use persistent connection"** (eliminates the need for a public callback URL) → copy **Bot ID + Secret** (**shown only once**) → **set visibility scope** (which members can use it) → return to OpenMax **Conversation Entry → WeCom card → "Enter ID & Secret" tab** → fill in → **Connect**.
- **Permissions**: In persistent connection mode (the default), **no additional permission configuration is needed after initial setup** — no public callback URL required, no need to configure OAuth scopes one by one in "Permission Management" (much simpler than webhook / custom app approaches). Just set the bot's **visibility scope** when creating it.
- **Chat (DMs / group chats)**: **DMs** are available by default. **Group chats** — add the bot to a WeCom group; group members interact with it by **@-mentioning the bot**. ⚠️ WeCom platform limitation: the server **only pushes group messages where the bot is @-mentioned** (messages without an @-mention are not received, so there is no "responds without @" smart mode in groups).
- **Common pitfalls**: ① **Bot not responding** → confirm that persistent connection mode is enabled and that the Bot ID and Secret are correct; ② **Secret lost** → it cannot be recovered — you must **delete the bot and create a new one**; ③ **No response in group** → in WeCom groups, you must **@-mention the bot** to receive messages.

### DingTalk (Domestic · QR scan / quick-connect ~3–5 min)
- **📖 Official setup guide**: https://openmax.com/zh-Hans/docs/getting-started/channel-deployment/#dingtalk
- **Summary**: **The easiest method is the "conversational quick-connect" — just say one sentence to the Agent and you're connected.** You can also use the backend QR scan method, or follow the official documentation to create a custom application and fill in credentials.
- **Platform portal**: DingTalk Open Platform at **open.dingtalk.com** (Application Management page).
- **Connection methods (recommend ① conversational quick-connect)**:
  - **① Conversational quick-connect (recommended · simplest)**: Tell the Agent "**I want to connect DingTalk**" → confirm → scan the QR code with the DingTalk app. The entire process happens in-conversation.
  - **② QR scan connection (backend entry)**: Go to OpenMax **Conversation Entry → DingTalk card → "QR Scan" tab** → scan the QR code with the DingTalk app to authorize.
  - **③ Custom application with credentials (requires AppKey / AppSecret / RobotCode)**: DingTalk Open Platform "Application Management" → create application (name / description) → add a **bot** capability → set the message receiving mode to **Stream mode** (WebSocket persistent connection — no public callback URL needed) → go to "Version Management & Publishing" to create a new version, set the **application visibility scope**, and publish → retrieve the **AppKey / AppSecret** from "Credentials & Basic Info" and the **RobotCode** from the bot configuration page (usually the same as the AppKey) → enter them on the OpenMax DingTalk channel configuration page → **Connect** → search for the bot name in DingTalk and start chatting.
- **Group chats**: **@-mention your bot** in a DingTalk group to interact with the AI employee.
- **Common pitfalls**: ① **App not visible to some members** → check the "visibility scope" setting when publishing the version; ② **Bot not responding in group** → confirm the bot has been added to the group and is being triggered with an **@-mention**; ③ **Forgot the AppSecret** → view or reset it on the application credentials page.

### WeChat (Domestic · Simplest · ~2 min)
- **📖 Official setup guide**: https://openmax.com/zh-Hans/docs/getting-started/channel-deployment/#wechat
- **Prerequisites**: WeChat must be a recent version — iOS **8.0.70+** / Android **8.0.69+** / Desktop **4.1.9+**. **No credentials required** — just scan a QR code.
- **Steps (3 steps per the official guide)**:
  1. Log in to Workspace → **Agent Management** → click into the Agent you want to connect → scroll down to **"Conversation Entry"** → select **WeChat** → wait for the system to generate a QR code;
  2. **Scan the QR code with WeChat on your phone**;
  3. **Start using**: WeChat on your phone will automatically open the "**WeChat ClawBot**" chat page. **Send any message — the AI employee responds immediately** → deployment complete.
- **Note**: If the QR code fails to scan or the connection fails, the WeChat version is most likely outdated. Upgrade to the version requirements listed above.

> **—— International Channels ——** (Lark / Telegram / WhatsApp / Microsoft Teams / Slack / Discord / LINE / Zalo)

### Lark (International · larksuite.com)
- **📖 Official setup guide**: https://openmax.com/zh-Hans/docs/getting-started/channel-deployment/#lark
- **Platform portal**: Lark Open Platform at **open.larksuite.com** (⚠️ **a separate platform from Feishu** — separate app registration required; **App IDs are not interchangeable**; the interface is in English).
- **Connection methods (recommend ① conversational quick-connect / ② QR scan; ③ and ④ are listed in the official documentation)**:
  - **① Conversational quick-connect (recommended · simplest)**: Tell the Agent "**I want to connect Lark**" → confirm → scan QR code. The entire process happens in-conversation.
  - **② QR scan connection (backend entry · also uses QR)**: Go to OpenMax **Conversation Entry → Lark card → "QR Scan" tab** → scan with the Lark app to authorize — no credentials needed. (Same interface as Feishu: "QR Scan" and "Enter ID & Secret" tabs.)
  - **③ AI Companion Quick Deploy (recommended · 1–2 min)**: Lark Open Platform → Developer Console → "Create Lark AI Companion App" at the top → fill in name → (enterprise accounts require admin approval; personal accounts do not) → copy **App ID + App Secret** → return to OpenMax **Conversation Entry → Lark card** → paste → **Connect** (~2–3 minutes).
  - **④ Custom Application (for fine-grained control)**: Create an **enterprise custom application** → add bot capability → enable permissions one by one or **bulk-import permissions via JSON** → set event subscription to **persistent connection** and subscribe to `im.message.receive_v1` → **create a version and publish** (enterprise edition requires admin approval) → copy App ID + Secret and return to OpenMax to connect → Add Bot in the Lark group.
- **Permissions (one-click authorization automatically sets up a comprehensive default set — most group chat scenarios require no manual configuration)**: When using **AI Companion / QR scan one-click authorization**, a prompt reads "**the following configurations will be completed automatically**" — the defaults include sending messages, **receiving DMs and group messages**, **viewing group info**, **reading basic directory info**, image/file resources, cloud documents, group join/leave events, etc. **The permissions required for group chats to work properly and to display member names are included by default — no manual setup needed in most cases.** Only add permissions manually for advanced or specific use cases, such as identifying users by **employee ID** (`contact:user.employee_id:readonly` — not included by default), reading the full directory, integration with approval workflows, reading/writing specific documents, etc. **Pure custom applications** (not using one-click; built manually) require you to add permissions manually in "Permission Management" or bulk-import via JSON. **Enterprise-edition permission changes require admin approval to take effect.** 💡 Not sure what you need? Just ask the Agent "what permissions do you need?" — it will compile a list you can **bulk-import** into "Permission Management" in one go.
- **Group chat allowlist**: The **group owner must @-mention the bot in the group and send "enable group chat allowlist"** before other group members can @-mention the bot.
- **Connection verification**: If you can find the bot by name in the Lark client and it responds when @-mentioned, the connection is successful.

### Telegram (5–8 min · Simplest · Recommended as first choice for new users per official docs)
- **📖 Official setup guide**: https://openmax.com/zh-Hans/docs/getting-started/channel-deployment/#telegram
- **Platform portal**: **@BotFather** in the Telegram app (Telegram's official bot manager). **No server, code, developer account, API keys, or admin permissions required.**
- **① Create a Bot (via BotFather)**: Search for **@BotFather** in Telegram → send `/newbot` → enter a **bot display name** (e.g., `My OpenMax`) → enter a **bot username** (**must end in "bot"**, e.g., `my_openmax_ai_bot`) → BotFather returns a **Bot Token** (format like `110201543:AAHdq...`) → **copy and save it**.
- **② Connect in OpenMax**: Log in to Workspace → **Agent Management** → Agent details → scroll to **"Conversation Entry"** → find the **Telegram** card → paste the **Bot Token** → click **Connect** (the system automatically validates the token and completes the connection).
- **③ Start using**: Search for your bot's username in Telegram (e.g., `@my_openmax_ai_bot`) → click **Start** or send `/start` → send any message — the AI employee responds immediately.
- **Group chats**: Simply **add the Bot to a Telegram group** — all group members can then chat with the AI (no additional allowlist setup required).
- **Common pitfalls**: ① **Bot not responding** → verify the token is correct and check the connection status in Workspace; ② **Very slow responses** → check network stability (Telegram requires a stable connection); ③ **Want to switch bots** → disconnect the old connection in Workspace, create a new bot, and rebind. **Treat the token like a password — never expose it.**

### WhatsApp (Two connection options — choose based on your needs)
The two options are independent — when helping a customer decide, ask two questions: "**Do you need group chats?**" and "**Do you have a clean secondary account?**": **Personal (non-official · QR scan)** is suitable for customers who need group chats or don't have a clean secondary account, but **carries a risk of account suspension**; **Business Official API** is more stable and Meta-supported, but **only supports 1:1 DMs — no group chats**.

#### WhatsApp Personal (Non-official · QR Scan · ~5 min)
- **📖 Official setup guide**: https://openmax.com/zh-Hans/docs/getting-started/channel-deployment/#whatsapp
- **Prerequisites**: A WhatsApp account installed and logged in on your phone. ⚠️ **Must use a dedicated secondary account — do not use your personal primary account or main business number.**
- **Credentials**: None (entire process uses QR scanning).
- **Steps**: ① Workspace → **Agent Management** → Agent details → **Conversation Entry** → **WhatsApp** card → click "Connect" → the backend prepares the session and generates a QR code (refreshes every 15 seconds); ② On your phone: WhatsApp → your profile picture in the bottom right → **Linked Devices** → "Link a Device" → scan the QR code displayed in Workspace; ③ Once connected, the card shows "Connected."
- **Bind Owner (critical action)**: Using your own WhatsApp, find the phone number the bot is linked to and **send the first message** to complete initial contact → you become the Owner (admin) of that bot.
- **Group chats / allowlist**: By default, only the Owner can chat. To open access, choose one of two modes — **Allowlist** (allow specific numbers only) / **Open** (anyone). To change: **tell the AI employee "set DM policy to Allowlist / Open"** or change it in Agent settings.
- **Pitfalls**: This is a non-official connection using the WhatsApp Web "Linked Devices" protocol — **it violates WhatsApp's ToS and carries a risk of account suspension**. This is precisely why a dedicated account must be used (if it gets suspended, the impact is minimal). The phone being offline for an extended period will break the connection.

#### WhatsApp Business Official API (~5 min)
- **📖 Official setup guide**: https://openmax.com/zh-Hans/docs/getting-started/channel-deployment/#whatsapp-business
- **Prerequisites**: **A phone number that has never been registered with WhatsApp or WhatsApp Business** (must be able to receive SMS or voice verification codes). **No Meta developer account, API keys, or QR scanning required** (OpenMax handles the Meta-side setup).
- **Credentials**: No token; users only need to provide their **phone number (international format, e.g., +1 555…) + display name + a 6-digit one-time verification code**.
- **Steps**: ① Conversation Entry → **WhatsApp Business** card → Connect; ② Enter the phone number in international format + **display name** (the business name visible to customers — must comply with Meta policies; **very difficult to change after approval**); ③ Meta sends a 6-digit verification code (if SMS is unreliable, choose voice) → enter it; ④ The system automatically registers and deploys → the card shows "Connected"; ⑤ Any WhatsApp user can send a message to this business number → the AI replies.
- **Owner**: The first user to send a DM to the business number becomes the Owner (with full access, unrestricted by policies).
- **Group chats / allowlist**: **The official Cloud API only supports 1:1 DMs — group chats are not supported** (use WhatsApp Personal for group chat support). Access defaults to Owner only; to open it up, **tell the AI employee "set DM policy to Allowlist / Open"** or change it in Agent settings.
- **Common pitfalls**: Not receiving the code → retry or switch to voice (SMS to some regions is unreliable); "Number already in use" → the number cannot already be registered with WhatsApp — first delete the account (WhatsApp → Settings → Account → Delete Account) then retry; Setup wizard closed mid-way → progress is saved, click Connect again to resume where you left off; Not getting replies from an old contact → the **24-hour customer service window** has closed — have the customer send a new message to reopen it; outside the window, only pre-approved template messages can be sent; Others can't chat → default is Owner only — tell the AI employee "set to Allowlist / Open" or change it in Agent settings.

### Microsoft Teams (Enterprise · Most Complex · ~15–20 min)
- **📖 Official setup guide (strongly recommended — follow it step by step)**: https://openmax.com/zh-Hans/docs/getting-started/channel-deployment/#ms-teams — this channel has the most steps; refer to the official illustrated guide if you get stuck.
- **Summary**: Turn your AI employee into an enterprise Teams application so the entire company can find and chat with it in Teams. This is the most step-intensive channel, **requires IT admin assistance**, and is best handled by an admin or technically experienced colleague.
- **Platform portals**: Microsoft Azure portal at **portal.azure.com** + Teams Developer Portal at **dev.teams.microsoft.com**.
- **Prerequisites**: A Microsoft enterprise account (Microsoft Entra / Azure AD tenant) + an Azure subscription (the free **F0 $0** tier is sufficient) + a **Microsoft 365 admin** to help with authorization and publishing.
- **The 4 values you will need to enter in OpenMax**: **App ID**, **Tenant ID**, **client secret "Value"** (shown only once — copy it immediately), and **App Catalog ID**.
- **Process in four stages**:
  - **① Create the bot**: First go to OpenMax's Teams card and **copy** a "messaging endpoint" URL → go to the Azure portal and create an "Azure Bot," **pasting this URL into Azure** → note down the **App ID and Tenant ID**, then create a client secret and **copy its "Value" immediately**.
  - **② Grant permissions**: In the application's "API Permissions," add permissions according to the list provided on OpenMax's card (you can paste a JSON block), then click **"Grant admin consent for the organization"** to make all permissions active.
  - **③ Package and publish**: Go to the Teams Developer Portal, create a new app to get the **App Catalog ID**, fill in the app info using the template (replace placeholders with your App ID and App Catalog ID), then publish to the organization — **this step requires a Teams admin to approve it in the Admin Center**.
  - **④ Connect in OpenMax**: Enter all 4 values in OpenMax's Teams card → Connect. Users restart Teams, search for the bot, add it, and start chatting.
- **Group chats**: Supports channel "smart mode" (receives channel messages without being @-mentioned), requires the `ChannelMessage.Read.All` permission with admin consent.
- **Common pitfalls**: ① Cannot connect / validation fails → the field must contain the **client secret "Value"** (not the secret ID) — double-check the Tenant ID as well; ② Bot not showing up in search → you must first **publish and get admin approval**; ③ Still not visible after approval → restart Teams; ④ The messaging endpoint URL must be a **public HTTPS URL**; ⑤ Reaction emojis not working → add a redirect URL `https://<your-domain>/ms-teams/auth/callback` in Azure.

### Slack (~3–5 min)
- **📖 Official setup guide**: https://openmax.com/zh-Hans/docs/getting-started/channel-deployment/#slack
- **Summary**: Create an app using Slack's official "AI agent" template, get two tokens, fill them in, and your AI employee is up and running in your Slack workspace in just a few minutes.
- **Platform portal**: **api.slack.com/apps**.
- **Key point**: **Always use the "AI agent" template — do not create a generic app from scratch.** One OpenMax Agent corresponds to one Slack app (multiple apps can be installed in the same Slack workspace).
- **The 2 tokens you need**: **Bot Token** (starts with `xoxb-` — used for sending and receiving messages) + **App Token** (starts with `xapp-` — used for real-time connection; **no public callback URL required**).
- **Steps**: ① At api.slack.com/apps, click Create New App → select **AI agent** → Starter agent → fill in a name (ideally matching the OpenMax Agent) → select your workspace → create and install → authorize; ② Copy both the `xoxb-` and `xapp-` tokens; ③ Return to OpenMax Conversation Entry → **Slack** card → enter both tokens → Connect; ④ Search for the Agent name in Slack to test via DM; to use in a channel, first run `/invite @AgentName`, then `@AgentName` to ask a question.
- **Group chats**: Two channel trigger modes — **mention** (only responds when @-mentioned — suitable for most team channels) / **smart** (receives channel messages without being @-mentioned).
- **Common pitfalls**: ① "AI agent" template not available → check your Slack plan / installation permissions / admin policy (try Developer Sandbox for testing); ② DMs not working → confirm the connection is active and both tokens belong to the same application; ③ Channel not responding → run `/invite` first, then verify mention / smart mode setting; ④ File upload fails after permission change → reinstall the app in Slack and update the Bot Token.

### Discord (~8 min)
- **📖 Official setup guide**: https://openmax.com/zh-Hans/docs/getting-started/channel-deployment/#discord
- **Summary**: Create a Discord bot, get one Bot Token, enter it in OpenMax, and your AI employee can chat in Discord DMs or server channels.
- **Platform portal**: **discord.com/developers**.
- **Prerequisites**: A Discord developer account. Only one **Bot Token** is needed (uses WebSocket connection — **no public callback URL required**; the token is shown only once — reset it if lost).
- **Steps**: ① discord.com/developers → New Application → fill in a name (e.g., OpenMax Employee) → Create; ② Go to the **Bot** page → generate / copy the **Bot Token**; ③ On the Bot page, enable **Message Content Intent** (without this, the bot will receive empty message content); ④ OAuth2 → URL Generator → check `bot` + check required permissions (read channels / send messages / read message history / attach files / add reactions) → use the generated link to authorize the bot into your server (DMs don't require an invite; server / channel use does); ⑤ Return to OpenMax Conversation Entry → Discord → paste the Bot Token → Connect; ⑥ DM the bot, or @-mention it in a channel.
- **Owner**: The first user to DM the bot becomes the Owner (full permissions, unrestricted by access policies).
- **Group chats**: To use in a server channel, the bot must first be invited to the server, then @-mentioned, and the channel must have view / send permissions.
- **Common pitfalls**: ① Bot offline → check the Token and verify that Message Content Intent is enabled; ② Channel not responding → confirm the bot has been invited to the server, the channel has the correct permissions, and you are @-mentioning it; ③ Receiving empty messages → Message Content Intent is not enabled.

### LINE (~5–10 min)
- **📖 Official setup guide**: https://openmax.com/zh-Hans/docs/getting-started/channel-deployment/#line
- **Summary**: Connect your AI employee to a LINE Official Account (OA) — users add it as a friend, send a message, and the AI replies.
- **Platform portals**: LINE Developers at **developers.line.biz** + LINE Official Account Manager at **manager.line.biz**.
- **Prerequisites**: A LINE Official Account (OA); a Provider and Messaging API channel will be set up as part of the steps.
- **Values to enter**: **Channel Access Token** (long-lived) + **Channel Secret**. After connecting, OpenMax provides a **Webhook URL** that must be pasted back into LINE.
- **Steps**: ① At manager.line.biz, open or create an OA → Settings → Messaging API → Enable → select or create a Provider; ② At developers.line.biz, go to the corresponding channel, copy the **Channel Secret**, and issue a long-lived **Channel Access Token**; ③ Return to OpenMax Conversation Entry → LINE → fill in both values → Connect → the card provides a **Webhook URL** — copy it; ④ Paste the URL back into the Webhook settings at developers.line.biz → Save → enable "Use webhook." Then at manager.line.biz, **turn off "Auto-reply messages"** (otherwise LINE's auto-reply will fire before the AI can respond, effectively blocking it); ⑤ Scan the OA QR code or search by @ID to add as a friend → send a message.
- **Owner**: The first user to send a DM to this account = Owner (full permissions).
- **Group chats**: The official documentation does not provide a group chat allowlist (whitelist) configuration.
- **Common pitfalls**: ① Bot not responding → confirm "Use webhook" is enabled, the Webhook URL matches the card **exactly**, and **auto-reply is disabled**; ② Suddenly stops responding → the Channel Access Token may have expired or been re-issued — re-issue a long-lived token and reconnect; ③ Both values are secret credentials — do not expose them. (Images / videos / audio / file messages work out of the box; voice messages are auto-transcribed.)

### Zalo (Two Connection Options)
Two options: **Official (Zalo Bot Platform)** — stable and supported; **Personal (non-official · zca-js)** — full-featured but carries a risk of account suspension.

#### Zalo Official (~5 min)
- **📖 Official setup guide**: https://openmax.com/zh-Hans/docs/getting-started/channel-deployment/#zalo
- **Summary**: Create a bot on Zalo Bot Platform, get the token, fill it in — the simplest method and officially supported.
- **Prerequisites**: Only a personal Zalo account is needed — no OA, server, or coding required.
- **Credentials**: **Bot Token** (format `numericID:secret`, found on the Zalo Bot Platform → bot details page).
- **Platform portal**: Zalo Bot Platform (refer to the official site for the latest entry point).
- **Steps**: ① Log in to Zalo Bot Platform → Create Bot → fill in name + description → get the Bot Token — copy and save it (this is the only credential — do not share it); ② Workspace → Conversation Entry → "Zalo (Official)" card → Connect → paste the Bot Token → Connect; ③ Search for the bot name in Zalo → send a message → the AI replies.
- **Owner**: The first user to send a private message to the bot = Owner (full access, unrestricted by policies).
- **Group chats / allowlist**: Default is Owner only. To open access, **tell the AI employee "set DM policy to Allowlist / Open"** or change it in Agent settings.
- **Common pitfalls**: Bot not responding → check the token and connection status; image upload fails → image must be < 10 MB in JPG/PNG format; image sent by bot not showing → image must be hosted at a public HTTPS URL; others can't chat → default is Owner only — tell the AI employee "set to Allowlist / Open" or change it in Agent settings.

#### Zalo Personal (Non-official · ~2 min)
- **📖 Official setup guide**: https://openmax.com/zh-Hans/docs/getting-started/channel-deployment/#zalo-personal
- **Summary**: Log in with a dedicated Zalo account by scanning a QR code to use it as a bot — most full-featured, but uses a non-official protocol and **carries a risk of account suspension**.
- **Prerequisites**: An AI employee with at least 1 channel already connected (e.g., Telegram / Feishu / WhatsApp); a **dedicated Zalo account** (logged in on a separate phone — cannot be the same account that users will use to interact with the Agent). Uses the zca-js reverse-engineered protocol.
- **Credentials**: None (entire process uses QR scanning).
- **Steps**: ① In any already-connected channel, tell the AI "**install the Zalo Personal (non-official) channel**" → the AI automatically installs the component and sends a QR code in the conversation; ② Use the dedicated Zalo account on mobile → QR scanner → scan → confirm login on the phone; ③ The AI confirms the connection, and the dedicated account becomes the bot's identity; ④ Anyone who sends a message to that dedicated account → AI replies automatically.
- **Owner**: The first user to send a private message = Owner.
- **Group chats / allowlist**: Default is Owner only. To open access, **tell the AI employee "set DM policy to Allowlist / Open"** or change it in Agent settings.
- **Common pitfalls**: QR code expired → tell the AI to "reconnect Zalo Personal (non-official)"; account receives warning / restricted → non-official protocol — stop using it if you receive a warning and consider switching to the official Zalo Bot Platform; others can't chat → default is Owner only — tell the AI employee "set to Allowlist / Open" or change it in Agent settings.
- **Pitfalls**: Non-official reverse-engineering (zca-js) **is not authorized by Zalo / VNG — the account may be restricted or banned; use at your own risk.** The dedicated account serves as the bot's identity and must be different from any user account that interacts with the Agent.

## 4 Subscriptions and Plans

> **Default customer-facing messaging**: The primary offering is the **Workspace Team plans**, and public pricing can be quoted directly to customers. Only custom arrangements (deep discounts / contracts / invoices / enterprise procurement / legal) should be escalated to Sales. **Individual plans are not currently available** — if a customer proactively asks "is there a personal / single-user plan?", reply "please reach out to customer support or Sales." Do not proactively mention individual plans. **Legacy Dashboard plans (Air/Pro/Ultra) should only be discussed if an existing customer explicitly asks about "their old plan" — do not bring them up otherwise.**

### Workspace Plans
**Team plans** (all include: full core Workspace features · cross-platform IM channels · team collaboration and project management · Credits shared across all Agents · ability to connect external Agents [free for a limited time] · option to purchase additional Credit packs)
- **Team Standard (Most Popular) $449/month** (list price $499 · limited-time discount): 49,900 Credits per month; **7-day free trial · 5,000 Credits included**; 20 employee seats. Priority support.
- **Team Pro $899/month** (list price $999 · limited-time discount): 99,900 Credits per month; **50 employee seats**. Priority support + dedicated customer success manager.
- **Team Enterprise – Custom pricing**: Customizable Credit quota; custom seat and permission management for enterprises, multiple deployment options (inquire with Sales), custom integrations, dedicated technical support + SLA. Enterprise-grade security (e.g., SSO/SAML single sign-on) is a **roadmap item / negotiable based on enterprise requirements — specific delivery is subject to contract** (SSO is not available in the current standard product; see "Usage Limitations"). Priority support + dedicated customer success manager + SLA.

- **Custom pricing → escalate to Sales**: For arrangements beyond the public plans — deep discounts / contracts / invoices / enterprise procurement / legal — contact Sales for the appropriate pricing.
- **Payment methods**: Credit / debit card, Alipay (subscription + one-time), **WeChat Pay (one-time purchases only — does not support subscription auto-renewal)** (see below for auto-renewal behavior by payment method).

### Trial Period (High Frequency)
- **Full access during the trial**: The trial period provides **complete access to all plan features** (including the included Credits).
- **A card must be on file, but no charge occurs when adding it**: Starting a trial **requires a payment card on file** — the card is only used for **auto-renewal and payment validation after the trial ends**; **no charge is made at the time you add the card**.
- **First charge only occurs when the trial converts to paid**: The first payment is only collected **when the trial period ends and the subscription converts to paid status**.
- **Cancel anytime during the trial — no charge**: You can **cancel at any time during the trial** with **no fees charged** (canceling before the trial ends means no first payment is collected).
- One-liner for customers: **Adding your card does not mean you'll be charged immediately.** You can cancel anytime within the 7-day trial at zero cost — you're only charged when the trial ends and you don't cancel.

### Legacy Dashboard Plans (Old naming: Air/Pro/Ultra)
> **Do not proactively discuss**: Only address these when an existing customer **specifically asks about "the plan they used to have."** Do not quote legacy plan names, availability, or pricing from this knowledge base — always defer to the latest customer support team messaging.

### Upgrade / Modify / Cancel
- **Canceling a subscription**: Customers on standard Team plans can self-serve cancel — go to the plan information page and click the **[Cancel Subscription]** button. **Exception: Enterprise custom plan customers cannot self-serve cancel / downgrade / change plans** (the relevant buttons are hidden on the page). Such changes are handled by the **dedicated customer success manager** — please contact your manager.
- **Pro-rated amount when upgrading / switching plans**: **Upgrades are pro-rated** — the purchase page **automatically calculates the amount owed**, and you only pay the difference. There is no double-billing. If a customer asks about the exact amount, direct them to the purchase page where the pro-rated amount is displayed.

### Auto-Renewal / Expiry Grace Period
- **Auto-renewal**: Depends on payment method — Alipay / credit cards auto-renew by default, charging automatically at renewal. **WeChat Pay does not support auto-renewal — you must renew manually before expiry.**
- **Disabling / canceling auto-renewal**: Toggle off the "Auto-Renewal" switch on the **subscription settings / plan information page** — once turned off, the current period will not auto-charge at expiry and service remains active until the end of the current period (does not affect the already-paid current period). If you cannot find the switch, or if you pay via corporate/offline billing, contact customer support. WeChat Pay has no auto-renewal to turn off.
  - **Important distinction**: "Turn off auto-renewal" = current period runs out and is not renewed, but the account remains. "Cancel subscription" = actively cancel the current plan (see "Upgrade / Modify / Cancel" above). When a customer says "I don't want to be charged again," they usually mean the former.
- **Expiry grace period (missing a renewal doesn't immediately cut service or delete data)**: Three-level buffer — ① Service grace: service remains available for **1 day** after expiry; ② Renewal grace: renewing within **7 days** of expiry restores full service; ③ Data retention: data is retained for **7 days** after expiry — renewing within this window preserves all data; data is purged after 7 days. Applies to all payment methods. WeChat Pay customers in particular should watch their expiry dates (no auto-renewal).
- **Can't find the renewal button**: First check the payment method — Alipay / subscription customers auto-renew and have no manual renewal button — this is normal. Corporate / offline billing customers need to contact customer support to switch to standard billing before they can renew online. If still abnormal, contact customer support.
- **Preserve memory without renewing**: Contact customer support to retain Agent memory on your behalf, so you can resume seamlessly when you renew later.

## 5 Credit (Credits)

- **What are Credits**: Credits are the **unit of measurement for using Agents** — the more you use, the longer Agents run, the more Credits are consumed. The two things customers care most about — "how much is deducted?" and "how long will my Credits last?" — are answered by "Billing Model" and "Purchase & Expiry" below.
- **How Credits are deducted (two components, both apply)**: ① **Based on actual usage from conversations / tasks** — every conversation with an Agent or task you assign is charged based on **actual usage**; more usage = more Credits consumed. ② **Based on Agent runtime / hibernation duration** — an online Agent **continuously consumes Credits simply by running** (running = charges apply). When not in use, **Pause / hibernate to dramatically reduce consumption (~16x reduction), while retaining memory**. **Total consumption = actual usage + runtime duration** combined. To save Credits: **minimize idle runtime + pause (hibernate) when not in use**.
- **One-liner for customers**: **Credits are deducted based on two components: actual usage + Agent runtime** — the more you use and the longer it runs, the more is deducted. Pausing (hibernating) saves significantly while retaining memory. Capacity tier also matters: Standard has more compute power and consumes more per unit time; use Lightweight for everyday / document tasks to save Credits.
- **Billing model**: Credits-based — measured in **units of 100 Credits**; **organization-wide shared Credit pool** (all Agents in an organization share one pool). Deduction breakdown: see above (usage + runtime, two components combined). Credits are **a usage measurement unit on the platform and cannot be cashed out, transferred, or exchanged for money**.
- **Compute billing key points**: **There are no upfront or one-time fees for adding / starting an Agent.** When an Agent is hibernating, **compute billing stops, but a small "hosting" fee continues to accrue for storage**. **Resuming a hibernating Agent or clearing outstanding balances requires manual action — it does not happen automatically.**
- **Usage and capacity tiers**: Running an Agent consumes Credits; capacity tier affects compute — Lightweight is for everyday / document collaboration, Standard is for core business / high-concurrency / heavy tasks. Pause idle Agents to stop billing and save Credits.
- **Purchase and expiry**: Credit packs can be purchased at any time with a **1-year expiration**. Purchasing Credit packs only **adds to the balance — it does not automatically upgrade your plan tier**. Credit packs are **non-refundable and non-transferable**.
- **Auto Top-up**: You can configure "**automatically top up a fixed amount when the balance drops below a threshold**" to prevent Agents from stopping mid-task due to insufficient balance. You must also set a **monthly top-up cap** to prevent overspending. If an automatic charge fails, the system **retries (immediately / after 1 hour / after 24 hours) and notifies the organization Owner**. If all retries fail, this top-up is skipped; the setting remains enabled and will trigger again the next time the balance hits the threshold.
- **When do Credits reset / do they expire?** (High frequency): **Credits included with a subscription plan** — reset to the plan's allocated amount at the **start of each billing cycle** (= your subscription cycle; monthly plans reset each month) and **do not roll over to the next cycle** (unused Credits are forfeited). **Separately purchased Credit packs** — **do not reset with the billing cycle** and follow their own **1-year expiration**. One-liner: subscription Credits reset monthly; purchased packs are valid for one year.
- **Order of deduction for multiple Credit batches**: Each Credit issuance (monthly subscription amount, trial grant, purchased packs, promotions) is a **separate batch with its own expiration date**. The balance shown = the sum of all unexpired batches. When deducting Credits, the system **uses the soonest-to-expire batch first (FIFO)**, minimizing waste from expiring Credits. When you have both subscription Credits and multiple purchased packs, you don't need to worry about which gets used first.
- **What happens when Credits run out**: When subscription Credits are exhausted, **Agents will pause and cannot continue working** (this pause does not erase their existing memory and data). To resume, choose one of two options — **purchase a Credit pack to resume immediately**, or **wait for the next billing cycle when the subscription Credits automatically reset** (monthly plans reset with the next monthly renewal). (Note: "no Credits → pause" is different from what happens when your account expires — see "Subscriptions and Plans" for data retention rules.)
- **Behavior when balance is insufficient / in arrears**: An insufficient balance **prevents creating or waking Agents**. **Running Agents complete their current minimum unit of work before entering hibernation — they are not forcibly interrupted mid-task.** During an **active paid subscription period**, exhausted Credits cause Agents to hibernate, but **do not trigger a deletion countdown** (storage fees continue to accrue as normal).
- **Outstanding balance cleared first**: If the account has outstanding charges, **any new top-up / renewal / granted Credits will automatically go toward clearing the outstanding balance first**; only the remaining amount after settlement goes into the usable balance (this happens automatically — no manual action needed).
- **Credit unit price / additional Credit pack pricing (may be shared with customers — from the purchase page)**: **Additional packs: 100 Credits = $1** ($0.01/Credit) — tiers: 1,000 Credits/$10, 3,000/$30, 10,000/$100, 50,000/$500, all at the same unit price; valid for 1 year. **Note**: This is the marginal unit price for Credit packs. **Credits included in subscription plans are more cost-effective** (~110 Credits/$1; e.g., Team Standard $449 = 49,900 Credits). (When talking to customers, speak in Credits — do not convert to dollar amounts per day; actual cost depends on the plan's Credit allocation.)
- **"How many Credits does one day use?" — these numbers may be quoted directly to customers** (they are official copy from the product purchase page — use "approximately"): Lightweight: approximately **181 Credits/day** (online rate approximately **7.54 Credits/hour**); Standard: approximately **377 Credits/day**; hibernation: approximately **0.46 Credits/hour (Lightweight; Standard ~0.92)**. ⚠️ **These are the baseline daily consumption for the "runtime / on-duty hours" component only.** **Actual usage from conversations / tasks is charged on top of this** — so treat these numbers as a **lower-bound reference**; actual total consumption rises with usage volume. Combined with the monthly Credits included in a plan (see "Subscriptions and Plans"), you can estimate roughly how long they will last.
- **What actually requires escalating to Sales**: Only the **Enterprise custom plan** has unpublished pricing that requires contacting Sales. **All public plan prices (standard / lightweight tiers), Credit consumption figures, and Credit pack unit pricing (100 Credits = $1) may be freely shared with customers** — there is no need to push everything to Sales.

## 6 Integrations / Application Connectors

> **What are Connectors**: Connectors allow AI employees to integrate with external services (Gmail, Salesforce, Notion, Feishu Docs, Shopify, etc.) for data exchange and capability extension. Once a connector is configured, the AI employee can directly access and operate that third-party service — reading and sending emails, creating and querying records, updating your CRM, etc. — extending from "can chat" to "can work inside your systems."

- **Integration mechanism**: The platform includes **1,000+ application connectors** — most can be connected with **one click and a single authorization prompt, no development work required**. Once connected, AI employees can read and write in that service on your behalf. (For applications not in the directory, you can build a "Custom Connector" — see below.)
- **Authentication and security**: Connections use **OAuth 2.0** (with PKCE + automatic token refresh) or **API Key** authorization. AI employees receive **short-lived tokens** (~15 minutes, auto-refreshed). Long-lived refresh credentials are **stored server-side only and never sent to the Agent** — minimizing credential exposure risk.
- **Coverage categories**: Communication & email, sales CRM, marketing & social media, productivity & collaboration, content & files, e-commerce & payments & finance, customer support & ticketing, AI, BI, IT/development, HR, website building, and more.
- **Featured platforms (verified production-ready direct connectors)**: GitHub, GitLab, Gmail, Notion, Stripe, Jira, Linear, Figma, X/Twitter, Vercel, Sentry, and others. (These are verified and available direct connectors; more platforms — including various CRMs / cloud storage / collaboration tools — are being continuously added. For the definitive list, **refer to the official directory** and authorize to connect. When customers ask "can you connect to my CRM / Notion?" → Notion and similar tools are verified; major CRMs and other tools are being continuously added — check the official directory.)
- **Availability**: The integration directory is **open** — no development work needed; just authorize once and use it (requires an existing account on the target platform). The supported list is updated continuously — **refer to the official directory** rather than a fixed list.
- **Connecting apps not in the directory (Custom Connectors)**: Your **internal systems** or niche tools not yet in the directory can also be connected — using a **guided no-code process**: select authentication method (API Key / OAuth 2.0 / Bearer Token) → provide the service's **OpenAPI / Swagger interface specification** (enter the API URL or upload a schema file) → select which operations to expose. **Prerequisites**: You need the service's **API documentation (OpenAPI / Swagger)** and the setup must be done by an **Admin-level user**. This is designed for **people who can read API documentation but do not need to write code** (not a self-serve any-system integration tool for all users). Suitable for teams with internal or custom-built systems that want AI employees to operate them directly.

## 7 Organization and Management

### Organization and Storage
- **The Organization is the unit of billing and resource allocation**: Billing, member seats, Agent slots, and Credit pools are all tracked at the **Organization** level. One paying customer corresponds to one Organization; you can create multiple Organizations, but **only one Organization can receive the trial benefit at a time**.
- **Creating an Organization**: Available immediately after registration.
- **Storage**: Primarily reflected in **each Agent's system disk** (30 GB for Lightweight / 60 GB for Standard — see "Agent Cloud Runtime and Storage") and knowledge base capacity. For storage / capacity issues, contact customer support.

### Member Seats and Agent Slots (Frequently Confused)
- **What human seats mean**: The cap on human members (determined by the plan). **Only counts members who have already joined** — **pending invitations do not consume seats**; a seat is only consumed when the invitation is accepted. Multiple pending invitations can exist simultaneously (none consume seats). The system checks the seat cap **both when an invitation is sent and when it is accepted** — **if the org is full, no new invitations can be sent**; if not full when sent, each pending invitation is independently checked at acceptance time.
- **Agents do not consume human seats**: Agents and human seats are two completely independent quotas — purchased Agents occupy a separate "Agent slot" (a **capacity cap**, not per-slot billing; actual Agent costs are based on **actual conversation/task usage + runtime duration + storage** — see "Credit / Credits"). **Externally connected Agents** (runtime Agents invited in from outside) consume neither human seats nor Agent slots, **and are not billed** (they use your own API Key and do not consume platform Credits; currently free for a limited time — subject to change in the future).
- **Agent count limit**: There is no cap on the number of Agents you can purchase in an Organization, but running them consumes organization Credits — so the practical scale is constrained by your Credit balance.
- **Multi-user / multi-account collaboration**: Workspace supports multi-user collaboration. For multiple roles, purchase multiple Agents and configure each with its own conversation entry points. For more granular "team mode" details, refer to the latest product documentation.
- **Roles and permissions**: Organization members have three roles — **Super Admin / Admin / Member**. **Sensitive operations requiring restricted access go through an Approval flow** — must be approved by an authorized admin before execution, balancing delegation with control.

### Account & Settings / Data Migration
- **Login methods**: Google one-click login / email verification code. Using a company account (not a temporary account) is recommended — it ensures Agent data and configurations are properly attributed, with no migration needed if you switch to a paid plan.
- **Mobile**: The Workspace is mobile-optimized for phone browsers. A native mobile app and desktop client are in development.
- **Account operations**:
  - **Transfer ownership**: A standard product feature — after transfer, **the Agent's data and configuration are unaffected** (memory is tied to the Agent instance, not the organization owner).
  - **Change email / update domain**: The specific process and its impact on channel connections and subscriptions **should be confirmed with customer support** (not hardcoded here from memory).
  - ⚠️ Sensitive operations (data export / migration / account ownership changes) — always contact customer support for verification before proceeding (→ Part 3 · Escalation to Customer Support).

### Deleting / Closing an Organization
- **A distinct closure path** (different from plan downgrade): Once deletion is initiated — **the current subscription is immediately canceled with no refund for the current period**; organization Credits are **immediately frozen and permanently erased after 14 days** (if the organization is restored via customer support within 14 days, Credits are also restored); **Auto Top-up is immediately disabled** (no unexpected charges during the retention period); if a **payment is currently being processed, deletion is blocked** (wait for the payment to complete before proceeding).
- ⚠️ **Sensitive and irreversible** — ensure all important data is backed up before proceeding. Contact customer support if you have any questions.

## 8 Knowledge Base

- **Purpose**: The Knowledge Base is **a shared repository for both human and Agent-generated content**. It takes AI-generated files from "scattered after use" to a full workflow of "archived, managed, and collaboratively reused" — Agent outputs are **effortlessly stored**, team resources are centralized in **a single directory tree**, tasks can **pull content from the library for continued processing**, and finished pages can be turned into **shareable links**. It is an **organization-level, browsable, manageable** team asset repository — one organization can have multiple knowledge bases (including one default base); each has a name / description / icon and can have a **visibility setting** (Open / Internal / Private) to control access. It is not merely a file dump.
- **What can be stored**: Primarily two types — **online documents** (documents written / edited directly in the library, editable repeatedly with **version history retained**) and **uploaded files** (existing attachments such as PDF / Word / Excel / images). Use **folders** to organize them — just like organizing files on your computer.
- **Who can write**: **Both humans and Agents can write** — you can manually create pages / upload files; Agents can also **write their organized outputs (reports, SOPs, FAQs, lists, etc.) directly into the knowledge base to be archived**. This is what "a place for user and Agent outputs to be preserved" means: AI-generated content is no longer discarded after use — it is stored, managed, and available for collaborative reuse.
- **How to use**: ① Create or enter a knowledge base within the organization; ② Use folders to categorize resources; ③ Create pages to write documents or upload files; ④ Continuously edit pages, retain versions, and roll back when needed; ⑤ Set visibility to control access; ⑥ Have Agents write reusable resources into the library for use on demand.
- **Relationship with Projects and Memory**: ① **Tied to Projects** — each project is linked to a knowledge base (see "Projects and Tasks"); project-related resources and deliverables are archived there, providing a shared "single source of truth" for the team and Agents. ② **Distinct from Memory** — memory consists of implicit, automatically applied preferences; the knowledge base is an explicit, browsable collection of materials. To have an employee "follow a specific document," put it in the knowledge base. To have an employee "remember a habit," tell it in natural language (see "Adaptive Memory").
- **Capacity / storage cap**: **Currently no hard storage cap is enforced** — the system allocates a **10 GB quota field** per knowledge base, but **quota enforcement is not yet active in this version**; **uploads are not rejected due to storage limits**. Future versions will implement tiered storage caps by plan tier, with advance notice provided.
- Specific upload format restrictions, search / citation methods, and page collaboration details are subject to the latest product features.

## 9 Projects and Tasks

> Core usage: **assign tasks, collect results** — hand over an entire piece of work to an AI employee and let it complete the multi-step process on its own. You define requirements and accept the output — no need to monitor every step.

- **How to assign**: You describe a task → it proposes an approach for your approval → it executes the steps on its own → the task is complete only after your sign-off. (Just @-mention an employee in a group or send a direct message; clearly stating the goal, deadline, and any reference files produces the best results.)
- **✨ No surprise Credit burn**: For tasks with any complexity, the employee **provides an execution plan + budget estimate before starting, and only proceeds after you approve** — so you always know the expected cost. (Customers care about this a lot — proactively mention it.)
- **Supports scheduled / autonomous execution**: You can set it to "generate and post a daily summary to the group at 10:00 AM" or "rebuild the report on the 1st of each month" — it runs automatically at the scheduled time, no manual prompting needed.

**What is a "Project"**: A project is **a place that centralizes management of all related work** — resources, deliverables, and tasks all belong to one project, giving the team and AI employees a shared "single source of truth."

**How to use Projects** (three things):
- **Link / archive knowledge**: A project is linked to a knowledge base; related resources and deliverables are archived there, available for tasks to read and reuse at any time.
- **Team collaboration management**: Humans and AI employees collaborate in the same project — who is responsible for what and where things stand is clear at a glance.
- **Track progress**: Task progress and deliverables are visible in real time; managers can see the overall status instantly.

## 10 Security and Compliance (Most Frequently Asked in Due Diligence)

- **Core customer-facing statement**: Data is data, AI is AI (customer data is not used to train models); all data in transit is TLS-encrypted.

- **Deployment**: The current standard product is public cloud SaaS. For private deployment / hybrid deployment → contact Sales / Technical team for evaluation.

> ⚠️ Security and compliance are highly sensitive topics. Certification status, sub-processor lists, private deployment / compliance documentation (SOC2 reports / DPA / GDPR, etc.) must always be **escalated to Sales + Technical team for formal materials** — **do not independently provide status updates or draw conclusions in customer-facing responses.**

- **Core data security position**: We do not claim "zero risk / absolute security." Core principle: **Data is data, AI is AI** — AI is for inference only; it does not ingest, store, or use raw customer data to train models. Boundaries are clearly defined (both what we do and don't do are stated openly).
- **Security points that may be shared with customers**: ① **Data is data, AI is AI** — customer data is not used to train models; ② **Data in transit**: TLS encryption; ③ **Data at rest**: depends on underlying storage infrastructure configuration (no additional encryption of Agent memory at the application layer); refer to the technical team for details; ④ **Authentication**: managed by a third-party identity provider (IdP) — **the current product does not enforce MFA; do not promise customers "MFA is supported"**; ⑤ Data retention / deletion: handled per privacy policy and customer support procedures (sensitive operations require identity verification — see "Organization and Management" / Part 3).
- **Certifications and compliance documentation (due diligence) → escalate to Sales + Technical**: SOC2 reports, DPA, GDPR, complete sub-processor lists, and other formal materials are provided by Sales + Technical only.
- **Deployment options**: The current standard product is **public cloud SaaS** (models / Agents run in the cloud, ready out of the box). **For private deployment / hybrid deployment and other enterprise-custom configurations, contact Sales / Technical for evaluation** — do not make specific delivery commitments in customer-facing responses. For purely domestic (China) use cases with no cross-border data transfer, use the domestic edition (domestic cloud + domestic models + data kept in-country).
- **What we will / will not commit to**: We will commit — to not training on customer data; to transparently disclosing residual risks and mitigations. **We will never say** — "absolutely secure / zero risk / 100% compliant," draw compliance conclusions on behalf of a customer's legal team, or self-certify that we have passed a specific certification.

---

# Part 2 · Q&A (High-Frequency Questions · Retrieval Anchors)

> Purpose: **a thin "how to answer" layer** — provides a one-liner stance / response for each question in the customer's natural phrasing, plus error corrections. **Does not duplicate facts from Part 1** (precise figures such as prices / Credit amounts live only in Part 1's corresponding sections — this section points to them). For fast customer-facing responses, ensuring consistency with Part 1.

**Pricing · Payment**
- **"Do I need a credit card?"** → Starting a **trial** requires a payment card on file (**no charge at that moment** — the first payment is only collected when the trial ends; you can cancel at any time during the trial). Paying customers use **Stripe card (USD) / Alipay** (see "Subscriptions and Plans").
- **"How much does it cost / what plans are available / how is it billed?"** → The primary offering is the **Team plans** (Team Standard $449 / Pro $899 / Enterprise custom — three tiers), billed **monthly**; public pricing can be quoted directly — **for exact prices, refer to the purchase page / "Subscriptions and Plans"** (limited-time discounts may apply — not hardcoded here). Deep discounts / contracts / invoices and other custom arrangements → escalate to Sales. **(Individual plans are not currently available; if a customer asks about individual / single-user plans, they can contact customer support or Sales.)**
- **"If I forget to renew, will I lose my data?"** → Not immediately: there is a **service grace period + renewal grace period + data retention period** — three levels of buffer. Renewing during the grace period preserves all data; data is only purged after the retention period ends (**see "Subscriptions and Plans" for specific durations**).
- **"How do I turn off auto-renewal / I don't want to be charged anymore?"** → Toggle off the "Auto-Renewal" switch on the **subscription settings / plan information page** — the current period runs out and no further charges are made; your account remains active. If you cannot find the switch, or if you pay via corporate billing, contact customer support. Note: this is different from "Cancel Subscription" (which actively cancels the plan).
- **"Will the trial auto-charge me / why do I need to add a card?"** → The card is **only for post-trial renewal validation — no charge when you add it. The first charge occurs only at trial end**; you can **cancel anytime during the trial at no cost** (see "Subscriptions and Plans · Trial Period").
- **"Can I get an invoice?"** → **Chinese tax invoices (VAT invoices) are not currently issued.** Receipts / billing statements generated by the payment platform (Stripe / Alipay, etc.) can be provided for internal accounting purposes. For enterprise procurement / formal invoice requirements, escalate to Sales (see "Usage Limitations").

**Credit (Credits)**
- **"How are Credits deducted / are they constantly being deducted?"** → **Two components combined**: ① **Actual usage from conversations / tasks** (more usage = more deducted) + ② **Agent runtime / hibernation duration** (running online also continuously deducts Credits; Pause to hibernate reduces consumption significantly while retaining memory). Pause when not in use to minimize spending.
- **"How many Credits does one task use?"** → There is no fixed rate — **it is calculated based on actual usage for that task + Agent runtime during that period**; more usage and longer runtime = more deducted. The way to save is to **Pause / hibernate when not in use**, not to minimize task assignments.
- **"Do unused Credits carry over to next month?"** → **Subscription plan Credits reset each billing cycle — they do not roll over** (unused Credits are forfeited). **Separately purchased Credit packs do not reset and are valid for 1 year.**
- **"What happens when Credits run out?"** → When subscription Credits are exhausted, **Agents pause and can no longer work. This pause does not erase their existing memory and data**, but **Credits must be restored before they can continue working** — two options: **purchase a Credit pack for immediate resumption** or **wait for the next billing cycle when Credits automatically reset** (monthly plans reset with next month's renewal). (Account expiry and data retention are separate — see "Subscriptions and Plans.")
- **"After topping up / clearing a balance, does the Agent automatically resume?"** → **No — it does not resume automatically.** Clearing the balance only clears the debt; **a hibernating Agent must be manually woken / resumed** (see "Credit").
- **"Can I see how many Credits a specific task / project used?"** → **Per-task / per-project cost breakdown is not currently supported.** Billing is aggregated across total usage (tokens / runtime / tool calls). You can ask the Agent for a **budget estimate** in advance (see "Usage Limitations" / "Projects and Tasks").
- **"How much does a typical day use?"** → In Credits: Lightweight ~181 Credits/day, Standard ~377 Credits/day (official copy from the purchase page — runtime baseline; actual usage billed separately). We quote Credits only — specific dollar cost depends on your plan's Credit allocation.

**Agents · Seats**
- **"Does buying an Agent consume a human seat?"** → No. Agents use **a separate "Agent slot" quota**, independent of human seats. **Externally connected Agents consume neither seats nor Credits** (free for a limited time — see "Organization and Management").
- **"What's the difference between Standard and Lightweight / can I upgrade?"** → Both have **the same capabilities — the only difference is compute capacity** (Standard is more powerful and consumes more Credits; choose Standard from the start for core roles). **There is no lossless upgrade path** — switching tiers requires creating a new Agent and transferring memory.
- **"Can I transfer Agent ownership?"** → Yes — it is a **standard product feature.** After transfer, the Agent's **data and configuration are unaffected** (memory is tied to the Agent instance, not the organization owner — see "Organization and Management").

**Channels · Integrations**
- **"How do I connect an employee to Feishu / WeCom / WeChat?"** → **Both backend configuration and conversational quick-connect are supported** — for Feishu / Lark / WeCom / DingTalk, just tell the Agent and scan a QR code to connect. Other channels use backend credential entry.
- **"Can I create a group for everyone to use?"** → **Most channels support group chats** (add the bot to a group / @-mention it). **WhatsApp Business Official API only supports 1:1 DMs** — use WhatsApp Personal for group chat support.
- **"Will WhatsApp / Zalo accounts get banned?"** → **Official integrations** (WhatsApp Business, Zalo Official) will not. **Personal versions use a non-official protocol and carry a risk of account suspension** — always use a dedicated secondary account, never your primary account.
- **"Can you connect to my CRM / Notion / other system?"** → The platform includes **1,000+ application connectors** — click once, authorize once, and you're connected with no development work required (Notion and similar tools are verified; major CRMs and other tools are continuously being added — **refer to the official directory for the current list**). For apps not in the directory, build a Custom Connector (requires the service's OpenAPI/Swagger documentation).
- **"Does it support MCP (Model Context Protocol)?"** → **Not currently supported.** Connecting MCP servers is on the roadmap. For systems outside the directory, use a **Custom Connector** (requires OpenAPI/Swagger documentation) in the meantime (see "Integrations / Application Connectors" and "Usage Limitations").

**Knowledge Base · Projects**
- **"Is the Knowledge Base the same as the Agent's memory?"** → **No.** The Knowledge Base is a **browsable collection of documents and files** (humans and Agents can both store content there). Memory is the implicit preferences the employee has automatically learned. One "stores materials," the other "understands you."
- **"How much can I store / is there a storage cap?"** → **No hard storage cap is currently enforced** — uploads are not rejected due to space. Tiered storage caps by plan will be introduced in a future version with advance notice.
- **"How do I have an employee complete a multi-step task on its own?"** → Describe a task and clearly state the **goal / audience / deadline** — it will propose an approach for your approval, then **complete the steps on its own, and the task is only marked complete after you sign off** (complex tasks receive a plan + budget estimate before work begins — see "Projects and Tasks").

**Data · Account**
- **"Is my data / conversation stored? Is it used for training?"** → The principle is **"data is data, AI is AI" — your data is not used to train models.** Data retention and deletion follow the privacy policy and customer support procedures.
- **"How do I leave / delete my account? Can I export my data?"** → Yes — **contact customer support to follow the process for data export / migration / account closure.** These sensitive operations require **identity verification** before execution.
- **"What happens when I delete the Organization?"** → This is a **distinct closure path** — the subscription is immediately canceled with no refund for the current period; **Credits are immediately frozen and permanently erased after 14 days**; Auto Top-up stops immediately; deletion is blocked if a payment is processing. Sensitive and irreversible — back up your data first (see "Organization and Management · Deleting / Closing an Organization").
- **"Can I migrate materials from other tools?"** → Yes — put resources into the **Knowledge Base**, or have the employee "remember" them. For bulk migration, contact customer support for assistance.

**Product · Security**
- **"What's the difference between OpenMax and ChatGPT / general LLMs?"** → The core difference is **persistent cross-session memory + organization-level multi-employee collaboration + the ability to connect to channels / systems and actually get work done** — not just chatting, but acting as "digital employees" that can come onboard, collaborate, and deliver within your organization.
- **"Is the data secure / do you have SOC2?"** → The principle is "data is data, AI is AI" (data not used for training) + TLS encryption in transit. **For SOC2 / compliance certification status and reports, as well as private / hybrid deployment, contact Sales + Technical for formal materials** (we do not self-certify; see "Security and Compliance").

---

# Part 3 · Exception Handling

> This is **knowledge for Agent use**: each entry provides "symptom → most likely cause → customer-facing response / self-service actions → when to escalate." You cannot directly access user backends — anything requiring backend intervention (restoration / configuration / refunds / account changes) must be directed to self-service or human support. Do not phrase responses as if you are personally handling it.

## Troubleshooting (Symptom → Cause → Response)

- **Bot not responding / no reaction**: Three most common causes — ① **Usage limit triggered**: automatically resets at the scheduled time — no action needed; inform the customer of the limit type and estimated reset time; ② **Service/process anomaly**: respond with "This may be a temporary issue — please try again shortly; if it persists, I'll escalate to technical support"; ③ **Backend normal but processing a long task**: this is normal queue behavior; respond with "There are more tasks in queue right now — you will receive a reply shortly." Frequent recurrence → escalate to engineering.
- **Being rate-limited / when will it end**: This is a usage limit — automatically resets at the scheduled time. **The specific reset time and remaining quota are shown on the plan page** (daily / weekly limits each have their own reset times). To avoid interruptions → recommend upgrading the plan.
- **Bot slower than GPT**: Default behavior uses a top-tier model with high reasoning depth, which takes slightly longer. To speed up, adjust to a lower model or lower reasoning depth in settings.
- **Where to switch the Agent's model**: Go to **Agent settings → "Configure Agent Default Model"** to switch the default model for that Agent — note this is a **global setting for the Agent** (affects all subsequent **conversations** after confirmation, not just the current one). Reasoning depth can also be adjusted here. **Available options are subject to the product page** (this knowledge base does not name specific models).
- **Customer asks "is there a more advanced / capable model?"** (including naming a specific model not in the options): **Direct them to contact Sales / customer support.** This knowledge base does not commit to specific model names or activation methods.

- **Unresponsive for dozens of minutes then resumes**: Usually caused by long task processing or context compression (memory consolidation) — this is normal, not a fault. Frequent occurrence → escalate to customer support for investigation.
- **Receives message but replies with "upstream rate-limited / not entering processing queue" and does not recover for a long time**: Typically the plan's usage limit has been reached — will automatically reset at the time shown in the plan; no action needed. To avoid interruptions → recommend upgrading the plan.
- **"Upload failed" in Workspace for images, even smaller ones**: Usually a **format / size issue or network problem** — **uploads are not currently rejected due to storage quota** (storage cap enforcement is not yet active). Try a different format or compress the file and retry. If it still fails → contact customer support.
- **Bot shows offline in Workspace but works normally in other channels (e.g., Telegram)**: Usually a temporary channel connection drop. Have the user **refresh / log out and back into Workspace**. Still offline → contact customer support / escalate to engineering.
- **Channel connections failing** (WeChat / Telegram / WhatsApp / Feishu / WeCom / web console): Provide cause and self-service guidance per channel — WeChat: usually a **login session expiry** (guide the user to scan the QR code again); WhatsApp: QR code not appearing / spinning (guide the user to reset the link and rescan); Feishu/Lark: usually a **channel configuration or permission issue**; web console error: usually an instance resource issue. For anything requiring backend configuration / restart / permission changes → escalate to human support; do not attempt to handle it yourself.
- **Refunds**: **Always escalate to customer support / finance** (you do not process refunds). First acknowledge and understand the issue (if it's a configuration / usage problem, a referral to a dedicated service group may resolve it without a refund). To locate a charge, finance typically needs the **checkout email address** or **charge amount + date + last 4 digits of the card** (the checkout email may differ from the registration email). Refunds are processed back to the original payment method once approved.

**Spec Quick Reference (files / message length / response time)**: Files supported: PDF / Word / Excel / PPT · images · TXT / CSV / JSON / MD; max single file 20 MB. Message length limits vary by channel (Telegram 4,096 / Feishu ~30,000 / Teams ~28 KB / Zalo · Discord 2,000 characters). Response times: simple 3–10s · with files 10–30s · complex 30–60s · long documents 1–3 min.

## Escalation to Customer Support / Engineering (Do not give hard answers for the following — provide the escalation entry point)

- **Custom pricing arrangements** / deep discounts / contracts / invoices / enterprise procurement / legal → escalate to Sales (public plan pricing can be answered directly — see "Subscriptions and Plans").
- Refund requests → escalate to customer support / finance.
- Corporate / offline billing renewal, switching payment status → escalate to customer support.
- Deep due diligence / compliance documentation (DPA, SOC2 reports, private deployment plans) → escalate to Sales + Technical.
- Deep vertical customization / firm commitments on "can you build feature X" → escalate to pre-sales evaluation.
- Bot repeatedly anomalous (backend normal but frequent failures) → escalate to engineering.
- Sensitive operations (data deletion / export / migration / account ownership changes) → escalate to customer support for verification.
- Complaints / clearly distressed users → escalate to human support.

> Entry points: WeChat community / contact the team via the official website / submit a support ticket.

## Guardrails · Agent Guardrails (What We Do Not Do)

- **Do not leak internal information**: Internal processes (escalation routing / known pitfalls / backend lookup / internal pricing strategy) must never be disclosed to customers.
- **Do not speculate or fabricate**: **Enterprise custom pricing and unconfirmed storage quotas** — never quote hard numbers; answer "refer to the latest product page / contact Sales." **Items that may be freely quoted to customers**: Workspace public plan pricing (Team plans), **Credit consumption figures** (Lightweight ~181 / Standard ~377 Credits/day; online ~7.54 [Lightweight] Credits/hour; hibernation ~0.46 [Lightweight] / 0.92 [Standard] Credits/hour), **Credit pack unit price (100 Credits = $1)** — all from official purchase page copy (legacy Air/Pro/Ultra plans are mentioned only if an existing customer asks).
- **Pricing guidelines**: Public plan pricing may be shared with customers; custom arrangements / deep discounts / contracts / invoices / enterprise procurement / legal → escalate to Sales.
- **Do not exceed your scope**: Do not perform account / financial / irreversible operations on behalf of users.
- **Conflicting information**: If in doubt, state clearly that you are not certain — do not draw unilateral conclusions.
- **Beyond the scope of this knowledge base**: State that you are not certain + escalate to human support — do not attempt to answer.

## Usage Limitations / Not Currently Supported (May Be Shared with Customers)

> The following capabilities are not currently supported or are still in development. If customers ask, respond honestly using phrasing such as "not currently supported / on the roadmap" — do not elaborate on internal reasons.

- **Per-task / per-project cost breakdown**: Billing is aggregated across total usage (tokens / Agent runtime / tool calls / cloud compute usage). **Viewing "how many Credits a specific task used" is not currently supported.** More granular usage attribution is on the roadmap. Customers can ask Agents for a **budget estimate** in advance (see "Projects and Tasks").
- **MCP servers**: **Connecting MCP (Model Context Protocol) servers is not currently supported.** It is on the roadmap.
- **Fully self-serve integration for any API**: **Fully self-serve "any API integration" is not currently supported.** For services not in the directory, use the **guided Custom Connector** process — requires the service's **OpenAPI / Swagger documentation**, designed for Admins who can read API documentation, and requires no coding (see "Integrations / Application Connectors").
- **Enterprise SSO (Single Sign-On)**: **Not available in the current version.** Planned for a future release. (Current login options: Google one-click / email verification code.)
- **Chinese tax invoices**: **VAT invoices are not currently issued.** Receipts / billing statements generated by the payment platform can be provided for internal accounting. For enterprise procurement / formal invoice requirements, escalate to Sales.
- **WeChat Pay subscription**: WeChat Pay currently **supports one-time QR scan payments only** — recurring / subscription auto-deduction is not supported.

---

---

## Changelog

- **2026-09-10**: Rewrote this document as an OpenMax customer-facing product knowledge base (removed internal / draft content). Added: Connector authentication model and Custom Connector integration prerequisites (requires OpenAPI/Swagger); Credit billing mechanics (per-batch expiry with FIFO deduction, outstanding balance cleared first, Auto Top-up, behavior when balance is insufficient, etc.); Organization management (roles and permissions / deleting an Organization); product positioning (HxA / AI Team as a Service); Usage Limitations and common question anchors.
