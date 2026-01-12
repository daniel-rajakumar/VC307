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
### Screenshot 1
![Demo 1 output](screenshots/one.png)

---

Demo 1 assembles the sum program, prints the symbol table and translation, then emulates input 5 and 3 to produce a sum of 8.

### Screenshot 2
![Demo 2 output](screenshots/two.png)

---

Demo 2 assembles the factorial program and runs the emulator with input 9, producing 9! = 362880.

### Screenshot 3
![Demo 3 output](screenshots/three.png)

---

Demo 3 shows the branch/diff program and emulates input 3 and 7, outputting the absolute difference of 4.

### Screenshot 4
![Demo 4 output](screenshots/four.png)

---

Demo 4 assembles the Fibonacci program and emulates input 9, outputting the 9th Fibonacci number as 34.

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
