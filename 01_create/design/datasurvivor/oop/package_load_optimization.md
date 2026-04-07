
# Optimize loading packages
1. **Keep `__init__.py` light.** Maybe expose only symbols and small utils.
2. **Lazy-import heavy deps inside functions/classes**
3. Soft/otpional deps:
	1. declare core deps in `pyproject.toml`
	2. put heavy/specialized ones in `extra_require` (e.g., `pip install strelka-utils[audio,plots]`)
	3. on use wrap with try/except ImportError` and raise a clear message: “Install with `pip install strelka-utils[audio]`”.
4. **Module-level loaders.** Use tiny helper `require("torchaudio", extra = "audio")` that imports and gives a friendly error.
5.   **Lazy submodules (advanced):** Use `package.__getattr__` (PEP 562) to lazily import subpackages on first access.