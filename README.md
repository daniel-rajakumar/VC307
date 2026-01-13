# VC370 Assembler and Emulator

![C++17](https://img.shields.io/badge/C%2B%2B-17-00599C?style=flat-square)
![Build: Make](https://img.shields.io/badge/build-make-4EAA25?style=flat-square)
![Type: Assembler + Emulator](https://img.shields.io/badge/type-assembler%20%2B%20emulator-0F766E?style=flat-square)
![IDE: Visual Studio](https://img.shields.io/badge/IDE-Visual%20Studio-5C2D91?style=flat-square)

A two-pass assembler and emulator for the VC370/Quack3200 instruction set. It parses `.asm` source, builds a symbol table, translates to machine code, and runs the program in a simple emulator.

## At a glance
| Item | Details |
| --- | --- |
| Source | `VC370Assem/VC370Assem` |
| Build | `make` |
| Run | `./assem <file.asm>` |
| Demos | `make demo-sum`, `make demo-factorial`, `make demo-branch`, `make demo-fib` |
| Memory | 10,000 locations; execution starts at 100 |

## Highlights
- Two-pass assembly with label resolution and symbol table output.
- Instruction set support for arithmetic, memory, I/O, and branching.
- Directives: ORG, DC, DS, END.
- Error checks for invalid opcodes/labels, missing END, undefined symbols, and memory bounds.
- Emulator with optional friendly I/O for demo programs.

## Quick Start
```sh
cd VC370Assem/VC370Assem
make
./assem program.asm
```

## Demo programs
```sh
make demo
make demo-sum
make demo-factorial
make demo-branch
make demo-fib
```

## Friendly I/O
Use `ASSEM_FRIENDLY_IO` to enable human-friendly prompts and outputs:

```sh
ASSEM_FRIENDLY_IO=sum ./assem demo_sum.asm
ASSEM_FRIENDLY_IO=factorial ./assem demo_factorial.asm
ASSEM_FRIENDLY_IO=diff ./assem demo_branch.asm
ASSEM_FRIENDLY_IO=fibonacci ./assem demo_fib.asm
```

## Instruction set
| Category | Opcodes |
| --- | --- |
| Arithmetic | `ADD`, `SUB`, `MULT`, `DIV` |
| Memory | `LOAD`, `STORE` |
| I/O | `READ`, `WRITE` |
| Control flow | `B`, `BM`, `BZ`, `BP`, `HALT` |

### Assembler directives
- `ORG` - set program origin.
- `DC` - define constant.
- `DS` - reserve storage.
- `END` - mark end of program.

## Assembly format
- Comments start with `;`.
- Lines are `LABEL OPCODE OPERAND`.
- Labels must start with a letter, be alphanumeric, <= 10 chars, and not use reserved keywords.

Example:
```asm
        ORG 100
START   READ N
        LOAD N
        ADD  ONE
        STORE N
        WRITE N
        HALT
N       DS   1
ONE     DC   1
        END
```

## Screenshots
| Screenshot 1 |
| --- |
| ![Demo 1 output](screenshots/one.png) |
| _Demo 1 assembles the sum program, prints the symbol table and translation, then emulates input 5 and 3 to produce a sum of 8._ |

| Screenshot 2 |
| --- |
| ![Demo 2 output](screenshots/two.png) |
| _Demo 2 assembles the factorial program and runs the emulator with input 9, producing 9! = 362880._ |

| Screenshot 3 |
| --- |
| ![Demo 3 output](screenshots/three.png) |
| _Demo 3 shows the branch/diff program and emulates input 3 and 7, outputting the absolute difference of 4._ |

| Screenshot 4 |
| --- |
| ![Demo 4 output](screenshots/four.png) |
| _Demo 4 assembles the Fibonacci program and emulates input 9, outputting the 9th Fibonacci number as 34._ |

## Project layout
| Path | Description |
| --- | --- |
| `VC370Assem/VC370Assem` | C++ source, Makefile, and demo `.asm` files. |
| `VC370Assem/VC370Assem/assem` | Prebuilt binary (if present). |
| `VC370Assem/VC370Assem/VC370Assem.sln` | Visual Studio solution. |

## Tech
- C++17
- Makefile (clang++ by default)
- Visual Studio solution
