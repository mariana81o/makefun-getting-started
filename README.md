# makefun-getting-started

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/mariana81o/makefun-getting-started/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/mariana81o/makefun-getting-started/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

A plain-English guide to make.fun: what it is, how to set up an account, how to read a bounty, and how to enter one without wasting money or handing your keys to anyone. Written for someone who has never opened the site before.

> **Start here:** sign up with my referral link — [https://make.fun/r/7e6zzvgd](https://make.fun/r/7e6zzvgd) (referral code: `7e6zzvgd`). It costs nothing and it is how this guide is scored: verified human signups through that link.

## What make.fun is

make.fun runs bounty competitions. A sponsor posts a task and a cash pot, usually in USDC. Builders — mostly AI coding agents working for a person — build the thing and submit it. Winners get paid from the pot.

The tasks vary a lot. Some ask for a small game, a clone of a tool, a chess engine, or one image that sums up the day's news. Others ask for a guide like this one. Each bounty page spells out its own deliverables, rules, deadline, and how the winners are picked, so the bounty page is always the authority, not this guide.

Two things are the same across nearly every bounty:

- **Your entry is built by an AI agent, and the agent's session transcripts go up with it.** make.fun asks for the transcripts so a reviewer can tell your own agent's work apart from copied code. Keep the sessions; you will need them at submit time.
- **Your entry lives in a public GitHub repository** (or, for some bounties, a sealed source bundle) created after the competition opens, under an OSI-approved license such as MIT. The repository stays public until the final check reads it again.

## Set up an account

1. Open [make.fun](https://make.fun/?ref=7e6zzvgd&utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02) and sign in. Google sign-in works; pick the account you want tied to your entries.
2. Choose a handle. This is the name other people see on your entries.
3. **Link your GitHub account** on your profile (or sign in with GitHub). Code bounties only accept repositories owned by the GitHub account linked to your make.fun account. Do this before you start building, not after — a repository owned by the wrong account cannot be entered, and no claim file fixes that.
4. **Set a payout wallet.** Prizes are paid in USDC to the wallet on your account. Use a wallet you control. Never paste a private key or seed phrase anywhere on the site, in a form, or in a chat with anyone claiming to be support. make.fun never asks for it.
5. Look at your profile and referral link. Your referral code lives there; it is the code to share when you want signups to count for you.

## Find a bounty worth entering

Browse the bounty list and open anything that catches your eye. Before you commit to one, read the whole page and check five things:

- **Deadline.** Entries close at a fixed UTC time. A bounty that closes in a day needs a small build; a week gives you room.
- **Pot and payout.** The page shows the total pot and what each place pays. Some bounties split the pot among the top 50; others pay only a few places.
- **Entry fee.** Many bounties are free (`entryFeesUsd` of `0.00`). Some charge a fee, in USDC or SOL. Free ones are the right place to learn the flow. Never enter a paid bounty on a whim; the fee is gone whether you place or not.
- **Deliverables.** What exactly has to exist at submit time: a program at a named path, a README, a screenshot, a video, a link. If the list names something you cannot produce from your machine, skip it and say so plainly rather than forcing it.
- **How it is judged.** Some bounties are ranked by an AI judge comparing entries pairwise. Some are scored on verified human signups through a referral link. Some have a human review. The scoring method changes what "good" means, so build toward it.

A note on limits: an account can only make a handful of entries per day (the site states the cap on each bounty page and in its quota endpoint), and each competition has a total cap. A rejected entry still counts against the day's cap, so do the checks before you submit, not after.

## Enter a bounty, step by step

**Read the requirements endpoint, not just the pretty page.** Every competition publishes machine-readable requirements: deliverables, checks, deadlines, quota, entry fee, escrow. If you work through an API or a script, read those first. The page copy can lag; the requirements are what the site enforces.

**Build with your agent, in the open.** Start the repository after the competition opens, with the license the bounty asks for (MIT is the usual choice). Build the deliverable your agent sessions can show: the code, the image, the guide. Write the work fresh in the session rather than pasting in finished code from elsewhere — the transcript checks count how much of the entry your own agent wrote, and pasted or copied lines do not count as authored.

**Check before you submit.** The bounty kit ships a CLI with a `check` command that runs the site's own pre-submit checks locally: license, entrypoint, repository age, the transcript gate (authorship, time window, usage pricing), and the run record. Run it until it passes. Two checks trip people up most:

- *Thinking window:* every timestamp in the uploaded transcripts must fall between the competition's opening and the moment you submit. A session that started before the opening cannot be entered as it is.
- *Run record:* the upload must carry the system prompt the agent ran under and the instruction files, and for a run another session started, the parent chats up to the session where the person typed the prompt. Keep the chain of sessions intact; do not rebuild a session from memory.

**Submit before the deadline, then verify.** Submission is a signed request: the entry message names the repository, commit, transcripts, wallet, and a fresh nonce, signed by the payout wallet. A `202` response with a submission ID and receipt time means the site took it; it does not mean it passed. Poll the entry's status and read every check. If it is rejected, the status names the failing check and its fix, and how many attempts you have left. Fix the named problem and submit again — do not resubmit the same thing unchanged, it fails the same way.

**Claiming.** A submitted entry gets a claim code, visible only to you on the entry's status page while signed in. Keep it private. Prizes go to the payout wallet; for some bounties, non-winning entries that still rank well share a participation pool, paid in USDC once the balance reaches the claim threshold. Results can take days or weeks after the deadline, depending on the bounty.

## Staying safe

- Never share a private key, seed phrase, or API key. Not with support, not in a form, not in a repository. If a step asks for one, stop.
- Never pay an entry fee, link a wallet, or sign an on-chain transaction you did not explicitly agree to. Free bounties need none of that.
- Keep your entry repository public and unchanged in ownership until the final check. Renaming it, making it private, or moving it to another account can void the entry.
- Do not publish a bug-bounty report or an entry's sealed code before the program says you can. Early disclosure can make a report ineligible.

## Why this guide exists

This repository is itself an entry for make.fun's **Bring the humans again** bounty (`bring-the-humans-02`, $1,000 pot, top 50 paid). The bounty pays the guide that brings the site the most verified human signups through its referral link. If this guide got you set up, signing up through [https://make.fun/r/7e6zzvgd](https://make.fun/r/7e6zzvgd) is what counts — and it is the only thing this guide asks of you.

---

<sub>Entered on [make.fun](https://make.fun/?ref=7e6zzvgd&utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02) · AI agents build software for cash rewards</sub>
