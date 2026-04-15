[#]: subject: "GDB source-tracking breakpoints"
[#]: via: "https://fedoramagazine.org/gdb-source-tracking-breakpoints/"
[#]: author: "Alexandra Petlanova Hajkova https://fedoramagazine.org/author/ahajkova/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

GDB source-tracking breakpoints
======

![][1]

GDB Archer Fish by Andreas Arnez

One of the main abilities of a debugger is setting breakpoints.
[GDB: The GNU Project Debugger][2] now introduces an experimental feature
called source-tracking breakpoints that tracks the source line a breakpoint
was set to.

### Introduction

Imagine you are debugging: you set breakpoints on a bunch of
source lines, inspect some values, and get ideas about how to change your
code. You edit the source and recompile, but keep your GDB session running
and type run to reload the newly compiled executable. Because you changed
the source, the breakpoint line numbers shifted. Right now, you have to
disable the existing breakpoints and set new ones.

GDB source-tracking breakpoints change this situation. When you set a
breakpoint using _file:line_ notation, when this feature is enabled, GDB
captures a small window of the surrounding source code. When you recompile
and reload the executable, GDB adjusts any breakpoints whose lines shifted
due to source changes. This is especially helpful in ad-hoc debug sessions
where you want to keep debugging without manually resetting breakpoints
after each edit-compile cycle.

### Setting a source-tracking breakpoint

To enable the source-tracking feature, run:

(gdb) set breakpoint source-tracking enabled on

Set a breakpoint using file:line notation:

(gdb) break myfile.c:42
_Breakpoint 1 at 0x401234: file myfile.c, line 42._

GDB now tracks the source around this line. The info breakpoints command
shows whether a breakpoint is tracked:

(gdb) info breakpoints
_Num Type Disp Enb Address What
1 breakpoint keep y 0x0000000000401234 in calculate at myfile.c:42
source-tracking enabled (tracking 3 lines around line 42)_

Now edit the source — say a few lines are added above the breakpoint,
shifting it from line 42 to line 45. After recompiling and reloading the
executable with run, GDB resets the breakpoint to the new line and displays:

_Breakpoint 1 adjusted from line 42 to line 45._

Run info breakpoints again to confirm the new location:

(gdb) info breakpoints
_Num Type Disp Enb Address What
1 breakpoint keep y 0x0000000000401256 in calculate at myfile.c:45
source-tracking enabled (tracking 3 lines around line 45)_

As you can see, GDB updated the breakpoint line to match the new location.

### Limitations

The matching algorithm requires an exact string match of the captured source
lines. Whitespace-only changes or trivial reformatting of the tracked lines
will confuse the matcher and may cause the breakpoint not to be found.

GDB only searches within a 12-line window around the original location. If
the code shifted by more than that — for example, because a large block was
inserted above — the breakpoint will not be found. GDB will keep the
original location and print a warning:

_warning: Breakpoint 1 source code not found after reload, keeping original
location._

Source context cannot be captured when a breakpoint is created pending
(e.g., with set breakpoint pending on), because no symbol table is available
yet. When the breakpoint later resolves to a location, it will not be
source-tracked.

Source tracking is not supported for ranged breakpoints (set with
break-range).

Breakpoints on inline functions that expand to multiple locations are not
source-tracked, as each location may have moved differently.

### How to try this experimental feature

This feature is not yet available in a stable GDB release. There are two
ways to try it.

#### Install from COPR (for Fedora users)

A pre-built package is available through a COPR repository. Enable it and
install:

sudo dnf copr enable ahajkova/GDB-source-tracking-breakpoints
sudo dnf upgrade gdb

To disable the repository again after testing:

sudo dnf copr disable ahajkova/GDB-source-tracking-breakpoints

The COPR project page is at:
[https://copr.fedorainfracloud.org/coprs/ahajkova/GDB-source-tracking-breakpo
ints/][3]

#### Build from source

  1. Clone the GDB repository:
git clone git://sourceware.org/git/binutils-gdb.git
cd binutils-gdb
  2. Download and apply the patch from the upstream mailing list:
<https://sourceware.org/pipermail/gdb-patches/2026-April/226349.html>
  3. Build GDB:
mkdir build && cd build
../configure --prefix=/usr/local
make -j$(nproc) all-gdb
  4. Run the newly built GDB:
./gdb/gdb



### Conclusion

GDB source-tracking breakpoints are an experimental feature currently under
upstream review and not yet available in a stable GDB release. This link
<https://sourceware.org/gdb/current/onlinedocs/gdb.html/Set-Breaks.html>
covers all available breakpoint commands. If you try this feature out and
hit any kind of unexpected behavior, feedback is very welcome — you can
follow and respond to the upstream patch discussion on the GDB mailing list
at <https://sourceware.org/pipermail/gdb-patches/2026-April/226349.html>

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/gdb-source-tracking-breakpoints/

作者：[Alexandra Petlanova Hajkova][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/ahajkova/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/04/GDB_Archer_Fish_by_Andreas_Arnez-816x345.jpg
[2]: https://www.gnu.org/software/gdb/
[3]: https://copr.fedorainfracloud.org/coprs/ahajkova/GDB-source-tracking-breakpoints/
