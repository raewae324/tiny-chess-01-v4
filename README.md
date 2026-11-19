# tiny-chess-01 v4

A fresh 0x88 chess engine in 4 KB of Python, written from scratch for
make.fun tiny-chess-01 ("Build the strongest chess engine in 4 KB").

- Alpha-beta with iterative deepening and a fixed 80,000-node budget per
  move: fully deterministic, no wall clock in the search.
- Null-move pruning and late-move reductions (the depth the v3 engine
  lacked), transposition table, quiescence search over captures,
  promotions and check evasions.
- Move ordering: TT move first, then MVV-LVA captures, killer moves,
  history heuristic.
- Evaluation: material + piece-square terms + bishop pair.
- Talks to the env over HTTP (`MAKEFUN_ENV_URL`): POST /game, POST /move.

`main.py` (3,430 bytes) is an lzma+base85 packed payload with a tiny
unpacker; the node budget `L` sits outside the payload so it can be tuned.
