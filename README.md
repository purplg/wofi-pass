# wofi-pass
```
Usage: wofi-pass [options]
	-h, --help		show this help message
	-s, --squash-choice	don't show field choice if password file only contains password
	-t, --type		type the selection instead of copying to clipboard
```

Since `wofi` isn't a drop-in replacement for `rofi`, I couldn't use 
[rofi-pass](https://github.com/carnager/rofi-pass) anymore. So, I just made a 
version of `passmenu` that accomplishes everything I needed from `rofi-pass`. 

## What does it do?
This script uses [wofi](https://hg.sr.ht/~scoopta/wofi) and 
[ydotool](https://github.com/ReimuNotMoe/ydotool) to provide a completely 
Wayland-native way to conveniently use [pass](https://www.passwordstore.org/). 
It provides the same search that `passmenu` does, but shows a second dialogue 
that lets the user choose which field to copy/print.

It also assumes that [pass-otp](https://github.com/tadfisher/pass-otp) is 
installed if an `otpauth://...` string is present in a password file.

The script assumes password files are formatted like the following:
```
Th3Gr3at3stPassw0rd
username: JohnDoe
email: john@example.com
otpauth://totp/example?secret=ABCDCBABCDCBABCD
pin: 1234
```
Note that the password is **ALWAYS** on the first line.

The `-s | --squash` flag tells `wofi-pass` to "intelligently" skip 
the field choice dialogue when there is only a password in the file.

The `-t | --type` flag tells `wofi-pass` to type the choice instead of copying 
to clipboard. This also enables the autotype choice which types 
`username :tab password`.

## Disclaimer???
I know this script needs some work; it was mostly hacked together in an 
afternoon to get the minimum functionality I needed.
