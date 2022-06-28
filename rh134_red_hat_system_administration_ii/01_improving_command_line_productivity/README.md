# 01 Improving Command-line Productivity
## Writing Simple Bash Scripts
### Creating and Executing Bash Shell Scripts
1. Protecting arguments from expansion
    ```bash
    $ echo ${HOME} #顯示變數(HOME)的值
    $ echo \${HOME} #因跳脫字元顯示變數名稱(${HOME})
    ```
    ```bash
    $ echo file{1..3}, ${HOME}, $(hostname -s) #顯示命令(file1, file2, file3, /home/meich, meich-ubuntu)
    $ echo "file{1..3}, ${HOME}, $(hostname -s)" #因雙引號顯示命令(file{1..3}, /home/meich, meich-ubuntu)
    $ echo 'file{1..3}, ${HOME}, $(hostname -s)' #因單引號顯示命令(file{1..3}, ${HOME}, $(hostname -s))
    ```
## Running Commands More Efficiently Using Loops
### Using Loops to Iterate Commands
### Using Exit Codes Within a Script
### Testing Script Inputs
### Conditional Structures
## Matching Text in Command Output with Regular Expressions
### Writing Regular Expressions
### Matching Regular Expressions with Grep
1. Global search a regular expression and print (grep)
    ```bash
    $ grep <REGEX_KEYWORD> <FILE>
    ```
    ```bash
    $ grep -i <REGEX_KEYWORD> <FILE>
    ```
    ```bash
    $ grep -v <REGEX_KEYWORD> <FILE>
    ```
    ```bash
    $ grep -r <REGEX_KEYWORD> <FILE|DIRECTORY>
    ```
    ```bash
    $ grep -n <REGEX_KEYWORD> <FILE>
    ```
    ```bash
    $ grep -f <REGEX_KEYWORD_FILE> <FILE>
    ```
    ```bash
    $ grep -e <REGEX_KEYWORD1> -e <REGEX_KEYWORD2> ... <FILE>
    $ grep -e 'root' -e 'sshd' /etc/passwd
    ```
    ```bash
    $ grep -A <NUMBER> <REGEX_KEYWORD> <FILE>
    ```
    ```bash
    $ grep -B <NUMBER> <REGEX_KEYWORD> <FILE>
    ```
    ```bash
    $ grep -E <EXTEND_REGEX_KEYWORD> <FILE>
    ```
## Return to [RH134 Red Hat System Administration II](/rh134_red_hat_system_administration_ii/README.md)
