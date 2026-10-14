# Claude-Skills

A personal collection of [Claude Code skills](https://docs.claude.com/en/docs/claude-code/skills). This repo is the single place I keep every skill I want Claude to be able to use, so I can version them, sync them across machines, and pull them into any project.

Some skills are written by me. Others are borrowed from other people's public repos, and those are tracked in the [Borrowed skills](#borrowed-skills) table below.

## Layout

Every skill is a folder at the root of the repo. Nothing is nested under a `skills/` directory.

```
Claude-Skills/
├── README.md              ← what's here, conventions, where borrowed skills came from
├── .gitignore
├── <skill-name>/
│   ├── SKILL.md           ← required: frontmatter (name, description) + instructions
│   ├── template.md        ← optional supporting files live alongside SKILL.md
│   ├── references/
│   └── scripts/
└── <another-skill>/
    └── SKILL.md
```

## Conventions

- **One folder per skill.** Supporting files (templates, scripts, references) go inside that skill's folder, never at the repo root.
- **kebab-case folder names** that match the `name` in the skill's `SKILL.md` frontmatter. That name is what Claude uses to invoke the skill.
- **Borrowed skills are tracked in two places:** a row in the table below (skill, source URL, date copied) and a short note at the top of the skill's `SKILL.md` saying where it came from. There is no separate attribution file per skill.
- **Keep the original license.** If the source repo ships a license file, it stays inside the skill folder.
- **No secrets.** No API keys, tokens, or passwords in any skill file. This repo may be public.

## Using these skills

Claude Code discovers skills from two places:

- **Personal skills:** `~/.claude/skills/<skill-name>/` (available in every project)
- **Project skills:** `.claude/skills/<skill-name>/` (available only in that project)

The simplest way to use this repo is to clone it and symlink the skills you want into your personal skills directory:

```bash
git clone https://github.com/cadendane-droid/claude-skills.git ~/Claude-Skills

# link one skill
ln -s ~/Claude-Skills/<skill-name> ~/.claude/skills/<skill-name>

# or link every skill folder
for d in ~/Claude-Skills/*/; do
  [ -f "$d/SKILL.md" ] && ln -sfn "$d" ~/.claude/skills/"$(basename "$d")"
done
```

Symlinks mean a `git pull` here updates the skills everywhere they are linked.

Once linked, run `/<skill-name>` in Claude Code, or just describe a task that matches the skill's description and Claude will pick it up automatically.

## Adding a borrowed skill

1. Find the skill directory in the source repo (the folder containing `SKILL.md`).
2. Copy that whole directory to the root of this repo, including any license file.
3. Add a note at the top of its `SKILL.md`, just under the frontmatter, with the source repo URL, author, and date copied.
4. Check that the `name` in `SKILL.md` matches the folder name and does not collide with an existing skill.
5. Add a row to the Borrowed skills table below and commit.

## Borrowed skills

| Skill | Source | Date copied |
|-------|--------|-------------|
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
