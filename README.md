# The Reshuffle Room 🂡

A single-deck blackjack trainer that **reshuffles a fresh 52-card deck before every hand** — so card counting is useless — with a built-in coach that tells you the mathematically correct move (hit / stand / double / split) and *why*.

Just open `index.html` in any browser. No build step, no dependencies.

## Features

- **Fresh shuffle every hand.** A full Fisher–Yates shuffle of all 52 cards before each deal. The running count is always neutral, so there's nothing to count.
- **Live strategy coach.** For every decision the coach shows the correct basic-strategy play against the dealer's up-card, with a plain-English reason. The recommended button is tagged **Best**.
- **Grades your play.** Deviate from the book and it tells you what the correct move was and why; a running **strategy accuracy** stat tracks how often you nail it. Toggle the coach off to test yourself.
- **Real rules.** Dealer stands on all 17s, blackjack pays 3:2, double on any first two cards, double after split, split up to four hands. No insurance (it's a sucker bet).
- **Chips, bankroll, keyboard shortcuts** (`H`it, `S`tand, `D`ouble, s`P`lit), and light/dark friendly styling.

## The strategy engine

`strategy()` implements standard basic strategy (dealer stands on soft 17, doubling after split allowed) for hard totals, soft totals, and pairs — returning both the optimal action and an explanation. It never looks at the dealer's hole card; it works from the same information you have.

Play money only — this is a trainer, not a casino.
