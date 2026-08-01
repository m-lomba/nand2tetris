# Nand2Tetris

Implementation of the projects from the [Nand2Tetris](https://www.nand2tetris.org/) course (*The Elements of Computing Systems*): building a computer from the ground up, starting from a single NAND gate and ending with an assembler and a virtual machine translator capable of running a full program (Pong) on it.

The hardware projects (1-4) are built in HDL and tested with the official Nand2Tetris hardware simulator. The software tools (assembler and VM translator, projects 5-7) are implemented from scratch in **C** rather than the course's suggested language.

## Contents

| Folder | Project | Description |
|---|---|---|
| `project1` | Boolean logic | Elementary gates (`And`, `Or`, `Xor`, `Mux`, `DMux`) and their 16-bit / multi-way variants, built out of `Nand` |
| `project2` | Boolean arithmetic | Half/full adder, 16-bit adder and incrementer, and the ALU |
| `project3` | Sequential logic | `Bit`, `Register`, RAM chips (8 to 16K words) and the Program Counter, built on the `DFF` |
| `project4` | Machine language & architecture | Hand-written Hack assembly programs (`Add`, `Max`, `Rect`) plus the `CPU`, `Memory` and `Computer` chips that execute them |
| `project5_2` | Assembler (C) | Translates `.asm` source into `.hack` binary machine code; split into parser and symbol-table modules |
| `project6` | VM translator I (C) | Translates VM arithmetic and `push`/`pop` commands into Hack assembly |
| `project7` | VM translator II (C) | Adds branching and function-call support (`call`/`function`/`return`); used to translate a full Pong game written in VM code into runnable Hack assembly |

Each HDL project includes the matching `.tst` test script and `.cmp`/`.out` files produced by the hardware simulator, confirming the chip passes the official test suite. The `consegna*.zip` files are the original assignment submissions, kept for reference.

## Running the HDL projects

Open the `.hdl` files with the [Nand2Tetris Hardware Simulator](https://www.nand2tetris.org/software) and run the corresponding `.tst` script to verify each chip against the official test suite.

## Building and running the C tools

```bash
# Assembler
cd project5_2 && make
./assembler path/to/file.asm        # produces file.hack

# VM translator (arithmetic + push/pop)
cd project6/VMtranslator && make
./VMtranslator path/to/file.vm       # produces file.asm

# VM translator (branching + functions), e.g. the Pong game
cd project7/VMtranslator && make
./VMtranslator path/to/folder        # translates all .vm files into a single .asm
```

The generated `.asm` file can then be loaded into the [CPU Emulator](https://www.nand2tetris.org/software) to run on the simulated Hack computer.
