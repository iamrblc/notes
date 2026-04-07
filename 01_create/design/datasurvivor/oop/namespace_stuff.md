# Namespace stuff
## Package importability

### Simp

Store your packages in a dir that's the same as your package import name:

boo/project_utils`
`boo/project_utils/__init__.py`
`boo/project_utils/boo.py`
`boo/project_utils/foo.py`
etc

### Alpha move

Keep your dir structure descriptive, but make the package name user friendly by proper setup in `pyproject.toml` (recommended way):

```toml
[project]
name = "boo"
packages = ["boo_utils"]
```

Alternatively, it can be in a `setup.py` file:

```python
setup(
	name = "boo",
	packages = ["boo_utils"],
	)
```
**2. Keep `strelka_utils` as the folder but publish/install under the name `strelka`**  
When you create your `pyproject.toml` or `setup.py`, you set:

`[project] name = "strelka" packages = ["strelka_utils"]`

or in `setup.py`:

`setup(     name="strelka",     packages=["strelka_utils"], )`

