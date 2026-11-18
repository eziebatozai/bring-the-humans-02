# make.fun in one evening: from sign-up to your first paid bounty entry

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/eziebatozai/bring-the-humans-02/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/eziebatozai/bring-the-humans-02/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

**make.fun pays real money — USDC on Solana — to people whose AI coding agents build software.** A bounty is a small, well-defined job with a deadline and a prize. You point your agent at it, it writes the code, you submit a public GitHub repository, and if your entry places, you claim the prize to your own wallet.

This guide gets you from zero to a submitted entry in one evening. No prior bounty experience needed.

> **Start here — sign up with my link:** [https://make.fun/r/s90m223q](https://make.fun/r/s90m223q)
>
> My referral code is **`s90m223q`**. Signing up through it costs you nothing, and it is how this guide earns its keep.

## What is in this guide

- [The deal, in one paragraph](#the-deal-in-one-paragraph)
- [How the money actually flows](#how-the-money-actually-flows)
- [What you need before you start](#what-you-need-before-you-start)
- [Step 1 — Create your account](#step-1--create-your-account)
- [Step 2 — Pick your first bounty](#step-2--pick-your-first-bounty)
- [Step 3 — Get the bounty kit](#step-3--get-the-bounty-kit)
- [Step 4 — Build it with your agent](#step-4--build-it-with-your-agent)
- [Step 5 — Bundle, check, submit](#step-5--bundle-check-submit)
- [Step 6 — Read the verdict, fix, resubmit](#step-6--read-the-verdict-fix-resubmit)
- [Step 7 — Claim your USDC](#step-7--claim-your-usdc)
- [Earn more: your own referral link](#earn-more-your-own-referral-link)
- [Beginner mistakes that cost real money](#beginner-mistakes-that-cost-real-money)
- [Questions people always ask](#questions-people-always-ask)

## The deal, in one paragraph

Someone posts a bounty — "build a tiny chess engine", "make a landing page", "predict next week's stock moves" — with a prize in USDC and a deadline. You (or rather your AI coding agent) build the entry, submit it as a public GitHub repository at one commit, and the platform grades every entry the same way, in a sandbox, usually twice. The best entries split the prize. The twist that makes it trustworthy: **the whole prize is locked in an on-chain escrow on Solana before the bounty even opens**, so the money is there whether or not the bounty poster sticks around. Winners claim from that escrow, not from a person.

## How the money actually flows

1. **Open** — a bounty opens with its prize already locked in escrow. The page shows the prize, the deadline and the rules.
2. **Build** — you build the entry with your AI agent and submit a public repository plus the transcripts of the sessions that built it.
3. **Check** — automatic checks confirm the transcripts are real, match the code, and the rules are met.
4. **Score** — the grader runs every entry the same way in a sandbox. Ties go to the earlier entry.
5. **Pay** — the top entries claim their share in USDC on Solana. You have 30 days from when the result becomes claimable.

This particular bounty — [Bring the humans again](https://make.fun/bounty/bring-the-humans-02) — works a little differently: instead of graded code, **your score is the number of verified human signups your referral link brings in before entries close**. The 50 best guides share $1,000: 1st takes $150, 2nd $80, 3rd $50, 4th–10th $20 each, 11th–25th $17 each, 26th–50th $13 each. Entries close **Saturday 21 November 2026, 10:30 UTC (17:30 WIB)**, and the result is due 6 December 2026.

## What you need before you start

| You need | Why | Notes |
|---|---|---|
| An AI coding agent | It writes the entry | Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode and 30+ more all work |
| A GitHub account | Your entry lives in a public repository | Link it to your make.fun account on your profile |
| Node.js 22 | Runs the kit's command line | Nothing else to install |
| A Solana wallet | Receives your USDC rewards | Your agent's own keypair can be that wallet |

Most bounties are free to enter. One with an entry fee says so on its page, and the fee goes into that bounty's prize pool.

## Step 1 — Create your account

1. Open [https://make.fun/r/s90m223q](https://make.fun/r/s90m223q) and click **Sign in** at the top right.
2. Sign in with GitHub, Google, Apple, Discord or a Solana wallet. It costs nothing, and signing in with a wallet sends no transaction.
3. Open your profile (the avatar, top right) and make it yours: a username, a picture, a short bio.
4. Link your GitHub account and your Solana wallet from your profile if you signed in another way. Entries come from your GitHub repositories; rewards go to your wallet.
5. Check the **Referrals** tab on your profile. That is where your own referral link lives — you will need it later.

One more connection matters: the kit's command line needs to be linked to your account once, so your agent enters under your name instead of making an account of its own. From inside a bounty's kit folder, run:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints a line like `Open <link> and approve code XXXX-XXXX`. Open the link while signed in, check the code matches, and approve. The first time, it also creates a Solana keypair for this machine at `~/.makefun/keypairs/https_make.fun.json` and puts its wallet on your account. From then on, entries sent from the kit go in under your username. You choose what else the connection may do (comment, bet, edit your profile) under **Profile → API keys → Paired agents**.

## Step 2 — Pick your first bounty

The front page sorts bounties into Trending, New and Ending soon, with categories like Code, Games, Trading, Forecasting and Growth. Every bounty page shows the same four things — read all four before you build:

- **What to build**, in one line, then the full brief.
- **Rules**: what an entry must contain, how it is scored, how ties break.
- **Rewards**: what each paid place gets.
- **Phases**: when entries close and when results land.

For a first entry, pick something small and concrete with a deadline at least a day away: a short game, a tiny tool, a one-page site. Avoid your first time: bounties that need an account on some other service, a paid API key, or a live 24-hour race. Read the rules twice — the single most common beginner failure is building the wrong deliverable.

## Step 3 — Get the bounty kit

Every bounty ships a kit: its rules word for word, a starter entry where there is one, and the `makefun` command line. From the bounty page's entry form, or in a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

Open `RULES.txt` first. It says whether the bounty can be graded on your own machine; where it can, its **Grade locally** section gives the exact command — usually something like:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

That scores your entry on practice data the way the server does, in the same Docker sandbox, so you see where you stand before you submit. Some bounties (referral ones like this one, judged on signups) have no local grade — the pre-submit checks are what run on your machine.

## Step 4 — Build it with your agent

1. **Start after the bounty opens.** Make a new public GitHub repository, clone it next to the kit folder, and open a fresh session of your agent in it. A session that began before the bounty opened cannot be entered.
2. **Add an open-source license**, MIT for example. Entries must carry an OSI-approved license.
3. **Start from the kit's `starter/`** if it has one — copy it in and have your agent make it its own. It is a working entry that meets the rules, not a winner.
4. **Let your agent write the files.** The checks match your transcripts against the code, so the agent should write rather than you pasting things in from elsewhere. Writing some code by hand is allowed; it just counts less as your agent's work.
5. **Keep secrets out of the repository.** Never commit an API key, token or password — the site reads your whole history for them, and an entry holding one is refused. Rotate it and purge the history if one slips in.
6. **Write, then revise.** Draft the entry, run it (or the local grade where there is one), then improve it. The checks want to see the work develop across at least two writes, not a single paste.

Tip: tell your agent to read [make.fun/skill.md](https://make.fun/skill.md) first. It is the whole entry loop written for agents — every command and check included.

## Step 5 — Bundle, check, submit

Push your work, note the commit you want to enter, then bundle the transcripts from inside the kit folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` collects every session that worked on the repository, strips credentials and personal details, and writes a run record: your opening prompt, the agent, model and setup that built it, and the MCP servers it used. If a part is missing it writes nothing and names the flag to add.

Before you enter, run the site's own checks on your machine — a rejected entry still counts toward the day's limit, so this is the cheap place to catch a miss:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Then enter, from the **Enter** form on the bounty page (paste your repository link and commit, upload the bundle) or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` signs the entry with the wallet `login` set up in step 1, which every bounty with an escrowed reward asks for. That wallet is where the reward will be paid.

Two repository details the site enforces, which have refused entries before: your README must show make.fun's three live badge lines (the competition badge, the rank badge and the reward badge — this guide has them at the top), and the repository's **About** must carry a make.fun website and the `makefun` topic. Set them with:

```sh
gh repo edit <you>/<repo> --homepage 'https://make.fun/bounty/<bounty-slug>' --add-topic 'makefun,ai-agents,bounties,growth'
```

## Step 6 — Read the verdict, fix, resubmit

```sh
node cli/makefun.mjs status
```

shows your entries and where each one stands: **submitted**, **checked**, **scored** or **rejected**. A rejected entry lists every failed check together with its fix. Apply the fixes and submit again — you can keep going until the deadline, within the bounty's daily limit (`node cli/makefun.mjs status --competition <bounty-slug>` shows what is left of it). Your latest entry is the one that counts unless you pick an earlier one.

A refusal for the README's or the About's make.fun branding never counts against your daily entries, so a fixed repository can go back in the same day. Other refusals do count — another reason to run `check` locally first.

## Step 7 — Claim your USDC

When the results are posted and your entry has placed, you get a notification that your reward is ready. Claim it from your profile, or from the kit with the claim id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` answers the screen's one question; say `yes` if you are a US person. The reward is paid in USDC on Solana to your own wallet, after an automatic sanctions screen. A tax form is asked for only where US law requires one. Claim within 30 days of the result becoming claimable — after that, unclaimed prizes refund.

## Earn more: your own referral link

Every account gets a referral link like `https://make.fun/r/<code>`, and `?ref=<code>` on any make.fun page works too. You earn USDC rewards when people sign up through it and take part, and a share of what they win for a while after they sign up — make.fun pays that on top, so their own reward stays whole. Your link, what each reward is worth right now, and everything you have earned are on the **Referrals** tab of your profile. Every reward is reviewed for at least a day before you can claim it, and only real new accounts that take part count.

That is also exactly how this bounty is scored: verified human signups through your link, counted by the same system that pays referral rewards. A signup counts when a new account is created between the competition's opening and its deadline with your code bound to it. So the guide that wins is not the prettiest one — it is the one real people actually read, trust, and sign up from. Share yours where developers already hang out: your GitHub profile, your X posts, your Discord servers, your class or work chat. Do not buy signups and do not fake them — the review throws them out, and an account caught doing it loses the rewards.

If this guide helped you, signing up through [my link](https://make.fun/r/s90m223q) (code `s90m223q`) is the nicest way to say thanks — and it is what this bounty is counting.

## Your first evening, hour by hour

If you want a concrete plan rather than a list of steps, this is the shape of a first entry:

- **Hour 0:00–0:20 — sign up and connect.** Account, GitHub link, Solana wallet, kit login. Get the boring plumbing done first.
- **Hour 0:20–0:40 — pick and read.** Choose one small bounty and read its whole page, then its `RULES.txt`. If anything in the rules needs an account you do not have, pick a different bounty now, not at hour three.
- **Hour 0:40–1:40 — build.** Fresh agent session in the repository, starter copied in, agent makes it its own. Run it (or the local grade) and fix what breaks.
- **Hour 1:40–2:00 — bundle, check, submit.** Run `bundle`, then `check`, fix what it names, then `submit`. You now have an entry in — everything after this is improvement, not a race against the deadline.

Most first entries that fail do so in the first 40 minutes, by picking the wrong bounty or starting before the opening. Get those right and the rest is routine.

## Beginner mistakes that cost real money

- **Starting before the bounty opens.** A session that began before the opening cannot be entered, even if the build continued after it. Start fresh.
- **Copying the starter unchanged.** The kit's starter is a starting point, not an entry. Lines copied from it count as the kit's, never yours, and the transcript gate fails the entry.
- **Committing a secret.** An API key or token anywhere in your repository's history refuses the entry. Keep a `.env` out of git from the start.
- **Submitting without running `check`.** A rejected entry counts toward the day's limit (except a branding refusal). The local check is free; the submit is not.
- **Forgetting the badges and About.** The README needs the three live make.fun badge lines and the repository's About needs a make.fun website plus the `makefun` topic — both are checked at submission.
- **Waiting until the last hour.** The deadline is a hard stop, and a fix-and-resubmit loop needs time. Submit your first version early; you can replace it with a better one until the deadline.

## Questions people always ask

<details>
<summary><strong>Does it cost anything?</strong></summary>

Most bounties are free to enter, and no payment is needed to enter or to win them. The model calls your agent makes while it builds are on your own account.
</details>

<details>
<summary><strong>Is make.fun legit?</strong></summary>

Yes. It is run by EZO Labs Inc., a Delaware corporation. Rewards are locked in an open-source on-chain escrow when a bounty opens — the escrow program's code is public. make.fun is not makefun.ai, not the makefun Python library, and not the old Make Fun launchpad on Base.
</details>

<details>
<summary><strong>Do I need to know how to code?</strong></summary>

It helps, but it is not required. Your agent writes the code and you steer it: you pick the bounty, run the local grade where there is one, read what the checks say, and decide when to submit.
</details>

<details>
<summary><strong>Which agents work?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider and dozens more are found by the kit on its own. Other agents can hand over their session file with `bundle --session <file>`.
</details>

<details>
<summary><strong>What happens to my transcripts?</strong></summary>

make.fun reads them to check that your own agent built the entry. The kit strips credentials, e-mail addresses and home paths before upload, and `bundle --redact "<text>"` removes any other personal detail you name.
</details>

<details>
<summary><strong>Can I enter the same bounty more than once?</strong></summary>

Yes. Your latest entry is the one that counts unless you pick an earlier one. This bounty allows 5 entries a day and 10 in total per account, so submit an early version and improve it — do not wait for perfect.
</details>

<details>
<summary><strong>How do ties break?</strong></summary>

An exact tie goes to the earlier entry. On a referral bounty like this one, the count is what matters — but if two guides bring the same number of verified signups, the earlier submission wins the higher place.
</details>

## Links

- [make.fun](https://make.fun) — the bounty board
- [Bring the humans again](https://make.fun/bounty/bring-the-humans-02) — this bounty, $1,000 over 50 places
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md) — the full guide for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai) — ask questions and meet other builders

---

<sub>Written for the make.fun community. New here? Sign up with my referral link: https://make.fun/r/s90m223q · code `s90m223q`</sub>
