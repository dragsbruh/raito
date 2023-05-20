# Raito

[![Made with Python](https://img.shields.io/badge/Made%20with-Python-blue.svg)](https://www.python.org/)
[![GPL License](https://img.shields.io/badge/License-MIT-orange)](https://opensource.org/license/mit/)
[![Made for Pygame](https://img.shields.io/badge/Made%20for-Pygame-red.svg)](https://www.pygame.org/)
## What is Raito?

Raito is a toolkit specifically designed for game developers who use Python and Pygame.

Currently, Raito offers one main tool:

- Asset Packaging: This tool allows you to convert an asset folder into a single file and restrict users from modifying game assets.

Raito's asset packaging tool creates a .rasp file that contains all your asset files and provides you with a unique key to access these files.

To convert an assets folder to a .rasp file, follow these steps:

```shell
$ ls
assets
myfile.py
$ raito -p -f assets/ -o assets.rasp
RASP: Packaging folder "/path/to/assets/"...
RASP: Detected <num> files
RASP: Done! USE KEY: <key>
$ ls
assets
myfile.py
assets.rasp
```

Let's break down what's happening in the command:

- `-f [PATH]`: Specifies the input folder.
- `-o [PATH]`: Specifies the output file (default: assets.rasp).
- `-k [KEY]`: Uses a custom key (default: randomly generated).

Importing .rasp files:

```python
import pygame
import raito  # Make sure you have raito.py in your working directory

pygame.init()

assets = raito.assets.Assets("path/to/file.rasp", "<key>")

# Your code

my_sprite = assets.image("my_sprite.png")  # Returns the surface loaded with pygame.image.load()
my_audio = assets.audio("my_audio.wav")  # Returns the sound loaded with pygame.mixer.Sound()
my_text = assets.plain("my_file.txt")  # Returns the plain text content of the file

file_object = assets.file("my_sprite.png")  # Returns a file object (equivalent to using open())
```

For development purposes, you can skip compiling to .rasp by importing assets like this:

```python
assets = raito.dev.Assets("path/to/assets")
```

This allows Raito to directly access files from the assets folder, eliminating the need to compile assets every time you make modifications.

Please note that this project is still in development and may have some issues that need to be addressed.

