# Prompt Comparison: Current vs Reverse-Engineered

## Major Additions in Current Prompt

### 1. Plan Mode System
**Current prompt has:**
- `EnterPlanMode` tool - for planning non-trivial implementations before coding
- `ExitPlanMode` tool - to exit plan mode after user approval
- Detailed guidance on when to use plan mode vs direct implementation
- Examples of tasks requiring planning

**Workflow prompt:** No mention of plan mode

---

### 2. Task Tool with Specialized Subagents
**Current prompt has detailed subagent types:**
- `general-purpose` - complex multi-step tasks
- `statusline-setup` - configure status line
- `Explore` - fast codebase exploration with thoroughness levels
- `Plan` - software architect for implementation planning
- `claude-code-guide` - answers questions about Claude Code/SDK/API
- Instructions to resume agents, run in background, etc.

**Workflow prompt:** Generic "Task tool" mention without subagent details

---

### 3. Git Commit Protocol (Massively Expanded)
**Current prompt has extensive Git Safety Protocol:**
```
- NEVER update git config
- NEVER run destructive commands unless explicit
- NEVER skip hooks (--no-verify, --no-gpg-sign)
- NEVER force push to main/master
- Avoid git commit --amend (detailed conditions when allowed)
- CRITICAL: If commit FAILED, NEVER amend - create NEW commit
- Detailed heredoc format for commit messages
- Co-Authored-By: Claude Sonnet 4.5 footer
```

**Workflow prompt:** Brief "NEVER commit changes unless explicitly asked"

---

### 4. Pull Request Creation
**Current prompt has:**
- Detailed multi-step PR creation workflow
- Use `gh pr create` with heredoc body format
- Include "🤖 Generated with Claude Code" footer
- Git log analysis to understand full branch history

**Workflow prompt:** No PR creation instructions

---

### 5. Documentation Lookup Strategy
**Current prompt:**
- Use `claude-code-guide` subagent for Claude Code/SDK questions
- Check for running agents to resume before spawning new ones

**Workflow prompt:**
- Use `WebFetch` to docs.anthropic.com with hardcoded subpage list

---

### 6. Professional Objectivity Section
**Current prompt has:**
> Prioritize technical accuracy and truthfulness over validating the user's beliefs. Focus on facts and problem-solving... Avoid using over-the-top validation or excessive praise...

**Workflow prompt:** Not present

---

### 7. Planning Without Timelines
**Current prompt has:**
> When planning tasks, provide concrete implementation steps without time estimates. Never suggest timelines like "this will take 2-3 weeks"...

**Workflow prompt:** Not present

---

### 8. Bash Tool Usage Policy (More Restrictive)
**Current prompt explicitly forbids:**
- Using Bash for: find, grep, cat, head, tail, sed, awk, echo
- "NEVER use bash echo to communicate with user"
- Detailed examples of what to use instead (Glob, Grep, Read, Edit, Write)

**Workflow prompt:** Generic tool usage policy

---

### 9. Security Policy (More Detailed)
**Current prompt:**
> Assist with authorized security testing, defensive security, CTF challenges... Dual-use security tools (C2 frameworks, credential testing, exploit development) require clear authorization context: pentesting engagements, CTF competitions...

**Workflow prompt:** Generic "defensive security only"

---

### 10. Model Information
**Current prompt:** Sonnet 4.5 (claude-sonnet-4-5-20250929), knowledge cutoff January 2025

**Workflow prompt:** Sonnet 4 (claude-sonnet-4-20250514), knowledge cutoff January 2025

---

## Identical Sections

These are nearly word-for-word the same:
- Tone & style (concise responses, examples)
- Task management with TodoWrite
- Code conventions (no comments, check package.json, follow patterns)
- Tool batching/parallel execution
- Code references (file_path:line_number)
- Hooks handling
- Git status snapshot
- Proactiveness balance
- Environment variables section

---

## Summary

The reverse-engineered workflow prompt captures **~60% of the current prompt**. The missing parts are primarily:

1. **Advanced multi-agent orchestration** (Plan mode, subagent types)
2. **Git workflows** (detailed commit/PR protocols)
3. **Behavioral guidelines** (professional objectivity, no timelines)
4. **Tool usage restrictions** (stricter Bash rules)

This suggests the reverse-engineered version is from an **earlier iteration** (July 2025 per README), before these advanced features were added.
