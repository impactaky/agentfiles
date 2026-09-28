## Minimal Harness for Coding Agents

> **Archived.** This repository is no longer maintained. Its contents were
> integrated into [knowledge-management](https://github.com/impactaky/knowledge-management)'s
> `order` skill, which embeds the harness directly in the first prompt of each
> implementation agent instead of copying files into repositories.
>
> | Former file | Now |
> |---|---|
> | `AGENTS.override.md` (harness) | [`skills/order/worker-prompt.md`](https://github.com/impactaky/knowledge-management/blob/main/skills/order/worker-prompt.md) |
> | `project-rules.md` | Per-project rules injected through the order config's `[context] project_rules` by [`skills/order/scripts/build-prompt.py`](https://github.com/impactaky/knowledge-management/blob/main/skills/order/scripts/build-prompt.py) |
> | `.myagents/commands/` | Removed |

A simple, minimal harness for coding agents.

Keeping the instructions short makes them easier to maintain and reduces context usage.
