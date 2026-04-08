# AgentV Bench: Skills

Benchmark repo for agent skill and capability evaluations using [AgentV](https://github.com/EntityProcess/agentv).

## Overview

This repository contains evaluation benchmarks that test agent capabilities across different providers and skill configurations. The goal is to systematically measure how well various AI agents perform on reasoning, coding, and tool-use tasks, enabling comparison across providers like Claude, GPT, and Gemini.

Each eval suite focuses on a specific skill category, with individual test cases that exercise different aspects of that skill. Results are graded using a combination of LLM-based grading, exact matching, and code execution.

## Structure

```
agentv-bench-skills/
├── evals/                    # Eval YAML files
│   ├── reasoning/            # Reasoning task evals (logic, math, puzzles)
│   ├── coding/               # Coding task evals (non-SWE-bench)
│   └── tool-use/             # Tool use evaluations (file ops, search, etc.)
├── scripts/                  # Utility scripts
├── .agentv/                  # AgentV project configuration
│   ├── config.yaml           # Project settings
│   └── targets.yaml          # Provider/model target definitions
└── README.md
```

## Running Evals

Run all evals against all targets:

```bash
agentv eval
```

Run a specific eval suite:

```bash
agentv eval evals/reasoning/
```

Run against a specific target:

```bash
agentv eval --target claude-sonnet
```

## Results

Results are stored in `.agentv/results/` (git-ignored). Use AgentV Studio to visualize:

```bash
agentv studio
```

The default pass threshold is set to 0.8 (80%) in `.agentv/config.yaml`.

## Experiments

Use this repo to run comparative experiments across providers:

- **Provider comparison**: Run the same eval suite against Claude, GPT, and Gemini to compare capabilities.
- **Model scaling**: Compare different model tiers (e.g., Sonnet vs Opus) on the same tasks.
- **Skill-specific analysis**: Identify which providers excel at reasoning vs coding vs tool use.
- **Regression tracking**: Re-run evals after model updates to detect capability changes.

To add a new experiment, create a new eval YAML file in the appropriate `evals/` subdirectory following the existing patterns.
