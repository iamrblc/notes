# General Shell Stuff

## Check shell

```bash
echo $SHELL
```

## Switch to `zsh`

Temporarily:

```bash
zsh
```

Permanently:

```bash
chsh -s $(which zsh)
```

After this you need to log out and in (or restart the terminal).

## Is there `oh-my-zsh`?

```bash
ls -a ~ | grep .oh-my-zsh
```

Or check ~/.zshrc for OMZ reference.

```bash
grep "oh-my-zsh" ~/.zshrc
```