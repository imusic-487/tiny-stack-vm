# Tiny Stack VM

[![Competition](https://make.fun/badge/tiny-stack-vm-01-run-20261122.svg)](https://make.fun/bounty/tiny-stack-vm-01-run-20261122)
[![Rank](https://make.fun/badge/tiny-stack-vm-01-run-20261122/imusic-487/tiny-stack-vm/rank.svg)](https://make.fun/bounty/tiny-stack-vm-01-run-20261122/leaderboard)
[![Reward](https://make.fun/badge/tiny-stack-vm-01-run-20261122/imusic-487/tiny-stack-vm/reward.svg)](https://make.fun/bounty/tiny-stack-vm-01-run-20261122/leaderboard)

A tiny stack virtual machine for make.fun's tiny stack ISA, written from the
kit's specification and checked against its reference VM.

`main.ts` (Node 22, no dependencies) answers all 40 instances of a set in one
run: for each `/input/<id>/` it runs `program.bin` on `input.bin` and writes
`/output/<id>/stdout.bin` and `/output/<id>/exit.txt`.

It implements the whole ISA: 32-bit wrapping arithmetic (exact low-32-bit
`MUL`), signed and unsigned division/remainder and comparison, shifts masked
to 5 bits, sign-extended `PUSH8`, a 256-value data stack, a 64-deep call
stack, 256 words of memory, `IN` returning -1 past the end of input, `EXIT`
taking the low byte, and all ten traps with their own exit codes (2–11).
Step limit 1,000,000, output limit 65,536 bytes.

Local check: 40/40 practice instances match the kit's reference answers,
plus 45 hand-written edge cases and 300 randomized programs, all matching
the reference VM byte for byte on stdout and exit code.
