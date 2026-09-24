# Bandit Level 18


<img width="1005" height="500" alt="loading bar" src="https://github.com/user-attachments/assets/28398882-6a60-46a9-9487-f92a14c88af3" />









## Concept learned
- Comparing files with diff<br><br>

## Commands used
- diff[^1] <br><br>

### Walkthrough
1. Connect to Level 18 using the private key you got from the previous level:
    ```
    ssh -i sshkey.private bandit18@bandit.labs.overthewire.org -p 2220
    ```
2.  In this level we need to find a line that is different in two text files. This can be achieved with the command ```diff```:
    ```
    diff -a passwords.new passwords.old
    ```
3. The output may be confusing at first but it's simple. The text after ```<``` is the text which needs to be changed to the text following ```>``` so the two file are exactly the same. So if you have two files with fruits and the newer version changed one line to "Banana" instead of "Watermelon" the output would look something like this:
    ```
    < Banana
    ---
    > Watermelon
    ```
4. Save the password to your notes and disconnect from the current level.
<br><br><br>

[^1]:[explanation of diff](https://phoenixnap.com/kb/linux-diff)
