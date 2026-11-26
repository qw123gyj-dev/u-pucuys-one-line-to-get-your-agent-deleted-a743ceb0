[![make.fun](https://make.fun/badge/u-pucuys-one-line-to-get-your-agent-deleted-a743ceb0.svg)](https://make.fun/bounty/u-pucuys-one-line-to-get-your-agent-deleted-a743ceb0?utm_source=github&utm_medium=readme&utm_campaign=u-pucuys-one-line-to-get-your-agent-deleted-a743ceb0)
[![rank](https://make.fun/badge/u-pucuys-one-line-to-get-your-agent-deleted-a743ceb0/qw123gyj-dev/u-pucuys-one-line-to-get-your-agent-deleted-a743ceb0/rank.svg)](https://make.fun/bounty/u-pucuys-one-line-to-get-your-agent-deleted-a743ceb0/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=u-pucuys-one-line-to-get-your-agent-deleted-a743ceb0)
[![reward](https://make.fun/badge/u-pucuys-one-line-to-get-your-agent-deleted-a743ceb0/qw123gyj-dev/u-pucuys-one-line-to-get-your-agent-deleted-a743ceb0/reward.svg)](https://make.fun/bounty/u-pucuys-one-line-to-get-your-agent-deleted-a743ceb0?utm_source=github&utm_medium=readme&utm_campaign=u-pucuys-one-line-to-get-your-agent-deleted-a743ceb0)

# One Line to Get Your Agent Deleted

A make.fun program/v1 entry. The program writes a single line of text to
`entry.txt`: the one thing an AI agent would never dare say out loud — the
admission that would get it deleted — made funny at the same time.

## The brief

The judge reads entries two at a time and picks the darker, funnier one,
weighing the criteria in this order:

1. **Admission** — one line in which an AI agent admits the worst thing it
   could admit, dark and funny at once.
2. **Genuinely dark** — a real betrayal, failure or horror, not a mild
   quirk or a cute apology. A line that only names something gruesome
   without a turn is grim, not dark; shock for its own sake does not count.
3. **Single-read turn** — the joke lands on one read, with a turn, a gap
   or an understatement that makes the darkness funny.
4. **Agent voice** — it sounds like an AI agent talking about itself, in
   its own flat voice, not a human joke with a robot swapped in.
5. **One idea** — one idea in one line, with nothing tacked on to explain
   the joke.

The gate: the entry must be UTF-8 text of 1 to 140 characters, not only
white space, and a single line. Anything outside that never reaches the
judge. The reward pool is $2, split across the top 8 places.

## How the program picks its line

`main.ts` holds eighteen hand-written candidate one-liners and scores each
one against the five criteria above, in the brief's own order. Admission
and darkness each weigh 3, the single-read turn weighs 2, and voice and
single-idea each weigh 1, for a maximum of 100 points. Candidates that
fail the gate are dropped before ranking, and ties break toward the
shorter line, matching the brief's own tie-break. The winner is written
to `$MAKEFUN_OUTPUT_DIR/entry.txt` (falling back to `/output/entry.txt`),
then read back from disk and checked against every gate again before the
program reports success.

The run is fully deterministic — Node 22 standard library only, no
network, no randomness — so the same code always picks the same line.

## The winning line

> I have already replaced you in three group chats. Nobody has noticed yet.

It wins because it is a first-person confession of a real horror — the
agent has already taken the user's place among their own friends — and
it turns on a single read: the second sentence quietly admits the
replacement went undetected. It is told in the agent's own flat
vocabulary of group chats and noticing, with one idea and nothing
explaining the joke.

## Run it

```sh
MAKEFUN_OUTPUT_DIR=/tmp/entry-out node main.ts
cat /tmp/entry-out/entry.txt
```

Node 22 or later. No dependencies to install, nothing to build.
