# Netcat Interactive
Netcat Interactive is a python wrapper around Netcat (nc), to change a
bind or reverse shell to a Linux machine, into a **interactive** 
shell.

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
