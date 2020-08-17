[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Rendering Music notation with ABC)
[#]: via: (https://fedoramagazine.org/rendering-music-notation-with-abc/)
[#]: author: (Stuart D Gathman https://fedoramagazine.org/author/sdgathman/)

Rendering Music notation with ABC
======

![][1]

ABC is a [human readable ascii representation][2] of music notation.  John Chambers posted a [brief history][3] of ABC notation and there is a [newer history][4] by Chris Walshaw.

Unlike [MusicXML][5], which is designed for exchanging music between score editing and performance applications, ABC is designed to be directly edited by humans. I can type a score in ABC with vim much faster than by fiddling with a mouse in a GUI score editor. Unlike other formats ABC works well with version control such as git. As with [Latex][6], what you see is _not_ what you get. But the notation is intuitive, the learning curve is pretty short, and the benefits are awesome.

While often touted as the standard for folk music, it works perfectly for Jazz lead sheets and does [full scores][7] as well. Some GUI score editors can import/export ABC notation. I used [noteedit][8] for a GUI editor until it was abandoned upstream, but was able to export as ABC. The [result][9] is reasonably human readable – letting me continue to edit in ABC notation, and serving as an example of a more complete score. When you are done with this lesson, you’ll be able to turn it into a PDF!

### Ancient 4th Century Hymn

For a folk tune example, we will do a simple arrangement of a 4th century hymn, with a medieval era tune. “O Lux Beata Trinitas” is one of the twelve hymns which the Benedictine editors regarded as undoubtedly the work of [St. Ambrose][10]. It is cited as by St. Ambrose by Hinemar of Rheims in his treatise De unâ et non trinâ Deitate, 857. [Hymnary.org][11]

The hymn was still popular in the Gregorian Chant era. [Here][12] you can see the medieval notation and hear a performance as historically accurate as you will find today.

### 20th Century Interpretations

The medieval notation was updated in hymnals to [more modern notation][13], This is our starting point. As reflected in those hymnals, there were no measures or bar lines in the medieval period.

Here are the basics of ABC:

  * Comments are lines beginning with ‘%’.
  * Notes beginning with “middle C” are entered as CDEFGABcdefgab.
  * Following a note with a number multiplies the timevalue by that number.
  * Notes that are next to each other are joined together whenever possible. This is the only way spaces are significant.
  * Parenthesis are used to tie or slur notes together.
  * The tune begins with X: 1, where 1 is the tune number. There can be multiple tunes in a file. Folk tunes are often collected into a file. For instance, we could collect all 12 known works of St. Ambrose into a single file named ‘ambrose.abc’.
  * The title is given with T:
  * The composer or source is given with C:
  * The key (default is C major) is given with K:



Here is a simple transcription of our tune into ABC:

```
X: 1
T: O lux beata Trinitas
C: Plainsong, Mode VIII
K: D
% Fedora Magazine example
(AB) (AGFG) EFG (AB) (BA) A4
(AB) (AGFG) EFG (AB) (BA) A4
(AB) d (cd) B (AG) (AB)  (AGF) F4
(GA) (AGFG) EFG (AB) (BA) A4
```

We are going to do our work in a terminal emulator. Enter the above with your favorite text editor (bonus points if that is cat) into a file named ‘lux.abc’.
Or [download lux.abc][14] with all the tunes for this lesson. To format and view this, we need ghostscript, xreader, and abcm2ps. You probably have ghostscript and xreader (or other PDF viewer) already installed on a desktop, but it doesn’t hurt to ask again.

```
$ sudo dnf install ghostscript xreader abcm2ps make
```

I had you install make so a simple makefile can simplify rendering:

```
.SUFFIXES:  .abc .ps .pdf .mid
.abc:
    abcm2ps $*
.abc.pdf:
    abcm2ps $*
    ps2pdf Out.ps $*.pdf
.abc.mid:
    abc2midi $*.abc -o $*.mid
```

Enter or [download][15] that as a file named ‘Makefile’. Now format and view our tune:

```
$ make lux.pdf
$ xreader lux.pdf &
```

I had you run xreader in the background, so you can switch back to your terminal. Xreader will update the view whenever lux.pdf is updated. If you are just reading this article, you can also view the output [here][16].

### Adding Lyrics

Lyrics are entered with ‘w:’ under the tune line they go with. Words are hyphenated to show how the syllables go with the notes. Use ’*’ to use additional notes for the last syllable.

Append tune 2 to the lux.abc file, it is the same tune with lyrics:

```
X: 2
T: O lux beata Trinitas
C: Words: St. Ambrose 4th century
C: Plainsong, Mode VIII
K: D
% Fedora Magazine example
(AB) (AGFG) EFG (AB) (BA) A4
w: O*  lux***  be-a-ta trin-* ni-* tas,
(AB) (AGFG) EFG (AB) (BA) A4
w: et* prin-*** ci-pa-lis U-* ni-* tas,
(AB) d (cd) B (AG) (AB)  (AGF) F4
w: i-* am sol* re-ce-* dit* i-*gne-us,
(GA) (AGFG) EFG (AB) (BA) A4
w: in-* fun-***  de lu-men cor-*di-* bus.
```

Now ‘make lux.pdf’ and see the results in your xreader window. Both tunes are rendered to the PDF.

### Adding Measures

So, historical authenticity is all very fine, but I want to make a modern version. The first step for modern ears is to divide the tune into equal sized measures. My ear says that 7/8 is an excellent time signature for this tune.

  * M: 7/8 specifies a default meter of 7/8
  * L: 1/8 specifies a default note length of 1/8 of a whole note. This was already the default, but now it is documented.
  * Q: 1/4=80 specifies a suggested speed: 80 quarter notes per minute.
  * Measures are separated by bar lines represented by ‘|’.
  * There will be multiple verses, so ‘:|’ adds a repeat bar line.
  * A final bar line is ‘||’, but we don’t use it for this example.
  * It is good practice for debugging to divide the lyrics into measures as well, and not rely on automatic distribution.
  * Note that additional spaces can be added for readability.
  * Lining up the bar lines is not required, but can make it more readable.



Here is tune 3 with bar lines (appended to lux.abc):

```
X: 3
T: O lux beata Trinitas (3)
C: Words: St. Ambrose 4th century
C: Plainsong, Mode VIII
M: 7/8
L: 1/8
Q: 1/4=80
K: D
% Fedora Magazine example
z(AB) (AGFG) | EFG     (AB) (BA) | A3-A4 |
w: O*  lux***|be-a-ta trin-* ni-*| tas,  |
z(AB) (AGFG)   |  EFG    (AB) (BA)| A3-A4 |
w: et* prin-***|ci-pa-lis U-* ni-*| tas,  |
 (AB) d (cd)   B (A |G) (AB) (AGF)   F-| F7|
w:i-* am sol* re-ce-|* dit*  i-*gne-us,| * |
z(GA)  (AGFG) | EFG      (AB) (BA) | A3-A4 :|
w:in-* fun-***| de lu-men cor-*di-*|bus. |
```

### Bass Line, Chords, and Verses

Now we begin the real departure in our interpretation. First, chords are added to assist in improvising from a “lead sheet”. Then we add a suggested bass line.

  * V:1 and V:2 switch between voices.
  * Chords are entered in double quotes in the tune line, and are rendered above the following note.
  * Each comma after a note lowers it by an octave.
  * C: can also be used to document arranger and license.
  * Addition verses are added as additional lyric lines under a tune line.
  * Verse numbers can be added by using ‘~’ to join them to the next word with a non-break space. Otherwise they would be counted as words.
  * %%MIDI these are magic comments that are used in the next section!



Here is our final tune for this lesson:

```
X: 4
T: O lux beata Trinitas (4)
C: Words: St. Ambrose 4th century
C: Plainsong, Mode VIII
C: Arranged: Stuart D. Gathman
C: Copyright 2012: Creative Commons Attribution-ShareAlike 2.0
M: 7/8
L: 1/8
Q: 1/4=80
K: D
%%MIDI gchord c3c4
%%MIDI program 75
V:1
"D"z(AB) (AGFG) | "A7"EFG (AB) (BA) | "Dsus"A3-"D"A4 |
w:i.~O*  lux*** |be-a-ta trin-* ni-*| tas,  |
w:ii.~Te* ma-***|ne lau-dum car-*mi-*| ne, |
w:iii.~De-* o***|Pa-tri sit glo-*ri-*| a, |
V:2
   D,3  A,2 A,2 |   E,3  A,2 A,2    | D,3  A,2 A,2 |
V:1
"D"z(AB) (AGFG) | "A7"EFG (AB) (BA) | "Dsus"A3-"D"A4 |
w:  et* prin-***|ci-pa-lis U-*  ni-*| tas,  |
w:  te* de-***  |pre-ce-mur ves-*pe-*|re: |
w:  ei-* us-*** |que so-li   Fi-*li-*| o, |
V:2
   D,3  A,2 A,2 |   E,3  A,2 A,2    | D,3  A,2 A,2 |
V:1
"G"(AB) d (cd) B (A  |"Em"G) (AB)  (AGF)  F-|"D"F7 |
w: i-* am sol* re-ce-|*     dit*  i-*gne-us,| * |
w: te* nos-tra* sup-plex|* glo-*ri-**a | * |
w: cum* Spi-ri-*tu Pa-|* ra-*cli-**to, | * |
V:2
   G,3  B,2 B,2 |   D,3  B,2 B,2    | D,3  A,2 A,2 |
V:1
"A7"z(GA) (AGFG) | "A7"EFG (AB) (BA) | "Dsus"A3-"D"A4 :|
w: in-* fun-***  |  de lu-men cor-*di-*| bus. |
w: per* cunc-*** | ta lau-det sae-*cu-*| la. |
w: et*  nunc,*** |  et in per-pe-*tu-* | um |
V:2
   E,3  A,2 A,2 |   C,3  A,2 A,2    | D,3  A,2 A,2 :|
```

### Rendering to MIDI

Rendering that makes a nice lead sheet! What does it sound like? You will need the abc to MIDI translator and a MIDI renderer. Fedora comes with a number of MIDI synthesizer and rendering options, but we will use timidity – a simple command line utility that can render to audio files or play on your speakers.

Install abcMIDI and timidity:

```
$ sudo dnf install abcMIDI timidity++
```

If you have been following the examples, you have 4 tunes in lux.abc. Render them to midi with the abc2midi utility:

```
$ abc2midi lux.abc
```

This creates four midi files, one for each tune: lux1.mid .. lux4.mid. Use timidity to play each file to your speakers:

```
$ timidity lux1.mid
```

When you play ‘lux4.mid’, you will hear what the ‘%%MIDI’ directives did. You can read more about abc2midi and its directives [here][17]. You can also hear me [singing and playing piano][18] from the lead sheet and totally butchering the Latin.

There is a lot more to ABC, but this has hopefully been a fun introduction!  There are more examples in /usr/share/doc/abcm2ps/examples, and check out [folk tunes from many cultures][19].

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/rendering-music-notation-with-abc/

作者：[Stuart D Gathman][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/sdgathman/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2020/08/rendering-music-notation-abc-816x345.png
[2]: https://abcnotation.com
[3]: http://trillian.mit.edu/~jc/music/abc/doc/ABCtut_History.html
[4]: https://abcnotation.com/history
[5]: https://www.musicxml.com
[6]: https://fedoramagazine.org/latex-typesetting-part-1/
[7]: https://www.ucolick.org/~sla/abcmusic/sym7mov2.html
[8]: https://en.wikipedia.org/wiki/NoteEdit
[9]: https://pagure.io/abcmusic/raw/master/f/se_tu.abc
[10]: https://en.wikipedia.org/wiki/Ambrose
[11]: https://hymnary.org/text/o_lux_beata_trinitas
[12]: https://www.youtube.com/watch?v=5MUWjxoOhLg
[13]: https://hymnary.org/tune/o_lux_beata_trinitas#media
[14]: https://pagure.io/abcmusic/raw/master/f/lux.abc
[15]: https://pagure.io/abcmusic/raw/master/f/Makefile
[16]: https://pagure.io/abcmusic/raw/master/f/lux.pdf
[17]: https://ifdo.ca/~seymour/runabc/abcguide/abc2midi_guide.html
[18]: https://gathman.org/music/ogg/LUX%20MIX_1.ogg
[19]: http://abcnotation.com/browseTunes
