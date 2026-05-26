# xworkspace-core-skills

Workspace core skills synchronized from the `ubuntu` user runtime on `root@openclaw.svc.plus`.

This directory is intentionally separate from the repository's existing `skills/` directory. The existing `skills/` directory remains the source-owned AI video/content skill set. `xworkspace-core-skills/` is a runtime-core bundle for OpenClaw/Codex workspace support skills that were present remotely but were not first-class local repository skill directories.

## Sources

| Source | Remote path | Local path | Acquisition path |
|---|---|---|---|
| OpenClaw workspace | `/home/ubuntu/.openclaw/workspace/skills` | `xworkspace-core-skills/skills/openclaw-workspace` | Runtime workspace skills installed through OpenClaw/Clawhub or workspace bootstrap |
| Codex system | `/home/ubuntu/.codex/skills/.system` | `xworkspace-core-skills/skills/codex-system` | Bundled Codex system skills, normally provided by `npx codex` / Codex runtime |

Excluded source:

- `/home/ubuntu/.agents/skills`: broad user skill library. It is not mirrored here because it contains many general-purpose and marketplace skills beyond the OpenClaw/Codex workspace core surface.

## Inventory

### OpenClaw Workspace Skills

| Skill directory | Skill name | Source note |
|---|---|---|
| `browser-automation` | `browser` | OpenClaw workspace / Clawhub-style browser automation skill |
| `cron-helper` | `cron-helper` | OpenClaw workspace scheduling helper |
| `excel-xlsx` | `Excel / XLSX` | OpenClaw workspace document skill for Excel files |
| `find-skills-skill` | `find-skills` | OpenClaw workspace skill discovery helper |
| `hermes-learning-loop` | `hermes-learning-loop` | OpenClaw workspace Hermes-inspired learning loop |
| `image-cog` | `image-cog` | OpenClaw workspace image generation/editing skill |
| `image-resizer` | `image-resizer` | OpenClaw workspace image resize/compress helper |
| `pdf` | `pdf` | OpenClaw workspace document skill for PDFs |
| `powerpoint-pptx` | `Powerpoint / PPTX` | OpenClaw workspace document skill for PowerPoint decks |
| `qmd` | `qmd` | OpenClaw workspace markdown knowledge-base search skill |
| `remote-desktop` | `Remote Desktop` | OpenClaw workspace remote desktop helper |
| `self-improving` | `Self-Improving + Proactive Agent` | OpenClaw workspace self-improvement skill |
| `skylv-hermes-agent-integration` | `hermes-agent-integration` | OpenClaw workspace Hermes Agent integration |
| `tiangong-notebooklm-cli` | `notebooklm` | OpenClaw workspace NotebookLM CLI wrapper |
| `video-translator` | `video-translator` | OpenClaw workspace video translation/dubbing skill |
| `virtual-remote-desktop` | `virtual-remote-desktop` | OpenClaw workspace KasmVNC virtual desktop helper |
| `wan-image-video-generation-editting` | `wan-image-video-gen-edit` | OpenClaw workspace Wan image/video generation and editing skill |
| `web-search` | `web-search` | OpenClaw workspace web search helper |
| `word-docx` | `Word / DOCX` | OpenClaw workspace document skill for Word files |

### Codex System Skills

| Skill directory | Skill name | Source note |
|---|---|---|
| `imagegen` | `imagegen` | Codex system skill bundled with the Codex runtime |
| `openai-docs` | `openai-docs` | Codex system skill for official OpenAI documentation workflows |
| `plugin-creator` | `plugin-creator` | Codex system skill for plugin scaffolding |
| `skill-creator` | `skill-creator` | Codex system skill for authoring skills |
| `skill-installer` | `skill-installer` | Codex system skill for installing skills |

## Refresh Command

Run from the repository root:

```bash
ssh root@openclaw.svc.plus 'cd /tmp && rm -rf xworkspace-core-skills-sync && mkdir -p xworkspace-core-skills-sync/openclaw-workspace xworkspace-core-skills-sync/codex-system && for d in browser-automation cron-helper excel-xlsx find-skills-skill hermes-learning-loop image-cog image-resizer pdf powerpoint-pptx qmd remote-desktop self-improving skylv-hermes-agent-integration tiangong-notebooklm-cli video-translator virtual-remote-desktop wan-image-video-generation-editting web-search word-docx; do cp -a /home/ubuntu/.openclaw/workspace/skills/$d xworkspace-core-skills-sync/openclaw-workspace/; done && for d in imagegen openai-docs plugin-creator skill-creator skill-installer; do cp -a /home/ubuntu/.codex/skills/.system/$d xworkspace-core-skills-sync/codex-system/; done && tar -czf /tmp/xworkspace-core-skills-sync.tar.gz -C /tmp xworkspace-core-skills-sync'
scp root@openclaw.svc.plus:/tmp/xworkspace-core-skills-sync.tar.gz /tmp/xworkspace-core-skills-sync.tar.gz
mkdir -p xworkspace-core-skills/skills
tar -xzf /tmp/xworkspace-core-skills-sync.tar.gz -C /tmp
rm -rf xworkspace-core-skills/skills/openclaw-workspace xworkspace-core-skills/skills/codex-system
mv /tmp/xworkspace-core-skills-sync/openclaw-workspace xworkspace-core-skills/skills/openclaw-workspace
mv /tmp/xworkspace-core-skills-sync/codex-system xworkspace-core-skills/skills/codex-system
rm -rf /tmp/xworkspace-core-skills-sync /tmp/xworkspace-core-skills-sync.tar.gz
ssh root@openclaw.svc.plus 'rm -f /tmp/xworkspace-core-skills-sync.tar.gz'
```

## Notes

- Do not merge these directories into the top-level `skills/` tree unless they become source-owned by this repository.
- Keep source attribution in this README current when refreshing from a different host, user, or runtime installation path.
