# Netcat Interactive
Netcat Interactive is a python wrapper around Netcat (nc), to change a
bind or reverse shell to a Linux machine, into a **interactive** 
shell.

## How to Use
Use this on the attacker machine. Make sure `nc` is available in your
`PATH`, then use `nc-ai` just as you would use `nc`. For example on
the attacker machine execute the following to get a reverse shell:
```
nc-ai -nvlp 4444
...
nc-ai -nv 127.0.0.1 4444
```

When you have a connection and a plain shell, press `ESC` to upgrade the shell to a
interactive shell.

## Limitations
Only works for Linux...  
Only tested on kali...  
Only tried with bash...  

Netcat binary should be in PATH and be called `nc`.

Probably more...

## Issues
When waiting for a victim to connect to us, `CTRL-C` does not stop the script.

## References
The solution is based on the following blog:
https://blog.ropnop.com/upgrading-simple-shells-to-fully-interactive-ttys/

In short:
```bash
# In reverse shell
$ python -c 'import pty; pty.spawn("/bin/bash")'
Ctrl-Z

# In Kali
$ stty raw -echo
$ fg

# In reverse shell
$ reset
$ export SHELL=bash
$ export TERM=xterm-256color
$ stty rows <num> columns <cols>
```

The stdout/stderr/stdin redirection is based on the following:
https://stackoverflow.com/questions/31926470/run-command-and-get-its-stdout-stderr-separately-in-near-real-time-like-in-a-te/31953436#31953436
