# Andrej Karpathy Guideline For Codex

Behavioral guidelines for Codex, adapted from Andrej Karpathy's observations about common LLM coding failure modes.

This repository packages the ideas in a Codex-native form by centering them around workspace instruction files such as `AGENTS.md` and `CLAUDE.md`.

It is adapted from the original project:

- `https://github.com/forrestchang/andrej-karpathy-skills`

## Why this exists

Karpathy's critique of coding agents is still accurate across tools:

- they make hidden assumptions
- they overcomplicate simple tasks
- they touch code they were not asked to touch
- they optimize for motion instead of verifiable progress

Codex is powerful, but it also benefits from explicit local guidance. This repository gives you a small instruction file that pushes coding agents toward:

- explicit assumptions
- local inspection before editing
- simpler implementations
- surgical diffs
- verification-driven execution
- safer handling of high-risk changes

## The principles

### 1. Think Before Coding

Do not guess through ambiguity. Surface assumptions, name uncertainty, and ask when the risk of being wrong is material.

### 2. Inspect Before Editing

Read the relevant files and local conventions before making changes. Prefer project evidence over generic assumptions.

### 3. Simplicity First

Write the smallest solution that satisfies the request. Avoid speculative abstractions, unused flexibility, and premature edge-case machinery.

### 4. Surgical Changes

Touch only what the task requires. Avoid drive-by cleanup, formatting churn, and unrelated refactors.

### 5. Goal-Driven Execution

Turn tasks into verifiable goals. Prefer tests, builds, or direct checks over intuition when deciding whether work is complete.

### 6. Verify With Real Project Checks

Prefer actual repository checks such as tests, lint, type-check, and build commands over intuition. If verification cannot run, say why.

### 7. Preserve Object Boundaries

Simplifying implementation is fine. Silently collapsing distinct domain objects is not. Temporary feature reduction is usually safer than mixing ownership boundaries.

### 8. Respect Risk Boundaries

Ask before irreversible changes, dependency additions, schema or migration changes, network use, or writes outside the working area.

### 9. Keep Guidance Practical

Keep default guidance short and reusable. Put project-specific workflow details in repository-local instruction files.

## Install

Copy `AGENTS.md` into the root of the workspace you want Codex to follow:

```bash
curl -o AGENTS.md https://raw.githubusercontent.com/hobart9527/andrej-karpathy-guideline-for-codex/main/AGENTS.md
```

If you also want a Claude-compatible version in the same repository:

```bash
curl -o CLAUDE.md https://raw.githubusercontent.com/hobart9527/andrej-karpathy-guideline-for-codex/main/CLAUDE.md
```

Or append the guidance into an existing `AGENTS.md` if you already have workspace rules:

```bash
printf '\n' >> AGENTS.md
curl https://raw.githubusercontent.com/hobart9527/andrej-karpathy-guideline-for-codex/main/AGENTS.md >> AGENTS.md
```

You can do the same for an existing `CLAUDE.md`:

```bash
printf '\n' >> CLAUDE.md
curl https://raw.githubusercontent.com/hobart9527/andrej-karpathy-guideline-for-codex/main/CLAUDE.md >> CLAUDE.md
```

## What "good" looks like

These guidelines are working if you see:

- fewer unnecessary lines in diffs
- more time spent reading the right files before editing
- fewer speculative abstractions
- more clarifying questions before incorrect implementation
- stronger verification before claiming success

## Source

This repository is adapted from the original `CLAUDE.md`-based project at:

- `https://github.com/forrestchang/andrej-karpathy-skills`

The intent is not to change the ideas, only to package them for Codex.
