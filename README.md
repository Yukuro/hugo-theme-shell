# Hugo Theme: Shell
Terminal-like theme with selectable color schemes.

![Screenshot](https://raw.githubusercontent.com/Yukuro/hugo-theme-shell/master/images/motion.gif)

## Demo site
- https://hugo-theme-shell.netlify.app/

## Features
- Terminal-like portfolio
    - Selectable color schemes
        - `monokai`
        ![monokai](https://raw.githubusercontent.com/Yukuro/hugo-theme-shell/master/images/monokai.png)

        - `powershell`
        ![powershell](https://raw.githubusercontent.com/Yukuro/hugo-theme-shell/master/images/powershell.png)

        - `gruvbox_light`
        ![gruvbox_light](https://raw.githubusercontent.com/Yukuro/hugo-theme-shell/master/images/gruvbox_light.png)

        - `gruvbox_dark`
        ![gruvbox_dark](https://raw.githubusercontent.com/Yukuro/hugo-theme-shell/master/images/gruvbox_dark.png)

        - `solarized_light`
        ![solarized_light](https://raw.githubusercontent.com/Yukuro/hugo-theme-shell/master/images/solarized_light.png)

        - `solarized_dark`
        ![solarized_dark](https://raw.githubusercontent.com/Yukuro/hugo-theme-shell/master/images/solarized_dark.png)

        - `ubuntu`
        ![ubuntu](https://raw.githubusercontent.com/Yukuro/hugo-theme-shell/master/images/ubuntu.png)

        - `retro`
        ![retro](https://raw.githubusercontent.com/Yukuro/hugo-theme-shell/master/images/retro.png)
        
- Minimal design
- Responsive
- [MathJax](https://www.mathjax.org/): Beautiful and accessible math in all browsers

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

### How to use Goph theme
hugo-theme-shell supports the [Goph](https://github.com/Mayccoll/Gogh) theme by using [goph-to-stylesheet](https://github.com/Yukuro/goph-to-stylesheet)
1. Choose a Goph theme : you can choose a theme [here](https://mayccoll.github.io/Gogh/).
2. Use goph-to-stylesheet to convert to scss file
```bash
goph-to-stylesheet -t THEME_YOU_CHOSE -i template/shell.scss -o goph.scss
```
3. Copy goph.scss to `assets/sass/goph.scss`
4. Configure your config.toml as follows
```toml
[Params.Terminal]
schema = "goph"
```

## Configuration
in [config.toml](config/_default/config.toml)
```toml
[Params]
  # Note: This is for the meta description, which is different from the "description" displayed in the terminal.
  description = "Jane Doe's Portfolio!"
  [Params.Terminal]
  # Note: color schema
  # Note: You can choose between
  # Note: ["monokai", "powershell", "gruvbox_light", "gruvbox_dark", "solarized_light", "solarized_dark", "ubuntu", "retro"]
  # Note: If you want to use the Goph theme, set it to "goph" (See README.md)
  schema = "monokai"

  # Note: in terminal
  # [userName]@[pcName]:~/$ cd [workDir]
  # [userName]@[pcName]:~/[workDir]$ cat [profile]
  #
  # [description]
  #
  # Note: if you set Params.Tree > use = true
  # [userName]@[pcName]:~/[workDir]$ tree ./[folderName]/
  # ./[folderName]/
  # ...
  # Note: result of the tree command
  userName = "jane"
  pcName = "laptop"
  workDir = "mydir"
  profile = "profile.txt"

  # Note: speed at which text is displayed on the terminal
  # Note: if set to 0, typing animation will be disabled
  # Note:
  # Note: If you want to enable Mathjax, you need to set it to 0
  # Note: and set "math: true" at front matter in your Markdown file
  terminalDelay = 20

  # Note: speed at which text is displayed on the activity pages
  # Note: if set to 0, typing animation will be disabled
  # Note: 
  # Note: If you want to enable Mathjax, you need to set it to 0
  # Note: and set "math: true" at front matter in your Markdown file
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

## trouble shooting
- Hugo build fails
  - What is the version of your Hugo?
  - Shell theme requires Hugo version 0.85.0 or higher and **extended version**
- Post does not show up (return 404 not found)
  - There are two possible causes for this.
    1. Forgot to add -D (--buildDrafts) as an argument to the hugo command
    2. The front matter of the post's .md file has "draft: true" set.

## Contributing
Contributions are always welcome!
