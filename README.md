# Claude skills

A plugin marketplace for Claude with 84 skills in four plugins. Install it once and the skills work in Claude chat (web, desktop and mobile), Cowork and Claude Code.

| Plugin | Skills | What it's for | Source | License |
| --- | --- | --- | --- | --- |
| `react-animation-studio` | 11 | Animations for React and TypeScript: 3D, accents, backgrounds, creative effects, CSS, Framer Motion, GSAP, scroll, spring physics, SVG and text | [TheLobbi/claude](https://github.com/TheLobbi/claude/tree/056cffc07fbde4d068ba90ae0b0b81de9fc6d357/plugins/react-animation-studio) (Brookside BI's React Animation Studio) | MIT |
| `motion-design` | 1 | Motion design for product UI: whether to animate, which easing curve and duration to use, spring or bezier, reduced motion | [richtabor/agent-skills](https://github.com/richtabor/agent-skills/tree/f398e130361043e701140a764fbf10bdefaaf083/skills/motion-design) | None stated, so it isn't copied here ([see below](#changes-from-the-sources)) |
| `remotion` | 12 | Making videos with [Remotion](https://www.remotion.dev): best practices, new projects, captions, maps, markup, multimedia, interactivity, rendering, Studio, SaaS apps, docs search and upgrades | [remotion-dev/skills](https://github.com/remotion-dev/skills) | [Remotion License](plugins/remotion/LICENSE.md) |
| `remotion-maintainers` | 60 | Remotion's internal skills for working on the Remotion repository itself. Not needed for making videos | [remotion-dev/remotion](https://github.com/remotion-dev/remotion/tree/648721f460f68f972c57f204dda4d8d11efa6a23/.agents/skills) | [Remotion License](plugins/remotion-maintainers/LICENSE.md) |

## Install

**claude.ai or the Claude desktop app**

1. Go to **Customize > Plugins > Add > Add marketplace** and enter `khaledkhader94/Claude`.
2. Install `react-animation-studio`, `motion-design` and `remotion`. Install `remotion-maintainers` only if you work on Remotion's own code; its skills have generic names like `pr`, `merge` and `release` and follow Remotion's internal steps.
3. Turn on **Sync automatically** so changes to this repo reach your account.

**Claude Code in a terminal**

```
/plugin marketplace add khaledkhader94/Claude
/plugin install react-animation-studio@khaledkhader94-skills
/plugin install motion-design@khaledkhader94-skills
/plugin install remotion@khaledkhader94-skills
```

## Add a skill

Add a folder with a `SKILL.md` to `plugins/<plugin>/skills/`. The file must start with a header that gives the skill's `name` and a `description` of when to use it. To add a new plugin, create `plugins/<name>/.claude-plugin/plugin.json` and list the plugin in `.claude-plugin/marketplace.json`. Check your changes with `claude plugin validate .`.

No plugin sets a `version`, so installed copies follow this repo's latest commit. The exception is `motion-design`, which stays on the commit its catalog entry names.

## Changes from the sources

- `react-animation-studio`: copied from TheLobbi/claude at commit `056cffc`. Each `SKILL.md` got the `name` and `description` header Claude needs; the rest of the text is unchanged. Only the skills were copied, not the original plugin's agents, commands or hook scripts.
- `motion-design`: not copied. richtabor/agent-skills has no license that allows republishing, so the catalog entry fetches only its `skills/motion-design` folder, pinned to commit `f398e13`. To move to a newer version, review it and change `sha` in `.claude-plugin/marketplace.json`.
- `remotion`: copied from remotion-dev/skills at commit `4733526`. The only change moves each header's `version` line under `metadata`, because claude.ai doesn't accept a top-level `version` key.
- `remotion-maintainers`: copied from remotion-dev/remotion at commit `648721f`, leaving out 12 links that point at the skills in the `remotion` plugin. The only change removes the angle brackets around `Demo` in the `docs-demo` description, because claude.ai doesn't accept them there.

Remotion is free for individuals, non-profits and companies with up to 3 employees. Larger companies need a [company license](https://www.remotion.pro/license) to use it.
