# wp-agent-skills

A Claude Code plugin marketplace that re-exposes every skill from [WordPress/agent-skills](https://github.com/WordPress/agent-skills) as an individually toggleable plugin. Instead of installing all 15 skills globally into `~/.claude/skills/`, this marketplace lets you pick exactly which WordPress skills each project needs via `/plugin install` and `/plugin disable`.

## Install

Add the marketplace, then install only the plugins you need:

```bash
/plugin marketplace add <YOUR_GITHUB_USERNAME>/wp-agent-skills
```

```bash
/plugin install wp-block-development@wp-agent-skills
```

## Available Plugins

| Plugin | Description |
|--------|-------------|
| `wp-blueprint` | Creating, editing, or reviewing WordPress Playground blueprint JSON files |
| `wp-router` | Classify WordPress codebases and route to the correct workflow/skill |
| `wp-abilities-api` | WordPress Abilities API — defining abilities, categories, REST exposure, permissions |
| `wp-block-development` | Developing Gutenberg blocks — block.json, attributes, dynamic rendering, build tooling |
| `wp-block-themes` | Block themes — theme.json, templates, template parts, patterns, style variations |
| `wp-interactivity-api` | Interactivity API — data-wp-* directives, store/state/actions, hydration |
| `wp-performance` | Backend performance profiling — Query Monitor, object caching, DB optimization |
| `wp-phpstan` | PHPStan static analysis in WordPress projects — config, baselines, WP-specific typing |
| `wp-playground` | WordPress Playground workflows — disposable instances, CLI, version switching, Xdebug |
| `wp-plugin-development` | Plugin architecture — hooks, activation/deactivation, Settings API, security, packaging |
| `wp-plugin-directory-guidelines` | WordPress.org Plugin Directory guidelines — GPL compliance, naming, trialware rules |
| `wp-project-triage` | Deterministic repo inspection — detect project type, tooling, tests, version hints |
| `wp-rest-api` | REST API endpoints — register_rest_route, controllers, schema, authentication |
| `wp-wpcli-and-ops` | WP-CLI operations — search-replace, db management, cron, multisite, automation |
| `wpds` | WordPress Design System — components, tokens, patterns |

## Recommended Setups

### Block Development

```bash
/plugin install wp-router@wp-agent-skills
/plugin install wp-block-development@wp-agent-skills
/plugin install wp-block-themes@wp-agent-skills
/plugin install wp-interactivity-api@wp-agent-skills
/plugin install wp-project-triage@wp-agent-skills
```

### Plugin Development

```bash
/plugin install wp-router@wp-agent-skills
/plugin install wp-plugin-development@wp-agent-skills
/plugin install wp-rest-api@wp-agent-skills
/plugin install wp-phpstan@wp-agent-skills
/plugin install wp-plugin-directory-guidelines@wp-agent-skills
/plugin install wp-project-triage@wp-agent-skills
```

### Ops / Maintenance

```bash
/plugin install wp-router@wp-agent-skills
/plugin install wp-wpcli-and-ops@wp-agent-skills
/plugin install wp-performance@wp-agent-skills
/plugin install wp-playground@wp-agent-skills
/plugin install wp-project-triage@wp-agent-skills
```

## Updating

Pull the latest skill content from upstream:

```bash
/plugin marketplace update wp-agent-skills
```

Since individual plugin entries omit a `version` field, they track the upstream `trunk` branch and auto-update when WordPress pushes new commits.

To pin a specific upstream version, add a `sha` to that plugin's `source` in `marketplace.json`:

```json
{
  "source": {
    "source": "git-subdir",
    "url": "https://github.com/WordPress/agent-skills.git",
    "path": "skills/wp-block-development",
    "ref": "trunk",
    "sha": "abc1234..."
  }
}
```

Or change `ref` from `"trunk"` to a specific tag or branch name.

## Credits

All skill content is authored and maintained by the [WordPress/agent-skills](https://github.com/WordPress/agent-skills) project. This marketplace is a thin distribution layer — no upstream content is copied into this repo.

Licensed under [GPL-2.0-or-later](https://www.gnu.org/licenses/gpl-2.0.html), consistent with the upstream project.
