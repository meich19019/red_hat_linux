# 02 Accessing the Command Line
## Accessing the Command Line
### Introduction to the Bash Shell
1. Command line 命令行  
    一個純文字介面的應用程式。
2. GNU bourne-again shell (bash)  
    Red Hat Enterprise Linux的預設使用者shell為bash，bash是基於Bourne shell (sh)改進而來。
3. Shell prompt 命令提示字元  
    顯示一段字串等待使用者的命令，命令提示字元可依使用者需求自行修改，預設一般使用者命令提示字元為`[user@host ~]$`，預設超級使用者命令提示字元為`[root@host ~]#`。
4. Hostname (hostname)
    ```bash
    $ hostname #查看完整主機名稱
    ```
    ```bash
    $ hostname -s #查看簡短主機名稱
    ```
5. Manual pages (man)
    ```bash
    $ man <COMMAND> #查看指令(<COMMAND>)詳細資訊，常見符號有[]選項、<>必填、...可多個、|選項
    ```
### Shell Basics
1. User modify (usermod)
    ```bash
    $ usermod -L <USER> #鎖定使用者(<USER>)
    ```
### Logging in to a Local Computer
1. Terminal 終端機  
    用來讓使用者輸入資料，及顯示其計算結果的一台裝置。
2. Physical console 實體控制台  
    直接連接到電腦系統的螢幕、鍵盤和滑鼠。
3. Virtual consoles 虛擬控制台  
    模擬終端機裝置連接到電腦系統的應用程序。
4. Graphical environment 圖形環境  
    用圖形方式顯示的電腦操作使用者介面。
5. Headless server 無頭伺服器  
    已設定為無須螢幕、鍵盤和滑鼠操作的伺服器。
### Logging in over the Network
1. Secure shell (ssh) 安全外殼協定  
    一種加密的網路傳輸協定，ssh通過在網路中建立安全隧道來實現ssh客戶端與伺服器之間的連接。
    ```bash
    $ ssh <REMOTE_USER>@<REMOTE_HOST> #透過SSH以使用者(<REMOTE_USER>)遠端登入系統(<REMOTE_HOST>)
    ```
    ```bash
    $ ssh -i <PRIVATE_KEY> <REMOTE_USER>@<REMOTE_HOST> #透過ssh指定私密金鑰(<PRIVATE_KEY>)以使用者(<REMOTE_USER>)遠端登入系統(<REMOTE_HOST>)
    $ ssh -i mylab.pem student@workstation
    ```
2. OpenBSD secure shell (OpenSSH)  
    使用ssh透過計算機網路加密通訊的實現，此設定存放在`/etc/ssh/sshd_config`。
3. SSH Tunnel  
    利用ssh協定來建立這個隧道通訊傳送資料。
4. Public key authentication 公開金鑰認證  
    使用這種身份驗證方法，使用者有一個包含私密金鑰的特殊身份文件，相當於密碼，並且經過加密。而在遠端伺服器上的帳號配置有相對應的公開金鑰，該公開金鑰不必加密。登入時，使用者設置SSH提供私密金鑰，如果此私密金鑰有對應的公開金鑰安裝在遠端伺服器上的該帳號中，使用者將在不被要求輸入密碼的情況下登入。
5. Private key 私密金鑰  
    私密金鑰不可以公開，必須由使用者自行嚴格秘密保管，絕不透過任何途徑向任何人提供，也不會透露給被信任的要通訊的另一方。
6. Public key 公開金鑰  
    公開金鑰可以公開，可任意向外發佈。
### Logging Out
1. Exit (exit)
    ```bash
    $ exit #結束遠端連線登出系統
    ```
## Accessing the Command Line Using the Desktop
### Introduction to the GNOME Desktop Environment
1. Desktop environment 桌面環境  
    由多個軟體組成，這些軟體提供給電腦使用者視窗、資料夾、工具列、桌布、圖示以及拖放等服務。
2. Compiz  
    由OpenGL驅動的執行於X Window System上的混合視窗管理員，Compiz的混合彩現能力使其可以在窗口管理過程中實現多種視覺效果。
3. Gnome tweaks  
    GNOME優化工具，讓使用者能夠以直觀、簡單的方式自定義桌面。
### Workspaces
### Starting a Terminal
### Locking the Screen or Logging Out
### Powering off or Rebooting the System
1. Clear (clear)
    ```bash
    $ clear #清空終端機
    ```
2. User add (useradd)
    ```bash
    $ useradd <USER> #建立使用者(<USER>)
    ```
3. Password (passwd)
    ```bash
    $ passwd #變更目前使用者密碼
    ```
    ```bash
    $ passwd <USER> #建立或變更使用者(<USER>)密碼
    ```
## Executing Commands Using the Bash Shell
### Basic Command Syntax
1. Who am I (whoami)
    ```bash
    $ whoami #查看當前使用者名稱
    ```
### Examples of Simple Commands
1. Date (date)
    ```bash
    $ date #查看作業系統時間
    ```
    ```bash
    $ date -s #用字串設定作業系統時間
    ```
    ```bash
    $ date +<FORMAT> #指定格式(<FORMAT>)查看作業系統時間
    ```
    ```bash
    $ clock -w #將作業系統時間同步回RTC
    ```
2. Password (passwd)
    ```bash
    $ passwd #變更目前使用者密碼
    ```
    ```bash
    $ passwd <USER> #建立或變更使用者(<USER>)密碼
    ```
3. File (file)
    ```bash
    $ file <FILE> #查看檔案(<FILE>)格式
    ```
### Viewing the Contents of Files
1. List (ls)
    ```bash
    $ ls #查看工作目錄下檔案名稱
    ```
    ```bash
    $ ls <FILE|DIRECTORY> #查看檔案或目錄(<FILE|DIRECTORY>)下檔案或目錄名稱
    ```
    ```bash
    $ ls -l <FILE|DIRECTORY> #查看檔案或目錄(<FILE|DIRECTORY>)下檔案或目錄名稱及詳細資訊
    ```
    ```bash
    $ ls -l <FILE|DIRECTORY> | less #查看檔案或目錄(<FILE|DIRECTORY>)下檔案或目錄名稱及詳細資訊並可上下瀏覽
    ```
    ```bash
    $ ls -a <FILE|DIRECTORY> #查看檔案或目錄(<FILE|DIRECTORY>)下包含隱藏檔案的所有檔案或目錄名稱
    ```
2. Concatenate (cat)
    ```bash
    $ cat <FILE> #查看檔案(<FILE>)內容
    ```
    ```bash
    $ cat <FILE1> <FILE2> ... #查看多個檔案(<FILE1>, <FILE2>, ...)內容
    ```
    ```bash
    $ cat -A <FILE> #查看檔案(<FILE>)內容所有一般及控制字元
    ```
    ```bash
    $ unix2dos #Unix字元轉Windows字元
    $ dos2unix #Windows字元轉Unix字元
    ```
3. Split (split) and Concatenate (cat)
    ```bash
    $ split -b <BLOCK_SIZE> <SOURCE_FILE> <FILE_NAME> #將來源檔案(<SOURCE_FILE>)用指定的區塊大小(<BLOCK_SIZE>)切割成多個目標檔案(<FILE_NAME>1, <FILE_NAME>2, ...)
    $ split -b 50M boot.iso file_ 
    $ cat <SOURCE_FILE1> <SOURCE_FILE2> ... > <FILE_NAME> #將多個來源檔案(<SOURCE_FILE1>, <SOURCE_FILE2>, ...)重組成目標檔案(FILE_NAME)
    $ cat file_* > boot.iso
    ```
3. Head (head) and Tail (tail)
    ```bash
    $ head <FILE> #查看檔案(<FILE>)內容前10行
    ```
    ```bash
    $ tail <FILE> #查看檔案(<FILE>)內容後10行
    ```
    ```bash
    $ tail -n <NUMBER> <FILE> #查看檔案(<FILE>)內容後(<NUMBER>)行
    ```
    ```bash
    $ tail -f <FILE> #持續查看檔案(<FILE>)內容後10行
    ```
4. Word count (wc)
    ```bash
    $ wc <FILE> #查看檔案(<FILE>)行數、詞數、字數
    ```
    ```bash
    $ wc <FILE1> <FILE2> ... #查看多個檔案(<FILE1>, <FILE2>, ...)行數、詞數、字數、總計
    ```
    ```bash
    $ wc -l <FILE> #查看檔案(<FILE>)行數
    ```
    ```bash
    $ wc -w <FILE> #查看檔案(<FILE>)詞數
    ```
    ```bash
    $ wc -c <FILE> #查看檔案(<FILE>)字數
    ```
### Tab Completion
1. BASH completion  
    增強BASH自動補齊功能。
### Continuing a Long Command on Another Line
### Command History
1. History (history)  
    查看曾經下達過的命令，各使用者命令歷史紀錄預設存放在`~/.bash_history`。
    ```bash
    $ history #查看命令歷史紀錄
    $ !<COMMAND> #重下此命令(<COMMAND>)在命令歷史紀錄中最近一次的命令
    $ !<NUMBER> #重下此數字(<NUMBER>)在命令歷史紀錄中的命令
    ```
### Editing the Command Line
## Return to [RH124 Red Hat System Administration I](/rh124_red_hat_system_administration_i/README.md)
