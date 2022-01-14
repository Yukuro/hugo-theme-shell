# Hugo Theme: Shell
Terminal-like theme with selectable color schemes.

![Screenshot](https://raw.githubusercontent.com/Yukuro/hugo-theme-shell/master/images/motion2.gif)

## Demo site
- https://hugo-theme-shell.netlify.app/

## Features
- Terminal-like portfolio
- Selectable color schemes
  - [Mayccoll/Gogh](https://github.com/Mayccoll/Gogh) theme
    - `Molokai`  
    ![Molokai](https://raw.githubusercontent.com/Yukuro/hugo-theme-shell/master/images/v0.1.6/Molokai.png)

    - `Dracula`  
    ![Dracula](https://raw.githubusercontent.com/Yukuro/hugo-theme-shell/master/images/v0.1.6/Dracula.png)

    - `Gruvbox`  
    ![Gruvbox](https://raw.githubusercontent.com/Yukuro/hugo-theme-shell/master/images/v0.1.6/Gruvbox.png)

    - `Material`  
    ![Material](https://raw.githubusercontent.com/Yukuro/hugo-theme-shell/master/images/v0.1.6/Material.png)

    - `Tender`  
    ![Tender](https://raw.githubusercontent.com/Yukuro/hugo-theme-shell/master/images/v0.1.6/Tender.png)
  - hugo-shell-theme ~v0.1.5 theme
    - `shell-powershell`  
    ![shell-powershell](https://raw.githubusercontent.com/Yukuro/hugo-theme-shell/master/images/v0.1.6/shell-powershell.png)

    - `shell-ubuntu`  
    ![shell-ubuntu](https://raw.githubusercontent.com/Yukuro/hugo-theme-shell/master/images/v0.1.6/shell-ubuntu.png)

    - `shell-retro`  
    ![shell-retro](https://raw.githubusercontent.com/Yukuro/hugo-theme-shell/master/images/v0.1.6/shell-retro.png)
        
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

#### Note: How to use stable version
After running `git submodule add`, do the following
```bash
cd themes/hugo-theme-shell
git checkout TAG_FOR_STABLE_VERSION
```
`TAG_FOR_STABLE_VERSION` : The stable version tag can be found on the [release page of my repository](https://github.com/Yukuro/hugo-theme-shell/releases) (i.e. `v0.1.5`, `v0.1.4` ...etc).

### How to use theme
hugo-theme-shell supports the [Mayccoll/Gogh](https://github.com/Mayccoll/Gogh) theme
1. Choose a Goph theme : you can choose a theme [here](https://mayccoll.github.io/Gogh/).
2. Copy the name of the theme you selected
3. Configure your config.toml as follows
  ```toml
  [Params.Terminal]
  scheme = "THEME_NAME"
  ```

#### Note
Most of the themes used in hugo v0.1.5 and earlier have been deprecated with the introduction of Mayccoll/Gogh theme.  
See [here](https://github.com/Yukuro/hugo-theme-shell/blob/master/docs/shell_to_gogh.md) for details.  

## Configuration
in [config.toml](config/_default/config.toml)
```toml
[Params]
  # Note: This is for the meta description, which is different from the "description" displayed in the terminal.
  description = "Jane Doe's Portfolio!"
  [Params.Terminal]
  # Note: color scheme
  # Note: You can choose between
  # Note: hugo-theme-shell original: ["shell-powershell", "shell-ubuntu", "shell-retro"]
  # Note: or
  # Note: gogh theme: https://mayccoll.github.io/Gogh/
  scheme = "Molokai"

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
  # Note: if you want to enable Mathjax, you need to set it to 0
  # Note: and set "math: true" at front matter in your Markdown file
  ps1Delay = 0 # prompt speed : [userName]@[pcName]:~/$ , [userName]@[pcName]:~/[workDir]$
  stdoutDelay = 0 # stdout speed : [description] , files in Params.Tree
  commandDelay = 50 # command speed : cd [workDir] , cat [profile] , tree ./[folderName]/

  # terminalDelay = 20 : deprecated

  # Note: speed at which text is displayed on the activity pages
  # Note: if set to 0, typing animation will be disabled
  # Note: 
  # Note: if you want to enable Mathjax, you need to set it to 0
  # Note: and set "math: true" at front matter in your Markdown file
  titleDelay = 0 # title speed : "title" in front matter
  contentDelay = 0 # content speed : content in .md file

  # activityDelay = 5 : deprecated

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
