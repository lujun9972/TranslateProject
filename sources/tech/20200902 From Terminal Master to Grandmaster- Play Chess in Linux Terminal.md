[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (From Terminal Master to Grandmaster: Play Chess in Linux Terminal)
[#]: via: (https://itsfoss.com/play-chess-linux-terminal/)
[#]: author: (Chinmay https://itsfoss.com/author/chinmay/)

From Terminal Master to Grandmaster: Play Chess in Linux Terminal
======

You know Linux terminals can be fun too!

You can [run some funny Linux commands][1] for amusement. You can also [play games in Linux terminal][2].

Yes! You heard it right. You can play games in the terminal and in this #TerminalTuesday series, I’ll show you how to play chess in Linux terminal.

You might be thinking, “why would anyone want to play chess in the terminal ?!”. I say, it’s a lot of fun. It is also challenging if you play against [Stockfish][3].

Yes, there’s [GNU Chess][4] available, but it is not visually appealing and the chess engine “keeps thinking” for a long time.

I’m talking about an alternative to GNU Chess. Here are a few reasons you might enjoy this one better.

  * You get to play against one of the strongest chess engine, [Stockfish][3]. Here are the rankings for all the [computer chess engines][5].
  * Visually looks way better than GNU Chess and is relatively faster as well.
  * You’ll learn how to describe chess moves in algebraic notation.
  * I figured that a pretty good chunk of It’s FOSS readers are geeks/nerds and that you guys would enjoy it.



To install terminal chess you need two components, the **Stockfish** chess engine and **chs** which is the UI which plugs into the chess engine.

### Installing Chess in Linux terminal with Stockfish and chs

![][6]

The terminal commands here are for Ubuntu or Ubuntu based distributions since a lot of people use them. These commands were tested on Ubuntu 20.04.

You can use your distribution’s package manager for installing the mentioned software.

```
sudo apt install stockfish
```

Running the above command will install the latest version of the Stockfish chess engine.

chs is the UI which plugs into the chess engine. It is written in python3 and you can install it using pip3 the python package manager.

First, [install PIP on Ubuntu][7] with this command:

```
sudo apt install python3-pip
```

Once you have pip3 installed, run the below command to install chs.

```
pip3 install chs
```

#### Cofiguring chs

After installing chs, you’ll see an error message saying chs is not on PATH. At this point if you try to launch chs, the terminal won’t know where to launch it from.

![][8]

You can use the following command to fix the problem

```
export PATH="$PATH:$HOME/ .local/bin"
```

If you try to launch chs from the terminal, you’ll see a “FileNotFoundError”. This is a known bug in chs, it is not able to find the Stockfish chess engine to launch it.

To fix this issue we need to make a small edit in the chs python code. The file we are interested in will be located at **/.local/lib/python3.X/site-packages/chs/engine/stockfish.py**

Make sure to replace the the 3.X in the python version with the one installed on your computer. You can check the python version using the below command.

```
python3 -V
```

For me, it was Python 3.8. You can [use Nano editor][9] or your choice of text editor and open up the file.

```
sudo nano ~/.local/lib/python3.8/site-packages/chs/engine/stockfish.py
```

![][10]

In the line 13 of the code you’ll see _engine_path = ‘stockfish_10_x64_linux’_, you have to replace _‘stockfish_10_x64_linux’_ like this

```
engine_path = "/usr/games/stockfish"
```

![][11]

Now you’re finally done with all the setup. Type **chs** in the terminal to launch the game. This launches chs at level 1 difficulty.

You can specify the level of difficulty of the while launching the game as shown below.

```
chs level=8
```

![][12]

### Playing chess in Linux terminal

You play terminal chess using the algebraic notation (the name sounds complicated but it is quite simple) to describe the moves.

I’ll summarize a short version of how to play using algebraic notation, for detailed information you can check out [this article][13]. Chess pieces are represented by a single letter.

  * Knight – N
  * Rook – R
  * Queen – Q
  * King – K
  * Bishop – B
  * Pawns – blank, they don’t have an associated letter.



The chess board columns are represented by letters **a** to **h** and rows are represented by numbers **1** – **8**. To move your pawn in the position a2 to a4 you just write **a4**.

![][14]

To move your knight(N) from g1 to h3 you would write **Nh3**.

![][15]

To capture a pawn you have to add an **x** in the command. Here I’m trying to capture the bishop(B) which is in the position c4 using my knight(N). The command for this is **Nxc4**.

![][16]

The Stockfish engine also gives you suggestions when you type an invalid command or when there are multiple possibilities for a command. You can use the command **hint** and the chess engine will give you a hint for the next move.

You can also use the **back** which takes back your last move(s), this will help you cheat or revise the game depending on how you see it.

### Closing thoughts

If you find the chessboard to be very tiny, you can scale it up and play around with different fonts. Both Stockfish and chs are open source and you can easily get your hands dirty and mess around with the code for your own projects (if you want).

If you want to try out the good old GNU Chess, you can install it using the command below.

```
sudo apt install gnuchess
```

Let me know how your game went in the comment section :)

--------------------------------------------------------------------------------

via: https://itsfoss.com/play-chess-linux-terminal/

作者：[Chinmay][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/chinmay/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/funny-linux-commands/
[2]: https://itsfoss.com/best-command-line-games-linux/
[3]: https://stockfishchess.org/
[4]: https://www.gnu.org/software/chess/
[5]: http://www.computerchess.org.uk/ccrl/404/index.html
[6]: https://i1.wp.com/itsfoss.com/wp-content/uploads/2020/09/play-chess-linux-terminal.png?resize=800%2C450&ssl=1
[7]: https://itsfoss.com/install-pip-ubuntu/
[8]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/07/Screenshot-from-2020-07-21-18-07-58.png?resize=800%2C108&ssl=1
[9]: https://itsfoss.com/nano-editor-guide/
[10]: https://i1.wp.com/itsfoss.com/wp-content/uploads/2020/07/Screenshot-from-2020-07-21-18-13-48.png?resize=759%2C408&ssl=1
[11]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/07/Screenshot-from-2020-07-21-18-15-41.png?resize=800%2C433&ssl=1
[12]: https://i1.wp.com/itsfoss.com/wp-content/uploads/2020/07/Screenshot-from-2020-07-22-15-27-45.png?resize=800%2C494&ssl=1
[13]: https://www.ichess.net/blog/chess-notation/
[14]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/07/a4.png?resize=800%2C495&ssl=1
[15]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/07/Nh3.png?resize=800%2C494&ssl=1
[16]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/07/Nxc4.png?resize=800%2C499&ssl=1
