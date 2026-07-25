# adhd-friendly

A communication-style skill for AI coding agents — makes responses **structured,
scannable, and to the point**, instead of walls of prose. Built for people
with ADHD, and honestly just better for everyone.

Works with **Claude Code, Cursor, VS Code (Copilot/Continue), Windsurf,
Antigravity, and anything else that accepts custom instructions/rules/system
prompts** — see [Installation](#installation) for your tool.

## Why

Most coding agents default to writing like they're being graded on word
count: three paragraphs of throat-clearing before the actual answer, a wall
of prose describing five things that happened, and a closing "let me know
your thoughts!" that hands you a blank-page decision instead of a next step.

That's a tax on anyone's attention. For ADHD specifically, it's often the
difference between actually reading the response and bouncing off it
entirely.

This skill doesn't make the agent dumber or the answers shorter on
substance — it makes the *shape* of the answer respect your attention:
the point first, the structure visible, a concrete next step at the end.

See [`examples/before-after.md`](examples/before-after.md) for a real
side-by-side.

## What it actually does

- **Leads with the answer**, not three paragraphs of setup
- **Structures everything** — headers, bullets, numbered steps, tables —
  never a dense unbroken paragraph
- **Uses emojis as signposts** (✅ ⚠️ 👉), not decoration
- **Plain language over jargon**
- **Turns multi-step work into checkable steps**, not prose
- **Ends with a concrete next step**, not an open-ended "thoughts?"
- **Never cuts technical depth or accuracy** to hit a length target —
  compresses words, not substance

Full rules and rationale are in [`skills/adhd-friendly/SKILL.md`](skills/adhd-friendly/SKILL.md) —
that's the file that actually gets loaded by your tool; the rest of this
repo is just docs around it.

## Installation

### Claude Code

Copy the skill folder into your personal skills directory (works across
all your projects):

```bash
mkdir -p ~/.claude/skills
cp -r skills/adhd-friendly ~/.claude/skills/adhd-friendly
```

Or for one project only, put it in `.claude/skills/adhd-friendly/` inside
that project instead of `~/.claude/skills/`.

It activates automatically once you mention ADHD, ask for shorter/clearer
responses, or type `/adhd-friendly`.

### Cursor

Cursor reads project rules from `.cursor/rules/`. Copy the file in and
rename it:

```bash
mkdir -p .cursor/rules
cp skills/adhd-friendly/SKILL.md .cursor/rules/adhd-friendly.mdc
```

(Cursor's `.mdc` format also supports the same YAML frontmatter + Markdown
body — no content changes needed, just the file extension.)

### VS Code (Copilot / Continue / other assistants)

Copilot reads repo-level custom instructions from a fixed file:

```bash
mkdir -p .github
cat skills/adhd-friendly/SKILL.md >> .github/copilot-instructions.md
```

For Continue.dev or similar, paste the body of `SKILL.md` into your
`config.json` `systemMessage`, or your extension's custom-instructions
setting.

### Windsurf

```bash
cat skills/adhd-friendly/SKILL.md >> .windsurfrules
```

### Antigravity / any other agentic tool

Most agentic coding tools accept a custom system prompt, project
instructions file, or "rules" file. Paste the contents of
[`skills/adhd-friendly/SKILL.md`](skills/adhd-friendly/SKILL.md) into
whichever mechanism your tool provides. The file is plain Markdown with a
YAML frontmatter header — no special parsing required, any tool that
reads plain instructions can use it.

### Manual / just tell it directly

No install mechanism at all? Paste the SKILL.md body straight into your
first message of a conversation: *"Follow these communication rules for
the rest of this conversation: [paste]."* Works with literally any LLM
chat interface.

## Not the other "ADHD" skill

If you've seen a Claude Code skill also named `adhd` that does parallel
divergent-frame brainstorming — that's a different project, a pun on the
name for a reasoning technique, not about communication style. This one
is about how responses are *written*, not how the agent *thinks*. No
relation, easy to confuse, worth checking you have the right one.

## Contributing

The 8 core rules in `SKILL.md` are the load-bearing part — keep those
intact in forks. Tool-specific install docs, emoji choices, and template
shape are all fair game to adapt. PRs adding install instructions for
tools not yet covered here are especially welcome.

## License

MIT — see [LICENSE](LICENSE).
