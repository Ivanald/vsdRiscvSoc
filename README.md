# vsdRiscvSoc
All the projects/assignments done as part of India RISC-V Chip Tapeout workshop conducted by VSD. 
#Index

# Task1 - RISC-V Toolchain Setup Tasks & Uniqueness Test

## End Goal: 
To Install RICV-V Toolchain, install spike and pk, and do a uniqueness test.

## File Used for Uniqueness Test: 
unique_test.c: [task1/files/unique_test.c](task1/files/unique_test.c)

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
Task1 Output: ![images/task1/1UniquenessTest.png](task1/images/1UniquenessTest.png)



# Installation of RISC-V toolchain, spike and pk. 

Follow the below steps for installing RICV-V Toolchain, spike and pk for **Alma Linux Operating System**.

## Step1: Install riscv toolchain
### Install xpm packages: To ensure all the required libraries are installed. 
 xpm packages, abbreviated as xPacks, are versatile, language-neutral software packages coming from //link// https://xpack-dev-tools.github.io. xPack GNU RISC-V Embedded GCC packages help in easy installation without worrying about dependent libraries. These packages will automatically update the libraries as well when the system updates happen. More details on this can be found in the above link. 
 
#### Prerequisites for xpm 
The only prerequisite for xPack is a recent version of Node.js (>=18.0.0), as some dependencies require new features. So first checking the version available. 

```bash
node --version
```

 ![task1/images/2NodeJsVersion.png](task1/images/2NodeJsVersion.png)


To get the latest version run the sript given in the same above website (also attached in the folder [task1/files/install-nvm-node-npm-xpm.sh](task1/files/install-nvm-node-npm-xpm.sh). This will also install latest npm and xpm packages. 
```bash
mkdir -pv "${HOME}/Downloads/"
curl --output "${HOME}/Downloads/install-nvm-node-npm-xpm.sh" https://raw.githubusercontent.com/xpack/assets/master/scripts/install-nvm-node-npm-xpm.sh
cat "${HOME}/Downloads/install-nvm-node-npm-xpm.sh"
```

 ![task1/images/3NodeNvmXpmScriptDownload.png](task1/images/3NodeNvmXpmScriptDownload.png)
 After downlaoding run the sript. 
```bash
bash "${HOME}/Downloads/install-nvm-node-npm-xpm.sh"
exit
```
The last line of the script will give the version: 
 ![task1/images/4NodeInstallLastline.png](task1/images/4NodeInstallLastline.png)

You can exit this terminal and check in a new terminal whether xpm has been installed. 

```bash
which xpm
xpm --version
```
 ![task1/images/5XpmInstallCheck.png](task1/images/5XpmInstallCheck.png)


### Install riscv-none-elf-gcc (riscv toolchain) 

This is a prebuilt toolchain taken from https://www.npmjs.com/package/@xpack-dev-tools/riscv-none-elf-gcc. To download it, initialize xpm and download the riscv-none-elf-gcc
 
We need to ensure that .json file is available in your project folder for xpm to work. So make one folder for your project and initialize xpm there

```bash
cd /home/jahnavi
mkdir riscv_toolchain
cd riscv_toolchain
xpm init
```

![task1/images/6MakingADirectoryAndjsonfile.png](task1/images/6MakingADirectoryAndjsonfile.png)

Install the latest package:

```bash
xpm install @xpack-dev-tools/riscv-none-elf-gcc@latest --verbose
```

 ![task1/images/7InstallToolchainPackage.png](task1/images/7InstallToolchainPackage.png)


List all the files downloaded
```bash
ls -l xpacks/.bin
```
 ![task1/images/8FilesDownloadedFromRiscvToolchain.png](task1/images/8FilesDownloadedFromRiscvToolchain.png)


**Riscv Version Details**
```bash
~/.local/xPacks/riscv-none-elf-gcc/xpack-riscv-none-elf-gcc-14.2.0-3/bin/riscv-none-elf-gcc --version
```
![task1/images/9CheckingRiscvToolchainVersion.png](task1/images/9CheckingRiscvToolchainVersion.png)



## Step2: Install Device Tree Compiler (DTC)

Adding the device tree complier dependency also. 
```bash

```
## Step3: Install spike and add to path
Spike is an open-source RISC-V Instruction Set Simulator (ISS) which is used to emulate the RISC-V programs without the requirement of physical hardware. 

## Step4: Install pk and add to path

##Step5: Sanity checks

# Uniqueness Test

A program to give the 64‐bit FNV‐1a hash of username and hostname. 

## Program: 


## Compilation command:

## Running on spike with pk
Here, we were getting an error which was resolved when you are giving the pk path

Command:

Output:

# Errors encountered during the installation 

## Building from source rather than pk. 

## Path error for pk

## Compilation error. 



