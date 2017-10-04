# Substitute a font with another under Wine

Open `~/.wine/system.reg`. Find the section
`Software\\Microsoft\\Windows NT\\CurrentVersion\\FontSubstitutes`. Add a new
string value under that key, eg.:

```
"Tahoma" = "MS Sans Serif"
```
