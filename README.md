# Hugo Theme: Shell
Terminal-like theme with selectable color schemes.

![Screenshot](https://github.com/Yukuro/hugo-theme-shell/blob/master/images/motion.gif?raw=true)

## Demo site
- https://hugo-theme-shell.netlify.app/

## Features
- Terminal-like portfolio
    - Selectable color schemes
        - `monokai`
        ![monokai](https://github.com/Yukuro/hugo-theme-shell/blob/master/images/monokai.png?raw=true)
        - `powershell`
        ![powershell](https://github.com/Yukuro/hugo-theme-shell/blob/master/images/powershell.png?raw=true)
        - `gruvbox_light`
        ![gruvbox_light](https://github.com/Yukuro/hugo-theme-shell/blob/master/images/gruvbox_light.png?raw=true)
        - `gruvbox_dark`
        ![gruvbox_dark](https://github.com/Yukuro/hugo-theme-shell/blob/master/images/gruvbox_dark.png?raw=true)
        - `solarized_light`
        ![solarized_light](https://github.com/Yukuro/hugo-theme-shell/blob/master/images/solarized_light.png?raw=true)
        - `solarized_dark`
        ![solarized_dark](https://github.com/Yukuro/hugo-theme-shell/blob/master/images/solarized_dark.png?raw=true)
        - `ubuntu`
        ![ubuntu](https://github.com/Yukuro/hugo-theme-shell/blob/master/images/ubuntu.png?raw=true)
        - `retro`
        ![retro](https://github.com/Yukuro/hugo-theme-shell/blob/master/images/retro.png?raw=true)
- Minimal design
- Responsive

## Requirements
- Hugo Version 0.85.0 or higher
    - **Hugo extended version is required**.

## Installation
### Create a new website from scratch
```bash
hugo new site myportfolio
cd myportfolio
git init
git submodule add https://github.com/Yukuro/hugo-theme-shell.git themes/hugo-theme-shell
hugo server -t hugo-theme-shell -w -D
```

### Apply to an existing site
```bash
cd myportfolio
git submodule add https://github.com/Yukuro/hugo-theme-shell.git themes/hugo-theme-shell
hugo server -t hugo-theme-shell -w -D
```

## Configuration
in config.toml
```toml
[Params]
  # Note: This is for the meta description, which is different from the "description" displayed in the terminal.
  description = "Jane Doe's Portfolio!"
  [Params.Terminal]
  # Note: color schema
  # Note: You can choose between
  # Note: ["monokai", "powershell", "gruvbox_light", "gruvbox_dark", "solarized_light", "solarized_dark", "ubuntu", "retro"]
  schema = "monokai"

  # Note: in terminal
  # [userName]@[pcName]:~/$ cd [workDir]
  # [userName]@[pcName]:~/[workDir]$ cat [profile]
  #
  # [description]
  #
  # Note: if you set Params.Tree > user = true
  # [userName]@[pcName]:~/[workDir]$ tree ./[folderName]/
  # ./[folderName]/
  # ...
  # Note: result of the tree command
  userName = "jane"
  pcName = "laptop"
  workDir = "mydir"
  profile = "profile.txt"

  # Note: speed at which text is displayed on the terminal
  terminalDelay = 20

  # Note: speed at which text is displayed on the activity pages
  activityDelay = 5

  description = """
  Hi I am Jane Doe!
  Nice to meet you!

  """

  # Note: If you want to use a Markdown file, you can use the following
  # description = "/description.md"
  # Note: and put the description.md in /content/description.md

  [Params.Tree]
  use = true
  folderName = "my_activity"
  # Note: ["ACTIVITY", "URL or PATH TO YOUR MARKDOWN FILE"]
  files = [ 
    ["C/C++", "https://www.example.com/"],
    ["Python", "https://www.example.com/"],
    ["Go", "https://golang.org/"],
    ["Hugo", "/post/some-activity.md"],
    ["Docker", "/post/some-activity.md"],
  ]
```

## Contributing
Contributions are always welcome!
