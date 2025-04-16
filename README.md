# TP Archi 2

## Steps to solve the TP

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

