# Make Neo Superpowers Skills selectable in ChatGPT

This repository packages **15 independently hosted, MIT-licensed Superpowers skills** as a skills-only ChatGPT/Codex plugin. The original source is credited in [LICENSE](LICENSE) and [INDEPENDENT-MIRROR.md](INDEPENDENT-MIRROR.md).

## What has already been prepared in this GitHub repository?

- A portable root [`plugin.json`](plugin.json) named `neo-superpowers-skills`.
- A GitHub-sourced [Codex marketplace](.agents/plugins/marketplace.json) pointing exclusively to `jjanson123Java/superpowers-skills`.
- All 15 original `skills/<skill-name>/SKILL.md` instructions, including supporting files.
- A mobile-friendly [Skills Guide](SKILLS-INDEX.md) with direct skill links.

**Not yet done:** This GitHub preparation does not install the plugin into your ChatGPT account or change ChatGPT's built-in menus. Plugin installation requires account-side action.

## Verified standalone ZIP package

A portable, skills-only archive is now automatically built by [GitHub Actions — Package Neo Superpowers Skills](https://github.com/jjanson123Java/superpowers-skills/actions/workflows/package-neo-superpowers.yml).

- Validated archive name: `neo-superpowers-skills.zip`.
- Archive contents: the root `plugin.json`, 15 `SKILL.md` definitions and their support files, original `LICENSE`, original-attribution document, and required icon assets.
- GitHub Actions creates an artifact named `neo-superpowers-skills-install`. Download the artifact from the successful run, then extract its inner `neo-superpowers-skills.zip`; the **inner ZIP** is the standalone plugin package to upload.
- The root manifest's short description has been corrected to comply with the 30-character limit.
- Package generation does **not** install or save the personal plugin in ChatGPT. Plugin Creator (or an account-facing plugin save/upload tool) must complete that step.

When using **Plugin Creator** on Android, attach the inner ZIP from the device's Downloads folder and ask: "Save this archive as my personal Neo Superpowers Skills plugin; verify that all 15 skills were ingested and show me the plugin's installed page." Do not upload the **outer GitHub Actions artifact ZIP** in place of the inner plugin ZIP.

## Install as a personal ChatGPT plugin (Android or web)

1. In ChatGPT, open **Plugins** in the sidebar.
2. Install **Plugin Creator** if it is not installed.
3. Start a new chat using **@plugin-creator**, then send the following request.

> Create a personal skills-only plugin named **Neo Superpowers Skills**. Use **my** independent GitHub repository `https://github.com/jjanson123Java/superpowers-skills` as the content source, NOT `obra/superpowers` or an identically named public marketplace plugin. The repository already includes a root `plugin.json`, `.agents/plugins/marketplace.json`, and 15 `skills/*/SKILL.md` folders. Package all fifteen skills along with each skill's referenced scripts, prompts, templates, and references. Keep the skill contents unchanged. Preserve the MIT LICENSE and the original author's attribution. Do not include the upstream MCP server or require any external app to execute instruction-only skills. Give me a personal plugin I can select using `@Neo Superpowers Skills` and show me how to invoke a named skill. If any skill requires subagent or CLI capabilities unavailable on Android, identify those limitations. Do not claim installed until you can confirm the plugin appears in my Plugins > Personal or Installed view.

4. Follow any creator prompts to preview, test, and save/install the plugin.
5. Confirm **Plugins > Personal** or **Installed** shows **Neo Superpowers Skills**. The plugin should be selectable with an `@` mention when your app surface supports it.

**Note:** A single plugin groups all 15 skills; they are not automatically 15 separate entries in the Plugins menu. Ask for a particular skill by name, e.g. `@Neo Superpowers Skills Use systematic-debugging to investigate this error.` The actual invocation syntax and skill picker vary by ChatGPT surface.

## Codex on a development machine (optional)

The repo is also ready to be added as an independent Codex marketplace using the current Codex CLI:

```bash
codex plugin marketplace add jjanson123Java/superpowers-skills
```

Then open the Codex Plugins directory, choose **Neo Superpowers Skills**, install it and test skill discovery. This optional CLI step is not required on your phone. Do not substitute an upstream install command from the original README.

## Verify the installation

Ask the installed personal plugin:

> List the 15 skills in your package, give a one-sentence purpose for each, and link or identify the installed `skills/systematic-debugging/SKILL.md`.

Then try:

> Use the **systematic-debugging** skill to investigate a failing test, gathering evidence and proposing a regression test before code changes.

If the installed version has fewer skills, is named only `superpowers`, or points to `obra/superpowers` instead of your repository, revisit the creator session and specify this GitHub source.

## Scope and independence

This is a one-time independent mirror and an independent plugin package. Updating `obra/superpowers` does not change your repo. Changes in your GitHub repo do not automatically refresh a previously saved personal ChatGPT plugin unless you update or resync that plugin through its supported management workflow.

A skill is a workflow guide, not a standalone executable or a guarantee that ChatGPT can perform every action it describes. Tasks requiring shell scripts, isolated Git worktrees, or subagents depend on the capabilities and permissions of the runtime in which the skill is used.
