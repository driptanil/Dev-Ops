# Linux & Terminal Commands

A shell is a command-line interface which allows to perform certain tasks using command

### Basic Commands

- `cd` → change directory
    - `cd ..` → goes back a single directory
- `mkdir` → make new folder
    - `mkdir -p` → makes directories and sub-directories too.
        
        ![mkdir-p.png](mkdir-p.png)
        
- `touch` → creates a new file
    
    ![touch.png](touch.png)
    
- `ls`/`dir` → lists all the files in the current directory
    - `ls -a` → displays all the hidden files
    - `ls -l` → shows more information like size, date about the files in working directory.
    - `ls -R` → show files, directories and sub-directories as well.
- `xdg-open` / `open` → opens the graphical interface of the present working directory.
- `pwd` → Print Working Directory
- `cp` → creates a copy of a file or a folder
    
    ![cp.png](cp.png)
    
    - `cp -R` → copies directories and also the sub-directories
        
        ![cp-R.png](cp-R.png)
        
- `mv` → moves files
    
    ![mv.png](mv.png)
    
    If names of two files are given, then the file gets renamed.
    
    ![mv2.png](mv2.png)
    
- `rm` → removes only files permanently.
    - `rm -R` → removes directories permanently.
    - `rm -rf` → force remove of files or directories.
      
- `sudo` → Super User Do gives system administrator privileges.
    
    ![sudo.png](sudo.png)
    
- `history` → displays history of commands
    
    ![history.png](history.png)
    
    - `history | grep "ls"` → display the history of ls commands
    - `!1124` → runs `alias gpom="git push origin main"`
    - `!grep` → runs the last `grep` command
      
- `zip` → compresses files into a .zip file
    
    ![zip.png](zip.png)
    
    - `unzip` → decompresses the .zip file
        
        ![unzip.png](unzip.png)
        
- `man` → displays the command manual

### File Commands

- `echo` → displays
    
    ![echo.png](echo.png)
    
    ![echo2.png](echo2.png)
    
- `cat` stands for concatenate, it is used to display the contents of a file
    - `cat >` creates a file.
        
        ![cat>.png](cat>.png)
        
        ![cat>2.png](cat>2.png)
        

- `vi names.txt` allows editing the file in the console.
    
    ![vi.png](vi.png)
    
    ![vi2.png](vi2.png)
    
    - press `i` to enter insert mode and `Esc` to enter command mode.
        - `I` - Insert text at the beginning of the current line
        - `A` – Write at the end of the line (goes into insert mode)
        - `b` → Go to the beginning of the word
        - `e` → Go to the ending of the word
        - `u` – Undo last change
        - `U` – Undo all changes to the entire line
        - `o` – Open a new line (goes into insert mode)
        - `dd` – Delete line
        - `3dd` – Delete 3 lines.
        - `D` – Delete contents of the line after the cursor
        - `C` – Delete the contents of a line after the cursor and insert new text.
        - `dw` – Delete word
        - `4dw` – Delete 4 words
        - `cw` – Change word
        - `x` – Delete the character at the cursor
        - `~` – Change case of individual character
    - `:wq` → writes and quit the file in command mode
    - `:q!` → quit without saving the changes in command mode
    - `:w` → save and continue editing
    - `yy` → Yank [copy a line of text]
    
    [An introduction to the vi editor](https://www.redhat.com/sysadmin/introduction-vi-editor)
    
- `head` → displays the first 10 lines of a file
    - `head -n 1` → displays the first line of a file
- `tail` → displays the lasts 10 lines of a file
    - `tail -n 1` → displays the last line of a file
- `diff` → compares files and displays lines which does not match
    
    ![diff.png](diff.png)
    
- `tr` → translate
    
    ![tr.png](tr.png)
    
- `grep` → searches Strings in files.
    
    ![grep.png](grep.png)
    
    ![Screenshot_20220125_215119.png](Screenshot_20220125_215119.png)
    
    - `grep -w` → searches Strings of a complete word in files.
        
        ![grep-w.png](grep-w.png)
        
    - `grep -i` → [ignore cases] searches non-case sensitive Strings in files.
        
        ![grep-i.png](grep-i.png)
        
    - `grep -n` → searches Strings in files and also displays the line no.
        
        ![grep-n.png](grep-n.png)
        
    - `grep -win` → search non-case sensitive Strings in words in files and also displays the line no.
        
        ![grep-win.png](grep-win.png)
        
    - `grep -B 3` → also displays 3 lines before the searched Strings.
    - `grep -r` → searches Strings in files recursively.
        
        ![grep-B.png](grep-B.png)
        
    - `grep -l` → displays list of filenames only.
        
        ![grep-l.png](grep-l.png)
        
    - `grep -c` → display the no of times the search string is present in a file
        
        ![grep-c.png](grep-c.png)
        
    - `grep -p` → is used to search regular expressions
      
- `sort` → displays lines of file sorted alphabetically.
    
    ![sort.png](sort.png)
    
    - `sort -r` → displays lines of files sorted in reverse
        
        ![sort-r.png](sort-r.png)
        
    - `sort -b` → ignores blacks while sorting
    - `sort -f` → ignores cases while sorting
    - `sort -n` → sorts numerical value
- `lsof` → lists all the opened files
    - `lsof -u driptanil` → displays all the opened files by ‘driptanil’ user
- `cut` → remove sections from each line of files
    
    ![cut.png](cut.png)
    
    - `cut -b` → removes only bytes
    - `cut -c` → removes only characters
- `locate "*.txt"` → will display location of all the .txt files.
    
    ![locate.png](locate.png)
    
- `find .` → displays all the files and folder in the working directory.
    - `find . -type d` → displays all the folders in the working directory.
        
        ![find.-type.png](find.-type.png)
        
    - `find . -type f` → displays all the files in the working directory.
        
        ![Screenshot_20220125_090119.png](Screenshot_20220125_090119.png)
        
    - `find -name`  → displays all files and folders with the name in working directory.
        
        ![Screenshot_20220125_090440.png](Screenshot_20220125_090440.png)
        
        ![Screenshot_20220125_090519.png](Screenshot_20220125_090519.png)
        
    - `find -iname` → displays all files and folders with the name [not case sensitive] in the working directory.
        
        ![Screenshot_20220125_090740.png](Screenshot_20220125_090740.png)
        
    - `find -mmin -15` → displays all the files and folders modified less than 15 mins ago.
    - `find -mmin +30` → displays all the files and folders modified more than 30 mins ago.
        
        ![Screenshot_20220125_091041.png](Screenshot_20220125_091041.png)
        
    - `find -mtime -10` → displays all the files and folders modified less than 10 days ago.
    - `find -maxdepth 1` → displays files and folders in working directory.
        
        ![Screenshot_20220125_092708.png](Screenshot_20220125_092708.png)
        
    - `find -mindepth 2` → displays files and folders in the folders in working directory.
        
        ![Screenshot_20220125_092927.png](Screenshot_20220125_092927.png)
        
    - `find -size +1k` → displays files and folders more than 1 Kb size.
    - `find -empty` → displays files and folders which are empty.
    - `find -perm 777` → displays files and folders with -rwxrwxrwx permissions.
        
        ![Screenshot_20220125_201607.png](Screenshot_20220125_201607.png)
        
    - `find . -type f -name "name*" -exec rm -rf {} +` → `exec` : execute the files and folder found by find command with another command, `{}` : place holder, `+` : add all the files.
        
        ![Screenshot_20220125_202122.png](Screenshot_20220125_202122.png)
        

### Other Commands

- `where`/`whereis` → displays the location of the environment variables.
- `.bashrc` file consists of the commands which are automatically executed when `bash` terminal is opened.
    - It also has `alias`, which is a short user-defined command that the shell translates to another command.
    The variables in capitals are environmental variables.
    - temporary alias
        
        ![Screenshot_20220126_135127.png](Screenshot_20220126_135127.png)
        
    - permanent alias [adding it in ~/.bashrc file
        
        ![Screenshot_20220126_135626.png](Screenshot_20220126_135626.png)
        
- `.profile` file consist of all the environmental variable paths.
- `$PATH` → consists all directories of the environmental variables
    
    ![Screenshot_20220124_221344.png](Screenshot_20220124_221344.png)
    
- `export` is used to set temporary environmental variable
    
    ![Screenshot_20220124_231857.png](Screenshot_20220124_231857.png)
    
- `chmod` → used to change the access permissions of file.
    
    ![https://assets.digitalocean.com/articles/linux_basics/mode.png](https://assets.digitalocean.com/articles/linux_basics/mode.png)
    
    - Types of file permissions:
        1. Read(r) [value = 4]
        2. Write(w) [value = 2]
        3. Execute(x) [value = 1]
    - Types of users:
        1. User[u]
        2. Guest[g]
        3. Other[o]
    - `chmod 777` → -rwxrwxrwx
        
        ![Screenshot_20220125_144544.png](Screenshot_20220125_144544.png)
        
    - `chmod 124` → --x-w-r--
        
        ![Screenshot_20220125_144805.png](Screenshot_20220125_144805.png)
        
    - `chmod 000` → ---------
- `chown` → change owner
    
    ![Screenshot_20220125_201002.png](Screenshot_20220125_201002.png)
    

### Terminal Shortcuts:

- `Ctrl + A` → move to the beginning of the line
- `Ctrl + E` → move to the end of the line
- `Ctrl + U` → remove the whole command
- `Ctrl + K` → removes everything to right of the cursor.
- `Ctrl + L` → clears the terminal like `clear` command
- `Tab` → used to auto-complete
- `;` → many commands together

### Network Commands

- `ping` → allows to request website server and displays all the statistics
    
    ![Screenshot_20220126_153007.png](Screenshot_20220126_153007.png)
    
- `wget` → download files from the internet.
    
    ![Screenshot_20220126_160144.png](Screenshot_20220126_160144.png)
    
- `nslookup` → displays the IP address of a particular domain
    
    ![Screenshot_20220126_185000.png](Screenshot_20220126_185000.png)
    
    ![Screenshot_20220126_185147.png](Screenshot_20220126_185147.png)
    
- `netstat` → displays the ports that are listening
- `curl ifconfig.me -s` → displays the IP address of the user
    
    ![Screenshot_20220126_185730.png](Screenshot_20220126_185730.png)
    

### User Commands

- `whoami` → displays the username
    
    ![Screenshot_20220125_193051.png](Screenshot_20220125_193051.png)
    
- `hostname` → displays the name of the Hostname
    
    ![Screenshot_20220126_161033.png](Screenshot_20220126_161033.png)
    
    - `hostname -i` → displays the IP Address
        
        ![Screenshot_20220126_161255.png](Screenshot_20220126_161255.png)
        
- `useradd` → adds new user
    
    ![Screenshot_20220126_164312.png](Screenshot_20220126_164312.png)
    
    - `passwd` → adds new password
        
        ![Screenshot_20220126_164512.png](Screenshot_20220126_164512.png)
        
    - `userdel` → deletes existing users
        
        ![Screenshot_20220126_164548.png](Screenshot_20220126_164548.png)
        
- `uname` → displays the kernel name
    
    ![Screenshot_20220126_154945.png](Screenshot_20220126_154945.png)
    
    - `uname -o` → displays the type
        
        ![Screenshot_20220126_161456.png](Screenshot_20220126_161456.png)
        
    - `uname -m` → displays the architecture
        
        ![Screenshot_20220126_161709.png](Screenshot_20220126_161709.png)
        
    - `uname -r` → displays the kernel version
        
        ![Screenshot_20220126_161740.png](Screenshot_20220126_161740.png)
        
- `id` → displays the group IDs
    
    ![Screenshot_20220126_162853.png](Screenshot_20220126_162853.png)
    
- `getent group driptanil` → checks if ‘driptanil’ group exists
    
    ![Screenshot_20220126_163322.png](Screenshot_20220126_163322.png)
    

### System Information Commands

- `df` → shows the disk size and usage details
    - `df -h` → displays the size and usage details in human readable format.
- `du` → shows the disk usage statistics in working directory
    
    ![Screenshot_20220125_083537.png](Screenshot_20220125_083537.png)
    
    - `du -h` → shows the disk usage statistics in working directory in human readable format.
        
        ![Screenshot_20220125_083727.png](Screenshot_20220125_083727.png)
        
- `cat /etc/os-release` → displays the operation system information
    
    ![Screenshot_20220126_162039.png](Screenshot_20220126_162039.png)
    
- `lscpu` → displays the CPU details
    
    ![Screenshot_20220126_162235.png](Screenshot_20220126_162235.png)
    
- `free` → displays the memory statistics
    
    ![Screenshot_20220126_162456.png](Screenshot_20220126_162456.png)
    
- `vmstat` → displays the virtual memory statistics
    
    ![Screenshot_20220126_162609.png](Screenshot_20220126_162609.png)
    

### Managing Tasks Commands

- `top` → shows all the processes running
    
    ![Screenshot_20220126_154550.png](Screenshot_20220126_154550.png)
    
- `kill` → kills the process with the specified process ID.
- `jobs` → displays the running commands
- `ps aux` → the processes and the process ID
    
    ![Screenshot_20220126_192015.png](Screenshot_20220126_192015.png)
    
- `htop` → shows the processes which are using the resources
    
    ![Screenshot_20220126_154628.png](Screenshot_20220126_154628.png)
    

### Operators

- Ampersand `&`  → This command sends a process/script/command to the background.
    - to kill this background process use `ps` and `kill` command.
- Pipe `|` → The output of the first command acts as input to the second command

- `&&` → executes the second command if and only if the first command is executed successfully.
    
    ![Screenshot_20220126_194519.png](Screenshot_20220126_194519.png)
    
- `||` → executes the second command if and only if the first command fails.
    
    ![Screenshot_20220126_194602.png](Screenshot_20220126_194602.png)
    
- `!` → not operator
    
    ![Screenshot_20220126_194842.png](Screenshot_20220126_194842.png)
    
- `>>` → append
    
    ![Screenshot_20220126_195028.png](Screenshot_20220126_195028.png)
    
- `>` → over-write
    
    ![Screenshot_20220126_195324.png](Screenshot_20220126_195324.png)
    
- Combination `(...)` → group commands using `;`
    
    ![Screenshot_20220126_200354.png](Screenshot_20220126_200354.png)