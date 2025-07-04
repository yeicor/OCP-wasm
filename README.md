# OCP.wasm — CAD Modeling in the Browser with WebAssembly & Pyodide

OCP.wasm brings the full power of [build123d](https://build123d.readthedocs.io/) —the intuitive Pythonic 3D CAD library—
directly into your browser.

No installs. No setup. 100% private browser-native code-first CAD.

## Quick Start

Go to [the Pyodide REPL](https://pyodide.org/en/stable/console.html) and run the following code:

```py
import micropip, asyncio

micropip.set_index_urls(["https://yeicor.github.io/OCP.wasm", "https://pypi.org/simple"])
micropip.add_mock_package("py-lib3mf", "2.4.1", modules={
    "py_lib3mf": '''import micropip; import asyncio; asyncio.run(micropip.install("lib3mf")); from lib3mf import *'''})  # Only required for build123d<0.10.0
asyncio.run(micropip.install(["build123d", "sqlite3"]))

# Replace the following lines with your own build123d script.
from build123d import Box

b = Box(1, 2, 3)
assert b.volume == 6, "Box volume should be 6!"
```

Performance and support may vary across browsers.

## Projects using OCP.wasm

- [build123dWebAssmGenDemo](https://github.com/Radther/build123dWebAssmGenDemo): A web-based 3D model generator that
  creates parametric models using Python and WebAssembly ([demo](https://radther.github.io/build123dWebAssmGenDemo/)).
