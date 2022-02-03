# Customize the terminal as you like

## Note
This document explains how to customize the terminal, but it is a temporary solution.\
It is subject to change in future updates.

## 0. Directory structure
The Hugo configuration to be customized looks like this.\
This is the file structure of the hugo-theme-shell [READMD.md](https://github.com/Yukuro/hugo-theme-shell/blob/master/README.md#installation) with all the steps completed.
```bash
$hugo new site mysite
$cd mysite
$tree .
.
├── archetypes
│   └── default.md
├── config.toml
├── content
├── data
├── layouts
├── static
└── themes
      └── hugo-theme-shell
```

## 1. Copy some files to layouts
Hugo 0.42 or later has a feature that allows you to customize the theme without editing the original theme.

In order to customize the terminal, you need to edit the following files
- `hugo-theme-shell/layouts/index.html`
- `hugo-theme-shell/layouts/partials/typeIndex.html`

Copy it to `mysite/layouts`
```bash
$ mkdir -p ./layouts/partials
$ cp themes/hugo-theme-shell/layouts/index.html layouts/partials
$ cp themes/hugo-theme-shell/partials/typeIndex.html layouts/partials
```

## 2. Edit file
In `hugo-theme-shell`, the contents of `config.toml` are passed to `typeIndex.html` according to the [Hugo Template](https://gohugo.io/templates/) written in `index.html`

From here, we will edit the copied file, but the task will vary depending on what you want to do.
- If you want to change only the order of the commands
  - go to chapter 2-A
- If you want to change the order of the commands and change the display of the commands
  - go to chapter 2-B

## 2-A Change only the order of the commands
Here we want to add `[userName]@[pcName]:~/[workDir]$ cat [profile]` between the last line of the teminal and the line before it.

In `typeIndex.html`\
The collection of `span` tags at the beginning is the root of the order of the commands.\
Thus, if you want to add it between the last line and the line before it, add `<span id="ps1_05"></span> <span id="cat2"></span> <br>` at that position.
```html
    <span id="ps1_01"></span> <span id="cd"></span> <br>
    <span id="ps1_02"></span> <span id="cat"></span> <br>
    <span id="std_out_01"></span> <br>
    <span id="ps1_03"></span> <span id="tree"></span> <br>
    <span id="std_out_02"></span> <br>
+++ <span id="ps1_05"></span> <span id="cat2"></span> <br>
    <span id="ps1_04"></span> <br>
```
The id of the `span` tag must be unique.

The javascript in the second half of `typeIndex.html` uses `async/await` to control the typing effect.\
In particular, `typeeffect` is associated with the edited `span` tag, so you need to insert the code in the correct order.
```javascript
const typeeffetct = async () => {
    await typewriter("{{ .env }}", "ps1_01", ps1Delay); await typewriter("{{ .cd }}", "cd", commandDelay);
    await typewriter("{{ .envWithDir }}", "ps1_02", ps1Delay); await typewriter("{{ .cat }}", "cat", commandDelay);
    await typewriter("{{ .description }}", "std_out_01", stdoutDelay);
    await typewriter("{{ .envWithDir }}", "ps1_03", ps1Delay); await typewriter("{{ .tree }}", "tree", commandDelay);
    await typewriter("{{ .leaf }}", "std_out_02", stdoutDelay);
+++ await typewriter("{{ .envWithDir }}", "ps1_05", ps1Delay); await typewriter("{{ .cat }}", "cat2", commandDelay);
    await typewriter("{{ .envWithDir }}", "ps1_04", ps1Delay);
    return;
}
```

## 2-B Change the order of the commands and change the display of the commands
If you want to change the contents of the command, you need to edit `config.toml` and `index.html` additionally in addition to the steps in 2-A.

In this example, after adding `[userName]@[pcName]:~/[workDir]$ cat [profile2]` to the last line of the terminal, we want to display the contents of `[profile2]` (`[description2]`)

In `config.toml`\
In `config.toml`, under `[Params.Terminal]`, set the content you want to display and the name of the property that defines it.\
In this example, we will set `profile2` and `description2`.
```toml
    pcName = "PC"
    workDir = "mydi"
    profile = "profile.log"
+++ profile2 = "profile_other.log"
```

```toml
    contentDelay = 0 # content speed : content in .md file

    description = """
      Hi I am Jane Doe!
      Nice to meet you!
      Wow!
    """

+++ description2 = """
+++   Hi I like apple.
+++   """
```

In `index.html`\
Takes the property name and its contents from `config.toml` and passes it to `typeIndex.html`.\
Here, we create the variables `cat2` and `description2` and pass them to typeIndex.html through `partial`.
```html
      {{ $stdoutDelay :=  $.Site.Params.Terminal.stdoutDelay }}
      {{ $commandDelay := $.Site.Params.Terminal.commandDelay }}

+++   {{ $cat2 := printf "<span id=terminal>cat %s</span>" .Site.Params.Terminal.profile2 | safeHTML }}
+++   {{ $description2 := printf "<span id='terminal'>%s</span>" .Site.Params.Terminal.description2 | safeHTML}}
+++   {{ partial "partials/typeIndex.html" (dict "context" . "env" $env "cd" $cd "envWithDir" $envWithDir "cat" $cat "description" $description "tree" $tree "leaf" $leaf "ps1delay" $ps1Delay "stdoutdelay" $stdoutDelay "commanddelay" $commandDelay "cat2" $cat2 "description2" $description2) }}
```

In `typeIndex.html`\
Basically, what you need to do is the same as in step 2-A.\
Edit the HTML part that controls the display order and the javascript that controls the typing animation.
```html
    <span id="ps1_01"></span> <span id="cd"></span> <br>
    <span id="ps1_02"></span> <span id="cat"></span> <br>
    <span id="std_out_01"></span> <br>
    <span id="ps1_03"></span> <span id="tree"></span> <br>
    <span id="std_out_02"></span> <br>
    <span id="ps1_04"></span> <br>
+++ <span id="ps1_05"></span> <span id="cat2"></span> <br>
+++ <span id="std_out_03"></span> <br>
```

```javascript
const typeeffetct = async () => {
        await typewriter("{{ .env }}", "ps1_01", ps1Delay); await typewriter("{{ .cd }}", "cd", commandDelay);
        await typewriter("{{ .envWithDir }}", "ps1_02", ps1Delay); await typewriter("{{ .cat }}", "cat", commandDelay);
        await typewriter("{{ .description }}", "std_out_01", stdoutDelay);
        await typewriter("{{ .envWithDir }}", "ps1_03", ps1Delay); await typewriter("{{ .tree }}", "tree", commandDelay);
        await typewriter("{{ .leaf }}", "std_out_02", stdoutDelay);
        await typewriter("{{ .envWithDir }}", "ps1_04", ps1Delay);
+++     await typewriter("{{ .envWithDir }}", "ps1_05", ps1Delay); await typewriter("{{ .cat2 }}", "cat2", commandDelay);
+++     await typewriter("{{ .description2 }}", "std_out_03", stdoutDelay);
        return;
    }
```

## Tips
Many of the variables in `typeIndex.html` (`envWithDir, cat ... `) are defined in `index.html`, and have the following meaning
| Variable name | Relation to config.toml |
| ---- | ---- |
| env | `[userName]@[pcName]:~/` |
| envWithDir | `[userName]@[pcName]:~/[workDir]` |
| cd | `cd [workDir]` |
| cat | `cat [profile]` |
| description | `description` |
| tree | `tree [folderName]` |
| leaf | `[folderName] etc` |
| ps1delay | `display speed of [userName]@[pcName]:~/` |
| stdoutdelay | `display speed of [description], [leaf]` |
| commanddelay | `display speed of command(cd [workdir] / cat [profile])` |
