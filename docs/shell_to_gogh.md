# Migration Guide from shell to gogh
Most of the themes used in hugo v0.1.5 and earlier have been deprecated with the introduction of gogh theme.  

### "scheme" in config.coml
| hugo-shell-theme ~v0.1.5 | gogh theme     | 
| ---------------- | -------------- | 
| monokai          | Molokai        | 
| powershell       | PowerShell     | 
| gruvbox_light    | Gruvbox        | 
| gruvbox_dark     | GruvboxDark    | 
| solarized_light  | SolarizedLight | 
| solarized_dark   | SolarizedDark  | 

However, the following themes are left as original.  
The reason for this is that gogh doesn't have a theme or looks bad.

| hugo-shell-theme ~v0.1.5 | hugo-shell-theme v0.1.6~ | 
| ------------------------ | ------------------------ | 
| powershell               | shell-powershell         | 
| ubuntu                   | shell-ubuntu             | 
| retro                    | shell-retro              | 