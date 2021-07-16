# Hugo Theme: Shell
Terminal-like theme with selectable color schemes.

![Screenshot](https://github.com/Yukuro/hugo-theme-shell/blob/master/images/motion.gif?raw=true)

## Demo site
- https://hugo-theme-shell.netlify.app/

## Features
- Terminal-like portfolio
    - Selectable color schemes
        - `monokai`, `powershell`, `gruvbox_light`, `gruvbox_dark`, `solarized_light`, `solarized_dark`, `ubuntu`, `retro`.
- Minimal design
- Responsive

## Requirements
- Hugo Version 0.84.0 or higher
    - Hugo extended version is required.

## Installation
### Create a new website from scratch
```bash
hugo new site myportfolio
cd myportfolio
git init
git submodule add https://github.com/Yukuro/hugo-theme-shell.git themes/hugo-theme-shell
hugo server -t hugo-theme-shell -w
```

### Apply to an existing site
```bash
cd myportfolio
git submodule add https://github.com/Yukuro/hugo-theme-shell.git themes/hugo-theme-shell
hugo server -t hugo-theme-shell -w
```

## Configuration
in config.toml
```toml
[Params]
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
