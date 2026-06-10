# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

植物棋类策略游戏 — a turn-based PvE strategy game. Plants compete for territory and resources against insects and rival plants on a square grid. Gameplay revolves around planting seeds, growing a self-sustaining plant ecosystem (根/茎/叶/花/果), managing resources (水/光/土/养分), and defeating enemies.

**Current phase**: Design complete, code not yet started.

## Authoritative Document

`设计文档/游戏规则文档.md` (v0.4) — the single source of truth for all game rules, combat formulas, enemy AI patterns, turn structure, and variable parameters.

## Repo Structure

- `设计文档/` — current design documents (active)
- `完善规划/` — **deprecated** old design drafts, kept for reference only, do not modify

## Planned Tech Stack

- HTML + JavaScript + Canvas (no dependencies)
- Configuration-driven: all numeric parameters use variables (see 第八章 of the rules doc), to be tuned via simulation later
- Prototype first, then consider Electron for standalone release

## Key Design Decisions

- **Variables over hardcoded numbers**: Resource costs, combat stats, and decay rates are all parameterized (e.g., `C_种_水`, `ATK_玩家`). Placeholder defaults exist purely to make the engine runnable; final values will be determined through simulation.
- **Damage formula**: `max(ATK - DEF, 1)`, with planned future support for multipliers
- **Turn structure**: 5 phases — 回合开始 → 回合预备 → 回合进行 → 回合结束 → 回合终止
- **Piece resolution order within a tile**: 根 → 叶 → 茎 → 花 → 果 → 种
- **Enemy AI**: Three patterns (主动型/冷静型/不动型), Fire Emblem style

## When Coding Begins

Development order defined in 第十二章 of the rules doc:
1. Phase A: Engine core (board rendering → piece model → turn state machine → resources → player actions → enemy AI)
2. Phase B: Simulation & balance tuning
3. Phase C: Level design, UI polish, release
