# Brainf**k in nano!

How to use: `nano --rcfile brainfk.nanorc instructions.bf`

nano 7.2 (or patched 8.0, such as: https://savannah.gnu.org/bugs/index.php?65741#comment11) is needed.
A lookup table is also needed, a -256 to 255 lookup table is provided, to make a bigger one use `python3 make_lookup_table.py 512 > lookup_table` (replace 512 with the size you want)
The cells are stored in a file called `cells`, this should be as many cells as you need (I used 256), just put "0" on every line.
Any input you need, put in a file called `input`, all output will be in a file called `output`

Once you have the instructions open:
- Hit ^O to setup the other buffers
- Press ^P until you reach the last character (sadly it does not automatically stop, and it will loop back to the start if you let it, and this is no good)

Due to some limitations:
- The first char is skipped, so just put a space there (^O does this automatically)
- I could not find a way to loop (besides unrolling, which wouldn't work here), so you will have to hold ^P until the last char
- I could not find a way to automatically stop at the end, nano does not seem to have a way to block search from wrapping around to the start of the file
- The lookup tables are unideal, I would love to do without them if possible
- You cannot print '\n' or '\r' due to they way the lookup table works

When you are done, exit out of all files without saving except for `output` (the last one), it should have the output of the program!

Very much inspired by this bug report: https://savannah.gnu.org/bugs/index.php?65741

Relevant xkcd: https://xkcd.com/2556/

More info coming soon!
