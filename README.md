# Andrej Karpathy Guideline For Codex

Behavioral guidelines for Codex, adapted from Andrej Karpathy's observations about common LLM coding failure modes.

This repository packages the ideas in a Codex-native form by centering them around a workspace `AGENTS.md` file.

It is adapted from the original project:

- `https://github.com/forrestchang/andrej-karpathy-skills`

## Why this exists

Karpathy's critique of coding agents is still accurate across tools:

- they make hidden assumptions
- they overcomplicate simple tasks
- they touch code they were not asked to touch
- they optimize for motion instead of verifiable progress

Codex is powerful, but it also benefits from explicit local guidance. This repository gives you a small instruction file that pushes Codex toward:

- explicit assumptions
- simpler implementations
- surgical diffs
- verification-driven execution

## The four principles

### 1. Think Before Coding

Do not guess through ambiguity. Surface assumptions, name uncertainty, and ask when the risk of being wrong is material.

### 2. Simplicity First

Write the smallest solution that satisfies the request. Avoid speculative abstractions, unused flexibility, and premature edge-case machinery.

### 3. Surgical Changes

Touch only what the task requires. Avoid drive-by cleanup, formatting churn, and unrelated refactors.

### 4. Goal-Driven Execution

Turn tasks into verifiable goals. Prefer tests, builds, or direct checks over intuition when deciding whether work is complete.

## Install

Copy `AGENTS.md` into the root of the workspace you want Codex to follow:

```bash
curl -o AGENTS.md https://raw.githubusercontent.com/hobart9527/andrej-karpathy-guideline-for-codex/main/AGENTS.md
```

Or append it into an existing `AGENTS.md` if you already have workspace rules:

```bash
printf '\n' >> AGENTS.md
curl https://raw.githubusercontent.com/hobart9527/andrej-karpathy-guideline-for-codex/main/AGENTS.md >> AGENTS.md
```

## What "good" looks like

These guidelines are working if you see:

- fewer unnecessary lines in diffs
- fewer speculative abstractions
- more clarifying questions before incorrect implementation
- stronger verification before claiming success

## Source

This repository is adapted from the original `CLAUDE.md`-based project at:

- `https://github.com/forrestchang/andrej-karpathy-skills`

The intent is not to change the ideas, only to package them for Codex.
