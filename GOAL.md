The `pyromaniac` directory contains some modules from the Pyromanic project. And within it there is a module `riscos/pymods/core/wimp/ploticon.py`. This is an implementation of the icon rendering. We want to create a RISC OS C program that will render icons in the same way as that code.

We are using the GContext library for the rendering. And example is in the current workspace, and can be built with `riscos-amu`.
Validation strings can be handled by some separate code in the `riscos-wimp-validationstrings` directory - this is partially implemented and isn't complete.

Text is going to be rendered by another library. Initially we'll just stub any rendering with some functions that do nothing.
Sprite are going to be rendered by another library. Initially we'll just stub any rendering with some functions that do nothing.

We're only going to focus on the ploticon.py code - we won't convert much else out of the Pyromaniac source. We will need to convert over the iconborders handling code, and the structs, although the GContext library has some of these data structures defined.

We will create separate files for each of the parts of the implementation that are distinct. So we'll create stubs for sprites in c/sprite and text in c/text, for example.

We won't handle colourmapping here - we'll stub that if necessary. Configuration flags and settings should be placed in a structure so that we can change them at runtime. Enumerated values, or values that are indicated by strings in the Python code will be C enums.

We won't change anything in the `pyromaniac` directory.

I have placed some types and constants in the `h/types` file. These should be used in place of the Python constants and structures where possible.

You should try to convert the code from the Python into a set of C files that we can compile and run. I want some tests in a separate file, like we have with the `c/testgcontext` source. Please write some tests that will exercise the icons. The common background for icons is wimp colour 1. You may need to port across a little of the `wimp/palette.py` python module. Text is usually black on this grey wimp colour 1.

To check the tests you can run the program and take a screenshot. You should use a command line `riscos-build-run aif32/PlotIcon,ff8 --command "PlotIcon" --command "screensave -native screen" --return-file screen --return-to screen.png` to send the built code to the build service and return the screenshot in `screen.png`. When you have something interesting, show me it with `host-open screen.png`.

Use any skills that you think you might during the implementation.

Please tell me what you're going to do and then track things with a ToDo list.
