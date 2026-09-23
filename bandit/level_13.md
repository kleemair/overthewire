# Bandit Level 13



<img width="1538" height="500" alt="download (13)" src="https://github.com/user-attachments/assets/6e45ef3b-dca2-4794-b638-e4fee58fce0c" />






## Concept learned
- Working with hexdumps  
- Identifying file types  <br><br>

## Commands used
- file
- ls
- cd
- mv
- xxd[^1]
- gzip[^2]
- tar[^3]
- bzip2[^4]
- mktemp[^5]<br><br>

### Walkthrough
1.  Connect to the overthewire host with the username bandit12 and the password you found in the previous level.
2.  Inside the home directory, you will find a file named **data.txt**. When you open it with `cat`, the content clearly looks like a **hexdump**.
3.  Before we restore the orginal file you have to make a temporary directory using ```mktemp -d``` and ```cd``` into the new directory
4.  Reverse the hexdump using:
    ```
    xxd -r data.txt data.bin
    ```
5.  Identify the file type of the restored file:
    ```
    file data.bin
    ```
6.  This level contains multiple layers of encoded files.  
    Each time you extract a file, you receive *another compressed file*.  
    So you must repeatedly:
    - check the file type  
    - extract it  
    - inspect the new file
7.  Use the following commands depending on what ```file``` tells you:
      <br><br>**If it is a POSIX tar archive:**<br>
      `tar -xf filename`
      <br><br>**If it is gzip compressed:**<br>
      `
      mv filename file.gz
      `<br>
      `
      gzip -d file.gz
      `
      <br><br>**If it is bzip2 compressed:**<br>
      `
      mv filename file.bz2
     `<br>
      `
      bzip2 -d file.bz2
      `
      <br><br>After each extraction, run:<br>
      `
      file newfile
      `<br><br>
9. Continue decoding layer by layer until you eventually get a readable ASCII text file.
10.  The ASCII text file will contain the password. Copy it into your text file and disconnect from the current level.

<br><br><br>

[^1]:[xxd man page](https://linux.die.net/man/1/xxd)
[^2]:[gzip man page](https://linux.die.net/man/1/gzip)
[^3]:[tar man page](https://linux.die.net/man/1/tar)
[^4]:[bzip2 man page](https://linux.die.net/man/1/bzip2)
[^5]:[mktemp man page](https://linux.die.net/man/1/mktemp)
