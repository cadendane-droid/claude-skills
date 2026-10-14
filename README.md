# Claude-Skills

A personal collection of [Claude Code skills](https://docs.claude.com/en/docs/claude-code/skills). This repo is the single place I keep every skill I want Claude to be able to use, so I can version them, sync them across machines, and pull them into any project.

Most skills here are copied from other people's public repos. Each one keeps its original license and a pointer back to where it came from.

## Layout

```
Claude-Skills/
├── README.md
└── skills/
    └── <skill-name>/
        ├── SKILL.md        # required: frontmatter (name, description) + instructions
        ├── scripts/        # optional helper scripts
        ├── references/     # optional reference docs the skill reads on demand
        └── SOURCE.md       # where the skill came from, author, license, date copied
```

One directory per skill under `skills/`. The directory name should match the `name` in the skill's `SKILL.md` frontmatter, since that is the name Claude uses to invoke it.

## Using these skills

Claude Code discovers skills from two places:

- **Personal skills:** `~/.claude/skills/<skill-name>/` (available in every project)
- **Project skills:** `.claude/skills/<skill-name>/` (available only in that project)

The simplest way to use this repo is to clone it and symlink the skills you want into your personal skills directory:

```bash
git clone https://github.com/<your-username>/Claude-Skills.git ~/Claude-Skills

# link one skill
ln -s ~/Claude-Skills/skills/<skill-name> ~/.claude/skills/<skill-name>

# or link all of them
for d in ~/Claude-Skills/skills/*/; do
  ln -sfn "$d" ~/.claude/skills/"$(basename "$d")"
done
```

Symlinks mean a `git pull` here updates the skills everywhere they are linked.

Once linked, run `/<skill-name>` in Claude Code, or just describe a task that matches the skill's description and Claude will pick it up automatically.

## Adding a skill from another repo

1. Find the skill directory in the source repo (the folder containing `SKILL.md`).
2. Copy that whole directory into `skills/` here.
3. Add a `SOURCE.md` inside it noting the source repo URL, author, license, and the commit or date you copied it from.
4. Check that the `name` in `SKILL.md` matches the directory name and does not collide with an existing skill.
5. Add a row to the index below and commit.

Keeping the original license file alongside the skill is the right thing to do if the source repo has one.

## Skills index

| Skill | What it does | Source |
|-------|--------------|--------|
| _none yet_ | | |

## Writing your own

A skill only needs a `SKILL.md`:

```markdown
---
name: my-skill
description: One or two sentences on what this does and when Claude should use it.
---

Instructions for Claude go here.
```

The `description` matters most. Claude reads it to decide whether the skill applies to the current task, so make it specific about triggers ("use when the user asks to...").
