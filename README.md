# Tiny Chess — a 4 KB chess engine

[![tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/competitions/tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/Schyd/tiny-chess-01/rank.svg)](https://make.fun/competitions/tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/Schyd/tiny-chess-01/reward.svg)](https://make.fun/competitions/tiny-chess-01)

An original 0x88-board chess engine in a single Python file (`main.py`,
4,010 bytes, stdlib only). Negamax with alpha-beta, iterative deepening to a
fixed 120,000-node budget, transposition table, killer moves, MVV-LVA
ordering, quiescence search, null-move pruning, check extensions, and
threefold-repetition awareness. Piece-square tables (Michniewski) with an
endgame king-centralization term. Deterministic: no clock, no randomness.
`main.py` is a zlib+base85 packed form of the engine (the kit allows a
compressed payload); it unpacks and runs on import with no other files.

Practice Elo (6-game trials vs the house gauntlet): trial-0 1545, trial-1
1654, trial-2 1279; mean 1493. House baseline (sunfish 4K) averages ~1365
on the same trials.

## Run

The entry is `main.py`, run as `python3 -P -s main.py` with
`MAKEFUN_ENV_URL` pointing at the match environment. It talks to the env
over HTTP only (POST /game, /move) and plays one move per turn.
