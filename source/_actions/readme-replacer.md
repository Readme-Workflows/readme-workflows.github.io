---
layout: splash
permalink: /readme-replacer/

title: "Readme Replacer"
excerpt: "A GitHub Action to replace placeholders with specific values in a Markdown file."

header:
  overlay_color: "#0d1117"
  actions:
    - label: "<i class='fab fa-discord'></i> Discord"
      url: "https://discord.gg/2a9VC4AK6x"
    - label: "<i class='fab fa-github'></i> GitHub"
      url: "https://github.com/Readme-Workflows/readme-replacer"

custom_js:
  - https://buttons.github.io/buttons.js
---

<a class="github-button" href="https://github.com/Readme-Workflows/readme-replacer/subscription" data-color-scheme="no-preference: dark; light: light; dark: dark;" data-icon="octicon-eye" data-size="large" data-show-count="true" aria-label="Watch Readme-Workflows/readme-replacer on GitHub">Watch</a>
<a class="github-button" href="https://github.com/Readme-Workflows/readme-replacer" data-color-scheme="no-preference: dark; light: light; dark: dark;" data-icon="octicon-star" data-size="large" data-show-count="true" aria-label="Star Readme-Workflows/readme-replacer on GitHub">Star</a>
<a class="github-button" href="https://github.com/Readme-Workflows/readme-replacer/fork" data-color-scheme="no-preference: dark; light: light; dark: dark;" data-icon="octicon-repo-forked" data-size="large" data-show-count="true" aria-label="Fork Readme-Workflows/readme-replacer on GitHub">Fork</a>
<a class="github-button" href="https://github.com/Readme-Workflows/readme-replacer" data-color-scheme="no-preference: dark; light: light; dark: dark;" data-icon="octicon-play" data-size="large" aria-label="Use this GitHub Action Readme-Workflows/readme-replacer on GitHub">Use this GitHub Action</a>

Readme Replacer is a GitHub Action that allows you to define placeholders which should be replaced with another value.  
It also allows evaluation of the replacement value for further customization (i.e. using `new Date().toLocaleString()` to display the current date).

## Workflow setup

{% capture workflow-info %}
Make sure to replace `{version}` with the most recent version available!
{% endcapture %}

<div class="notice--success">
  {{ workflow-info | markdownify }}
</div>

```yaml
name: Replace placeholders

on:
  schedule:
    - cron: '*/30 * * * *' # Activate every 30 minutes
  workflow_dispatch:

jobs:
  replace:
    runs-on: ubuntu-latest
    name: Replace Placeholders in File.
    
    steps:
      - uses: actions/checkout@v2
      - uses: Readme-Workflows/readme-replacer@v1.0.1
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        with:
          # Those are all default values and only are shown for demonstration
          GH_USERNAME: ${{ github.repository_owner }}
          TEMPLATE_FILE: './TEMPLATE.md'
          COMMIT_FILE: './README.md'
          CUSTOM_REPLACER_FILE: './.github/customReplacer.json'
          DATE_FORMAT: "dddd, mmmm dS, yyyy, h:MM:ss TT"
          TIMEZONE: "0"
          COMMIT_MESSAGE: "⚡ Update README by replacing keywords"
          COMMIT_EMAIL: "41898282+github-actions[bot]@users.noreply.github.com"
          COMMIT_NAME: "replacer-bot"
```

### Workflow Options

All below options are **optional** and will use default values when not set!

#### `GH_USERNAME`

> **Default:** `${{ github.repository_owner }}` (Owner of the repository)

Sets the GitHub User to use in this action.

#### `TEMPLATE_FILE`

> **Default:** `./TEMPLATE.md`

Sets the Markdown file that should be used as a template.  
The Action will take the template, replace any set placeholders in it with their respective values and pushes it to the [COMMIT_FILE target](#commit_file).

#### `COMMIT_FILE`

> **Default:** `./README.md`

Sets the target Markdown file that should be pushed towards.  
The result will be the exact same as the [template file](#template_file) but with any defined placeholders replaced.

#### `CUSTOM_REPLACER_FILE`

> **Default:** `./.github/customReplacer.json`

Sets the JSON file to use for the custom placeholder replacements.  
If not set will the action use a specific [default replacements set](https://github.com/Readme-Workflows/readme-replacer/blob/main/src/replacers.json).

The target file has to be a JSON file! See the [Configuration Guide](https://github.com/Readme-Workflows/readme-replacer/wiki/Custom-Replacement-file) for more info.

#### `DATE_FORMAT`

> **Default:** `dddd, mmmm dS, yyyy, h:MM:ss TT`

Sets the date format to use. This is only useful when you're using the `eval` option in the [replacer file](#custom_replacer_file) and use `new Date().toLocaleString` as replacement value.

#### `TIMEZONE`

> **Default:** `0`

Sets the timezone to use. The timezone can either be a GMT-relative number such as `+2:00` or `-2:00` but also a Location String in the format `Country/City`.  
A list of supported Strings can be found [on Wikipedia](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)

#### `COMMIT_MESSAGE`

> **Default:** `⚡ Update README by replacing keywords`

Sets the commit message to use.

#### `COMMIT_EMAIL`

> **Default:** `41898282+github-actions[bot]@users.noreply.github.com`

Sets the Email to use for the committing user.

#### `COMMIT_NAME`

> **Default:** `replacer-bot`

Sets the name to use for the committing user.