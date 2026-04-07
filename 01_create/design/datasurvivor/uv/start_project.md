# Create a new project directory

If you don't have any, of course. In our example this directory will be called `project`. 

In terminal navigate to the [[00_rblc/wellbeing/sport/glossary#Parent directory|parent directory]]:

``` bash
mkdir project # This creates it
cd project   # Now you enter project
```

At the end you should see something like this:

```bash
~/coding/project
```

If you don't see a path right away don't panic. You can always check it with the `pwd` command that stands for print working directory.

# Initialize uv project

Now that we have a project folder, everything will be located here. Your `python` environment(s), your git, etc.

```bash
uv init # This creates the whole project magic
git add . # This adds all the changes to your git repo
git commit -m "Project init" # Just the mandatory start message. The text can be something else, of course but you need to commit.
```
## Set up the virtual environment

If you check your available `python`, you'll see that you are using the global environment. 

```bash
which python3
/usr/bin/python3
```

While this technically works, it's very much not a good practice. So set up your own environment that you want to use.

```bash
uv venv # this creates a virtual environment 
source .venv/bin/activate
```

Done. If you need a different python version than the latest, it's a bit trickier, but still very easy.

