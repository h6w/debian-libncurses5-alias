# debian-libncurses5-alias
Builds a very simple package that pretends that libncurses5 is installed.

Once upon a time, libncurses was packaged in Debian / Ubuntu / Whatever as "libncurses".

At some point, it reached version 5.   Since it was possible to have both versions installed on the same machine, and version 5 was quite different, the new package was called libncurses5.

When libncurses reached version 6, it stayed as libncurses5 for many years for backward compatibility, and apt would even select "libncurses5 (>= 6.0.0)".

At some point, it was decided to roll forward the package name to libncurses6, for similar reasons as in the earlier part of this story.  Asking apt to install libncurses5 simply installed libncurses6 and then you might have just had to symlink the files and everyone was happy.

However, many packages, particularly old packages from (long since not supported) commercial sources for hardware like LSI, along with some Debian-based distributions, still continued to refer to the debian package as "libncurses5".

So, this is a package that depends on libncurses6 but allows apt to believe that libncurses5 is actually installed so that it, too, can install.

And they all ran happily ever after.

...... except ......

You still need to symlink:
ln -s /usr/lib/i386-linux-gnu/libncurses.so.6 /usr/lib/i386-linux-gnu/libncurses.so.5
ln -s /usr/lib/x86_64-linux-gnu/libncurses.so.6 /usr/lib/x86_64-linux-gnu/libncurses.so.5

THE END
