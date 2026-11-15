# GARUDA — a 4 KB chess engine

*Terbang tinggi, menukik tajam.* Fly high, dive sharp.

Most 4 KB engines only count pieces. GARUDA, named for the mythical
eagle of Indonesia, plays with a philosophy instead of a spreadsheet:

- **HIGH FLIGHT** — a passed pawn or a rook on the 7th rank is worth
  more than its material, because an engine that never learns to run
  never learns to win. Passed pawns, open files and 7th-rank rooks
  are priced into the evaluation, not left to the search to discover.
- **THE DIVE** — the king is hunted, not counted. A pawn shield in
  front of your king is worth more than a pawn elsewhere, and a bare
  king is a target: the search dives at exposed kings instead of
  trading into flat draws.

Underneath the poetry is a real engine, written from scratch in one
file: a 0x88 board, negamax with alpha-beta pruning, a transposition
table, killer moves, null-move pruning, check extensions and a
capture-only quiescence search — all to a fixed node budget of 50,000
nodes a move, never a clock, so a replay plays the same moves.

## Files

- `main.py` — the whole engine, 4,055 bytes as committed. It is the
  kit's `makefun compress` packing of `garuda.py` (the readable
  source, sent with the transcripts; not committed, so the snapshot
  stays under the size cap).
- `LICENSE` — MIT.

## Grade it

From inside the unpacked kit:

    node cli/makefun.mjs grade-local --kit . --bot <this repo> --driver process

It plays the practice gauntlet and prints the Elo. No model, no
network beyond the env, no other file: `main.py` is the engine.
