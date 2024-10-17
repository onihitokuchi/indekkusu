```sh
setxkbmap -layout us -variant intl # setxkbmap -layout us_intl
setxkbmap -layout us

setxkbmap -layout us,us_intl -option grp:alt_shift_toggle
```

~/.config/i3/config
```sh
exec --no-startup-id "setxkbmap -layout us,us_intl -option grp:alt_shift_toggle"
```
