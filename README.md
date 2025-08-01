# vsdRiscvSoc
All the projects/assignments done as part of India RISC-V Chip Tapeout workshop conducted by VSD. 
#Index

# Task1 - RISC-V Toolchain Setup Tasks & Uniqueness Test

## End Goal: 
To Install RICV-V Toolchain, install spike and pk, and do a uniqueness test.

## File Used for Uniqueness Test: 
unique_test.c: [task1/unique_test.c](task1/unique_test.c)

## Command used for compliation: 
```bash
riscv-none-elf-gcc -O2 -Wall -march=rv64ima -mabi=lp64 -DUSERNAME=\"Jahnavi\" -DHOSTNAME=\"VLSILab\" unique_test.c -o unique_test
```

## Output Received: 

```bash
RISC-V Uniqueness Check 
User: Jahnavi
Host: VLSILab
UniqueID: 0x69b7e1cc91ae1a87
GCC_VLEN: 6
```
Task1 Output: ![images/task1/UniquenessTest.png](images/task1/UniquenessTest.png)



# Installation Steps:

Follow the below steps for installing RICV-V Toolchain, spike and pk for Alma Linux Operating System.

