# Detached Interactive Shell

## Launching an interactive shell

An **interactive** shell is a shell connected to your standard input. The easiest example is the shell you see when you open up a terminal. You can execute a command through your keyboard, get the instant result, browse your filesystem, and so on. You get the idea. Trivially, the opposite thing is a **non-interactive** shell. You can't (or _don't want to) do any of those things on your non-interactive shell because it's mainly used to execute a command given to the shell before the execution.

`bash` takes advantage of this definition to decide if a new `bash` instance should be interactive or non-interactive. That is, if the standard input of the new `bash` instance is your keyboard, it assumes it should be an interactive shell, otherwise a non-interactive shell. 

Why is it relevant to `tmox`? Because `tmox` will have to redirect the standard input to somewhere user-controllable (without `root`). A non-privileged user (i.e., non-`root`) cannot directly access or control any physical device such as a keyboard, so there is no way to redirect the standard input to something acting as a physical device (as far as I know). So our second best bet is to redirect it to a user-controllable file (say, the file belonging to the user), but it'll make our new `bash` instance **non-interactive** because the standard input is not a keyboard ("character device" in a technical term). So if you launch `bash` and redirect its input to a file, the resulting `bash` instance is not the same as the one you see in your terminal; different formatting from `ls`, complaints from any `ncurses` applications, and so on. Simply speaking, it's not compatible with some terminal applications.

But in this case, the solution is **very** simple. You just need the `-i` flag when you launch `bash`. It instructs your `bash` instance to be an interactive shell no matter what. Simple as that.

## 
