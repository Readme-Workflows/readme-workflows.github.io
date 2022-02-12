---
layout: splash
permalink: /recent-activity/

title: "Recent Activity"
excerpt: "A GitHub Action to display your most recent activities on GitHub!"

header:
  overlay_color: "#0d1117"
  actions:
    - label: "<i class='fab fa-discord'></i> Discord"
      url: "https://discord.gg/2a9VC4AK6x"
    - label: "<i class='fab fa-github'></i> GitHub"
      url: "https://github.com/Readme-Workflows/recent-activity"

custom_js:
  - https://buttons.github.io/buttons.js
---

<a class="github-button" href="https://github.com/Readme-Workflows/recent-activity/subscription" data-color-scheme="no-preference: dark; light: light; dark: dark;" data-icon="octicon-eye" data-size="large" data-show-count="true" aria-label="Watch Readme-Workflows/recent-activity on GitHub">Watch</a>
<a class="github-button" href="https://github.com/Readme-Workflows/recent-activity" data-color-scheme="no-preference: dark; light: light; dark: dark;" data-icon="octicon-star" data-size="large" data-show-count="true" aria-label="Star Readme-Workflows/recent-activity on GitHub">Star</a>
<a class="github-button" href="https://github.com/Readme-Workflows/recent-activity/fork" data-color-scheme="no-preference: dark; light: light; dark: dark;" data-icon="octicon-repo-forked" data-size="large" data-show-count="true" aria-label="Fork Readme-Workflows/recent-activity on GitHub">Fork</a>
<a class="github-button" href="https://github.com/Readme-Workflows/recent-activity" data-color-scheme="no-preference: dark; light: light; dark: dark;" data-icon="octicon-play" data-size="large" aria-label="Use this GitHub Action Readme-Workflows/recent-activity on GitHub">Use this GitHub Action</a>

Recent Activity is a GitHub Action that allows you to display your most recent actions on GitHub in an ordered list.

The Action can be used for your profile readme, but can also be included in any repository with the right configuration.

## Workflow setup

{% capture workflow-info %}
Make sure to replace `{version}` with the most recent version available!
{% endcapture %}

<div class="notice--success">
  {{ workflow-info | markdownify }}
</div>

```yaml
name: Update README

on:
  schedule:
    - cron: '*/30 * * * *' # Update every 30 minutes
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    name: Update Profile README

    steps:
      - uses: actions/checkout@v2.3.4
      - uses: Readme-Workflows/recent-activity@{version}
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        with:
          # Those are all default values and only are shown for demonstration
          GH_USERNAME: ${{ github.repository_owner }}
          CONFIG_FILE: "./.github/recent-activity.config.yml"
```

### Workflow Options

All below options are **optional** and will use default values when not set!

#### `GH_USERNAME`

> **Default:** `${{ github.repository_owner }}` (Owner of the repository)

This setting allows to set what user should be used for the displayed activity.  
This can be useful in cases where you display the activity on something like an Organisation Profile Page.

#### `CONFIG_FILE`

> **Default:** `./.github/recent-activity.config.yml`

This setting allows you to set a specific YAML configuration as the config for the GitHub Action.  
The GitHub Action will pull all settings from this file. If one isn't found will a default value be used.

Please refer to the [Configuration Guide](https://github.com/Readme-Workflows/recent-activity/wiki/Configuration) for further information.