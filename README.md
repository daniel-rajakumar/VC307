# VC407 - VC370 Assembler and Emulator

A two-pass assembler and emulator for the VC370/Quack3200 instruction set.
It parses `.asm` source, builds a symbol table, translates to machine code,
and runs the program in a simple emulator.

## Features
- Two-pass assembly with label resolution and symbol table output.
- Machine opcodes: ADD, SUB, MULT, DIV, LOAD, STORE, READ, WRITE, B, BM, BZ, BP, HALT.
- Assembler directives: ORG, DC, DS, END.
- Error reporting for invalid opcodes, bad labels, missing END, undefined symbols, and memory limits.
- Built-in emulator with optional friendly I/O for demo programs.
- Sample programs: sum, factorial, branch/diff, fibonacci, and a general demo.

## Project layout
- `VC370Assem/VC370Assem` - C++ source, Makefile, and demo `.asm` files.
- `VC370Assem/VC370Assem/assem` - prebuilt binary (if present).
- `VC370Assem/VC370Assem/VC370Assem.sln` - Visual Studio solution.

## Build
From `VC370Assem/VC370Assem`:

```sh
make
```

## Run
```sh
./assem program.asm
```

Run the provided demos:
```sh
make demo
make demo-sum
make demo-factorial
make demo-branch
make demo-fib
```

## Screenshots
![Screenshot 1](screenshots/one.png)
Caption: Demo output (1).
![Screenshot 2](screenshots/two.png)
Caption: Demo output (2).
![Screenshot 3](screenshots/three.png)
Caption: Demo output (3).
![Screenshot 4](screenshots/four.png)
Caption: Demo output (4).

## Friendly I/O mode
The emulator can print human-friendly prompts and outputs for demos using `ASSEM_FRIENDLY_IO`:

```sh
ASSEM_FRIENDLY_IO=sum ./assem demo_sum.asm
ASSEM_FRIENDLY_IO=factorial ./assem demo_factorial.asm
ASSEM_FRIENDLY_IO=diff ./assem demo_branch.asm
ASSEM_FRIENDLY_IO=fibonacci ./assem demo_fib.asm
```

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

## Notes
- Memory size is 10,000 locations.
- Execution starts at location 100 in the emulator.

## Tech
- C++17
- Makefile (clang++ by default) and Visual Studio solution
