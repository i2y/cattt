# :cat: Cattt
Cattt (kˈæt) is a pure Python cross-platform UI framework.

[Documentation Site](https://i2y.github.io/cattt)

## Goals
The primary final goal of Cattt is to provide features for Python programmers easy to create a GUI application for several OS platforms and web browsers in a single most same code as possible as. The second goal is to provide a UI framework that Python programmers can easily understand, modify, and extend as needed.

## Features
- The core part as a UI framework of Cattt is written in only Python. It's not a wrapper for existing something written in other programing languages.
- Cattt allows human to define UI declaratively in Python.
- Cattt provides hot-reloading or hot-restarting on development.
- Dark mode is supported. If the runtime environment is in dark mode, Cattt app's UI appearance will automatically be styled in dark mode. The default color scheme for light and dark mode might be very like the one of GitHub.

## Dependencies
- For desktop platforms, Cattt is standing on existing excellent python bindings for window management library (GLFW or SDL2) and 2D graphics library (Skia).
- For web browsers, Cattt is standing on awesome Pyodide/PyScript and CanvasKit (Wasm version of Skia).

## Installation
https://i2y.github.io/cattt/getting-started/

## An example of code using Cattt
```python
from cattt.core import App, Button, Column, Component, Row, State, Text
from cattt.frame import Frame


class Counter(Component):
    def __init__(self):
        super().__init__()
        self._count = State(0)

    def view(self):
        return Column(
            Text(self._count),
            Row(Button("Up").on_click(self.up), Button("Down").on_click(self.down)),
        )

    def up(self, _):
        self._count += 1

    def down(self, _):
        self._count -= 1


App(Frame("Counter", 800, 600), Counter()).run()
```

<video src="docs/videos/counter_glfw.mp4" controls="controls">
</video>

You can see some other examples in [examples](examples) directory.

## Supported Platforms
Currently, Cattt theoretically should support not-too-old versions of the following platforms.

- Windows 10/11
- Mac OS X
- Linux
- Web browsers

Unfortunately, however, I could not actually confirm this at all on Linux, as I don't have a Linux machine these days. I want it..

## License
MIT License

Copyright (c) 2022 Yasushi Itoh

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NON-INFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
