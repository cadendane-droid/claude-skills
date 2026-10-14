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
| [scroll-craft](scroll-craft/) | [nateherkai/scroll-craft](https://github.com/nateherkai/scroll-craft) by Nate Herk | 2026-10-14 |
| [humanizer](humanizer/) | [blader/humanizer](https://github.com/blader/humanizer) by Siqi Chen | 2026-10-14 |
| [api-and-interface-design](api-and-interface-design/) | [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills/tree/main/skills/api-and-interface-design) by Addy Osmani | 2026-10-14 |
| [browser-testing-with-devtools](browser-testing-with-devtools/) | [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills/tree/main/skills/browser-testing-with-devtools) by Addy Osmani | 2026-10-14 |
| [ci-cd-and-automation](ci-cd-and-automation/) | [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills/tree/main/skills/ci-cd-and-automation) by Addy Osmani | 2026-10-14 |
| [code-review-and-quality](code-review-and-quality/) | [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills/tree/main/skills/code-review-and-quality) by Addy Osmani | 2026-10-14 |
| [code-simplification](code-simplification/) | [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills/tree/main/skills/code-simplification) by Addy Osmani | 2026-10-14 |
| [constraint-driven-development](constraint-driven-development/) | [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills/tree/main/skills/constraint-driven-development) by Addy Osmani | 2026-10-14 |
| [context-engineering](context-engineering/) | [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills/tree/main/skills/context-engineering) by Addy Osmani | 2026-10-14 |
| [debugging-and-error-recovery](debugging-and-error-recovery/) | [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills/tree/main/skills/debugging-and-error-recovery) by Addy Osmani | 2026-10-14 |
| [deprecation-and-migration](deprecation-and-migration/) | [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills/tree/main/skills/deprecation-and-migration) by Addy Osmani | 2026-10-14 |
| [documentation-and-adrs](documentation-and-adrs/) | [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills/tree/main/skills/documentation-and-adrs) by Addy Osmani | 2026-10-14 |
| [doubt-driven-development](doubt-driven-development/) | [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills/tree/main/skills/doubt-driven-development) by Addy Osmani | 2026-10-14 |
| [frontend-ui-engineering](frontend-ui-engineering/) | [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills/tree/main/skills/frontend-ui-engineering) by Addy Osmani | 2026-10-14 |
| [git-workflow-and-versioning](git-workflow-and-versioning/) | [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills/tree/main/skills/git-workflow-and-versioning) by Addy Osmani | 2026-10-14 |
| [idea-refine](idea-refine/) | [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills/tree/main/skills/idea-refine) by Addy Osmani | 2026-10-14 |
| [incremental-implementation](incremental-implementation/) | [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills/tree/main/skills/incremental-implementation) by Addy Osmani | 2026-10-14 |
| [interview-me](interview-me/) | [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills/tree/main/skills/interview-me) by Addy Osmani | 2026-10-14 |
| [observability-and-instrumentation](observability-and-instrumentation/) | [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills/tree/main/skills/observability-and-instrumentation) by Addy Osmani | 2026-10-14 |
| [performance-optimization](performance-optimization/) | [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills/tree/main/skills/performance-optimization) by Addy Osmani | 2026-10-14 |
| [planning-and-task-breakdown](planning-and-task-breakdown/) | [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills/tree/main/skills/planning-and-task-breakdown) by Addy Osmani | 2026-10-14 |
| [security-and-hardening](security-and-hardening/) | [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills/tree/main/skills/security-and-hardening) by Addy Osmani | 2026-10-14 |
| [shipping-and-launch](shipping-and-launch/) | [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills/tree/main/skills/shipping-and-launch) by Addy Osmani | 2026-10-14 |
| [source-driven-development](source-driven-development/) | [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills/tree/main/skills/source-driven-development) by Addy Osmani | 2026-10-14 |
| [spec-driven-development](spec-driven-development/) | [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills/tree/main/skills/spec-driven-development) by Addy Osmani | 2026-10-14 |
| [test-driven-development](test-driven-development/) | [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills/tree/main/skills/test-driven-development) by Addy Osmani | 2026-10-14 |
| [using-agent-skills](using-agent-skills/) | [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills/tree/main/skills/using-agent-skills) by Addy Osmani | 2026-10-14 |
| [eas-app-stores](eas-app-stores/) | [expo/skills](https://github.com/expo/skills/tree/main/plugins/expo/skills/eas-app-stores) by Expo | 2026-10-14 |
| [eas-hosting](eas-hosting/) | [expo/skills](https://github.com/expo/skills/tree/main/plugins/expo/skills/eas-hosting) by Expo | 2026-10-14 |
| [eas-observe](eas-observe/) | [expo/skills](https://github.com/expo/skills/tree/main/plugins/expo/skills/eas-observe) by Expo | 2026-10-14 |
| [eas-simulator](eas-simulator/) | [expo/skills](https://github.com/expo/skills/tree/main/plugins/expo/skills/eas-simulator) by Expo | 2026-10-14 |
| [eas-update](eas-update/) | [expo/skills](https://github.com/expo/skills/tree/main/plugins/expo/skills/eas-update) by Expo | 2026-10-14 |
| [eas-update-insights](eas-update-insights/) | [expo/skills](https://github.com/expo/skills/tree/main/plugins/expo/skills/eas-update-insights) by Expo | 2026-10-14 |
| [eas-workflows](eas-workflows/) | [expo/skills](https://github.com/expo/skills/tree/main/plugins/expo/skills/eas-workflows) by Expo | 2026-10-14 |
| [expo-animation](expo-animation/) | [expo/skills](https://github.com/expo/skills/tree/main/plugins/expo/skills/expo-animation) by Expo | 2026-10-14 |
| [expo-app-clip](expo-app-clip/) | [expo/skills](https://github.com/expo/skills/tree/main/plugins/expo/skills/expo-app-clip) by Expo | 2026-10-14 |
| [expo-brownfield](expo-brownfield/) | [expo/skills](https://github.com/expo/skills/tree/main/plugins/expo/skills/expo-brownfield) by Expo | 2026-10-14 |
| [expo-data-fetching](expo-data-fetching/) | [expo/skills](https://github.com/expo/skills/tree/main/plugins/expo/skills/expo-data-fetching) by Expo | 2026-10-14 |
| [expo-design-system](expo-design-system/) | [expo/skills](https://github.com/expo/skills/tree/main/plugins/expo/skills/expo-design-system) by Expo | 2026-10-14 |
| [expo-dev-client](expo-dev-client/) | [expo/skills](https://github.com/expo/skills/tree/main/plugins/expo/skills/expo-dev-client) by Expo | 2026-10-14 |
| [expo-dom](expo-dom/) | [expo/skills](https://github.com/expo/skills/tree/main/plugins/expo/skills/expo-dom) by Expo | 2026-10-14 |
| [expo-examples](expo-examples/) | [expo/skills](https://github.com/expo/skills/tree/main/plugins/expo/skills/expo-examples) by Expo | 2026-10-14 |
| [expo-module](expo-module/) | [expo/skills](https://github.com/expo/skills/tree/main/plugins/expo/skills/expo-module) by Expo | 2026-10-14 |
| [expo-native-ui](expo-native-ui/) | [expo/skills](https://github.com/expo/skills/tree/main/plugins/expo/skills/expo-native-ui) by Expo | 2026-10-14 |
| [expo-overview](expo-overview/) | [expo/skills](https://github.com/expo/skills/tree/main/plugins/expo/skills/expo-overview) by Expo | 2026-10-14 |
| [expo-project-structure](expo-project-structure/) | [expo/skills](https://github.com/expo/skills/tree/main/plugins/expo/skills/expo-project-structure) by Expo | 2026-10-14 |
| [expo-router](expo-router/) | [expo/skills](https://github.com/expo/skills/tree/main/plugins/expo/skills/expo-router) by Expo | 2026-10-14 |
| [expo-ui](expo-ui/) | [expo/skills](https://github.com/expo/skills/tree/main/plugins/expo/skills/expo-ui) by Expo | 2026-10-14 |
| [expo-upgrade](expo-upgrade/) | [expo/skills](https://github.com/expo/skills/tree/main/plugins/expo/skills/expo-upgrade) by Expo | 2026-10-14 |
| [expo-web-to-native](expo-web-to-native/) | [expo/skills](https://github.com/expo/skills/tree/main/plugins/expo/skills/expo-web-to-native) by Expo | 2026-10-14 |

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
