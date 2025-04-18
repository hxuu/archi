# TP Archi 2

## Steps to solve the TP

### Example 01

1. create a new file and save it using ctrl+s

![first-thing](screenshots/2025-04-16-11-15-57.png)

2. copy the code from example 1 in the pdf

```asm
.data
vars:   .word 5
     .text
li $t0, 10
li $t1, 15
la $t2, vars
sw $t1, 0($t0)
lw $t2, 4($t0)
addi $t2, $t0,4
subi $t2, $t0,4
syscall
```

3. Donner le code  binaire de chaque instruction et le groupe de format. (press F3)

![binary-encoding](screenshots/2025-04-16-11-23-27.png)

4. Pour vérifier (the way of the bits) ouvrir la fenêtre MIPS X-RAY avec Tools>mips X-RAY.

![mips-xray](screenshots/2025-04-16-11-26-42.png)

5. Donner l’état des signaux de l’unité de contrôle et du alu-contrôle pour les instructions addi et subi

addi:
![addi](screenshots/2025-04-16-12-00-25.png)
sub:
![sub](screenshots/2025-04-16-12-20-14.png)

### Example 02

#### `Big idea`

Writing a MIPS assembly program using MARS, a simulator that lets you run MIPS assembly instructions.

This example is about:

1. Understanding a loop.
2. Conditionally breaking out of it.
3. Watching the flow of control (ie, PC - program counter)

---

1. create a new file and save it using ctrl+s

![second-source](screenshots/2025-04-18-16-10-41.png)

2. copy the code from example 2 in the pdf

```asm
.data
vars: .word 0       # Declare a word (int) in memory initialized to 0

.text
la $t0, vars        # $t0 ← address of 'vars'
lw $t1, 0($t0)      # $t1 ← value at address in $t0 (initially 0)
li $t2, 3           # $t2 ← 3 (this is our loop exit condition)

saut: beq $t1, $t2, exit   # If $t1 == 3, jump to exit
move $a0, $t1              # Put $t1 into $a0 (to prepare for print)
li $v0, 1                  # Load system call code for print_int
syscall                   # Print the value in $a0
addi $t1, $t1, 1           # $t1 += 1 (increment counter)
j saut                     # Jump back to loop

# If $t1 == 3, it exits:
exit: li $v0, 10
syscall
```

> [!TIP]
> vars has the value 0, its address is different from zero.

What we're doing here is:

- Initializing a counter (vars = 0)

- Looping and printing until the counter reaches 3

- Incrementing on each iteration

- Using a conditional jump to exit when done

- Learning how MIPS handles control flow

2. Déterminer  la valeur du registre pc pour chaque instruction

![](videos/example2-program-counter-2025-04-18_17.24.25.mp4)
