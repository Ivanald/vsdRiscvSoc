# Task 2 - Prove Your Local RISC-V Setup (Run, Disassemble,Decode)

## End Goal: 
Running some RISC-V C programs on my local machine (complied with local toolchain, executed with spike pk) and then geneate the assembly code, decode the RISC-V instructions for each program. 
Print the machnie username, hostname, machine iD and timestamps to ensure that the output is unique to my machine. 

## Spike Version used
To check the spike version, go to the command prompt from any folder in your PC and type the following command: 
```bash
spike -h 
```

The first line will print your version details. 
![task2/1SpikeVersionDetails.png](task2/1SpikeVersionDetails.png)

## Uniqueness mechanism 
To ensure that each build is machine and user specific, we can print the identity details in the start of every program. For this, we will save these details in some variables using the following command: 
This needs to be executed only once before executing all the programs. Then while compilation of the programs, pass these values. 

```bash
export U=$(id -un)
export H=$(hostname -s)
export M=$(cat /etc/machine-id | head -c 16)
export T=$(date -u +%Y-%m-%dT%H:%M:%SZ)
export E=$(date +%s)
```
![task2/1UserDetails_OnetimeExecution.png](task2/1UserDetails_OnetimeExecution.png)

Then create the following file in the folder where you are keeping all the programs for execution and save it with '.h' extension (which means we made a header file). 
This program will print all the details from above. We will include this program in every other programs executed in this task. 

![task2/unique.h](task2/unique.h)

It should be noted that this header files includes all the other commonly used and required (in our program) headers, so we don't need to call them separately in each program. Just including this file is enough. 
It includes the following common headers: 
```bash
#include <stdio.h>
#include <stdint.h>
#include <time.h>
```
## Programs implemented

### Factorial 

Program code (.c file): ![task2/factorial.c](task2/factorial.c)

#### Compilation command

```bash
riscv-none-elf-gcc -O0 -g -march=rv64ima -mabi=lp64 -DUSERNAME="\"$U\"" -DHOSTNAME="\"$H\"" -DMACHINE_ID="\"$M\"" -DBUILD_UTC="\"$T\"" -DBUILD_EPOCH=$E \factorial.c -o factorial
```
After entering this command, an executable file will be formed in your folder.

#### Execution command

```bash
spike /home/jahnavi/riscv_toolchain/pk/riscv-none-elf/bin/pk ./factorial
```

**Output**

![task2/factorial_z_images/factorial_output.png](task2/factorial_z_images/factorial_output.png)

#### Creating assembly file (.s)

```bash
riscv-none-elf-gcc -O0 -S factorial.c -o factorial.s
```

This will create the following file: ![task2/factorial.s](task2/factorial.s)

#### Creating the disassembly file of main only (.txt)

```bash
riscv-none-elf-objdump -d ./factorial | sed -n '/<main>:/,/^$/p' | tee factorial_main_objdump.txt
```

This will create the following file: ![task2/factorial_main_objdump.txt](task2/factorial_main_objdump.txt)


**Output**

![task2/factorial_z_images/factorial_main_asm.png](task2/factorial_z_images/factorial_main_asm.png)


#### After executing all the above commands, the following files should be available in your folder:

![task2/factorial_z_images/factorial_FinalFilesAfterCompleteExecution.png](task2/factorial_z_imagesfactorial_FinalFilesAfterCompleteExecution.png)


### Max Array
Program code (.c file): ![task2/max_array.c](task2/max_array.c)

#### Compilation command

```bash
riscv-none-elf-gcc -O0 -g -march=rv64ima -mabi=lp64 -DUSERNAME="\"$U\"" -DHOSTNAME="\"$H\"" -DMACHINE_ID="\"$M\"" -DBUILD_UTC="\"$T\"" -DBUILD_EPOCH=$E max_array.c -o max_array
```
After entering this command, an executable file will be formed in your folder.

#### Execution command

```bash
spike /home/jahnavi/riscv_toolchain/pk/riscv-none-elf/bin/pk ./max_array
```

**Output**

![task2/max_array_z_images/max_array_output.png](task2/max_array_z_images/max_array_output.png)

#### Creating assembly file (.s)

```bash
riscv-none-elf-gcc -O0 -S max_array.c -o max_array.s
```
This will create the following file: ![task2/max_array.s](task2/max_array.s)

#### Creating the disassembly file of main only (.txt)

```bash
riscv-none-elf-objdump -d ./max_array | sed -n '/<main>:/,/^$/p' | tee max_array_main_objdump.txt
```
This will create the following file: ![task2/max_array_main_objdump.txt](task2/max_array_main_objdump.txt)


**Output**

![task2/max_array_z_images/max_array_main_asm.png](task2/max_array_z_images/max_array_main_asm.png)


#### After executing all the above commands, the following files should be available in your folder:

![task2/max_array_z_images/max_array_FinalFilesAfterCompleteExecution.png](task2/max_array_z_images/max_array_FinalFilesAfterCompleteExecution.png)


### Bitops

Program code (.c file): ![task2/bitops.c](task2/bitops.c)

#### Compilation command

```bash
riscv-none-elf-gcc -O0 -g -march=rv64ima -mabi=lp64 -DUSERNAME="\"$U\"" -DHOSTNAME="\"$H\"" -DMACHINE_ID="\"$M\"" -DBUILD_UTC="\"$T\"" -DBUILD_EPOCH=$E bitops.c -o bitops
```

After entering this command, an executable file will be formed in your folder.

#### Execution command

```bash
spike /home/jahnavi/riscv_toolchain/pk/riscv-none-elf/bin/pk ./bitops
```
**Output**

![task2/bitops_z_images/bitops_output.png](task2/bitops_z_images/bitops_output.png)

#### Creating assembly file (.s)

```bash
riscv-none-elf-gcc -O0 -S bitops.c -o bitops.s
```
This will create the following file: ![task2/max_array.s](task2/max_array.s)

#### Creating the disassembly file of main only (.txt)

```bash
riscv-none-elf-objdump -d ./bitops | sed -n '/<main>:/,/^$/p' | tee bitops_main_objdump.txt
```
This will create the following file: ![task2/bitops_main_objdump.txt](task2/bitops_main_objdump.txt)

**Output**

![task2/bitops_z_images/bitops_main_asm.png](task2/bitops_z_images/bitops_main_asm.png)


#### After executing all the above commands, the following files should be available in your folder:

![task2/bitops_z_images/bitops_FinalFilesAfterCompleteExecution.png](task2/bitops_z_images/bitops_FinalFilesAfterCompleteExecution.png)

### Bubble sort

Program code (.c file): ![task2/bubble_sort.c](task2/bubble_sort.c)

#### Compilation command

```bash
riscv-none-elf-gcc -O0 -g -march=rv64ima -mabi=lp64 -DUSERNAME="\"$U\"" -DHOSTNAME="\"$H\"" -DMACHINE_ID="\"$M\"" -DBUILD_UTC="\"$T\"" -DBUILD_EPOCH=$E bubble_sort.c -o bubble_sort
```
After entering this command, an executable file will be formed in your folder.

#### Execution command

```bash
spike /home/jahnavi/riscv_toolchain/pk/riscv-none-elf/bin/pk ./bubble_sort
```
**Output**

![task2/bubble_sort_z_images/bubble_sort_output.png](task2/bubble_sort_z_images/bubble_sort_output.png)

#### Creating assembly file (.s)

```bash
riscv-none-elf-gcc -O0 -S bubble_sort.c -o bubble_sort.s
```
This will create the following file: ![task2/bubble_sort.s](task2/bubble_sort.s)

#### Creating the disassembly file of main only (.txt)

```bash
riscv-none-elf-objdump -d ./bubble_sort | sed -n '/<main>:/,/^$/p' | tee bubble_sort_main_objdump.txt
```
This will create the following file: ![task2/bubble_sort_main_objdump.txt](task2/bubble_sort_main_objdump.txt)


**Output**

![task2/bubble_sort_z_images/bubble_sort_main_asm.png](task2/bubble_sort_z_images/bubble_sort_main_asm.png)


#### After executing all the above commands, the following files should be available in your folder:

![task2/bubble_sort_z_images/bubble_sort_FinalFilesAfterCompleteExecution.png](task2/bubble_sort_z_images/bubble_sort_FinalFilesAfterCompleteExecution.png)

## After executing all the above programs your final folder will look like this

![task2/zFiles_in_final_folder.png](task2/zFiles_in_final_folder.png)


