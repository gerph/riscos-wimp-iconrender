The `pyromaniac` directory contains some modules from the Pyromanic project. And within it there is a module `riscos/pymods/core/wimp/ploticon.py`. This is an implementation of the icon rendering. We want to create a RISC OS C program that will render icons in the same way as that code.

We are using the GContext library for the rendering. And example is in the current workspace, and can be built with `riscos-amu`.
Validation strings can be handled by some separate code in the `riscos-wimp-validationstrings` directory - this is partially implemented and isn't complete.

Text is going to be rendered by another library. Initially we'll just stub any rendering with some functions that do nothing.
Sprite are going to be rendered by another library. Initially we'll just stub any rendering with some functions that do nothing.

We're only going to focus on the ploticon.py code - we won't convert much else out of the Pyromaniac source. We will need to convert over the iconborders handling code, and the structs, although the GContext library has some of these data structures defined.

We will create separate files for each of the parts of the implementation that are distinct. So we'll create stubs for sprites in c/sprite and text in c/text, for example.

We won't handle colourmapping here - we'll stub that if necessary. Configuration flags and settings should be placed in a structure so that we can change them at runtime. Enumerated values, or values that are indicated by strings in the Python code will be C enums.

We won't change anything in the `pyromaniac` directory.
