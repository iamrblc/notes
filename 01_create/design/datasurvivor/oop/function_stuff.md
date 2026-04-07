# 2) “embedded smaller functions” (helpers)

Only use nested defs when you truly need to capture local variables for a tiny localized helper. Prefer **private methods** on the class over nested functions, unless you need a closure for a one-off.

- Use `_helper` methods if they need `self` (config, cache, instance state).
    
- Use `@staticmethod` when they don’t touch `self` or `cls`.
    
- Use **module-level** functions if multiple classes will share them.

class SomeThing:
    def __init__(self, scale=1.0):
        self.scale = scale

    def outer(self, x):
        x = self._preprocess(x)
        y = self._core(x)
        return self._postprocess(y)

    def _preprocess(self, x):
        return x * self.scale

    @staticmethod
    def _core(x):
        # pure function helper
        return x ** 2

    def _postprocess(self, y):
        return y + 1
