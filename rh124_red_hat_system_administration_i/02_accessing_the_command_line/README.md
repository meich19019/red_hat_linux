# 02 Accessing the Command Line
## Accessing the Command Line
### Introduction to the Bash Shell
1. Command line 命令行
    一個純文字介面的應用程式。
2. GNU Bourne-Again Shell (BASH)  
    Red Hat Enterprise Linux的預設使用者shell為BASH，BASH是基於Bourne Shell (SH)改進而來。
3. Shell prompt 命令提示字元
    顯示一段字串等待使用者的命令，命令提示字元可依使用者需求自行修改，預設一般使用者命令提示字元為`[user@host ~]$`，預設超級使用者命令提示字元為`[root@host ~]#`。
```bash
$ hostname #查看完整主機名稱
```
```bash
$ hostname -s #查看簡短主機名稱
```
```bash
$ man #查詢指令，常見符號有[]選項、<>必填、...可多個、|選項
```
### Shell Basics
```bash
$ usermod -L user1 #鎖定帳號(user1)
```
### Logging in to a Local Computer
1. Terminal 終端機
2. Physical console 實體控制台
3. Virtual consoles 虛擬控制台
4. Graphical environment 圖形環境
5. Headless server 無頭伺服器  
    已設定為無須顯示器、鍵盤和滑鼠操作的伺服器。
### Logging in over the Network
1. Secure Shell (SSH) 安全外殼協定  
    一種加密的網路傳輸協定，SSH通過在網路中建立安全隧道來實現SSH客戶端與伺服器之間的連接。
2. OpenBSD Secure Shell (OpenSSH)  
    使用SSH透過計算機網路加密通訊的實現。
3. SSH Tunnel SSH隧道  
    利用SSH協定來建立這個隧道通訊傳送資料。
```bash
$ ssh remoteuser@remotehost #透過SSH以使用者(remoteuser)遠端登入系統(remotehost)
```
4. Public key authentication 公開金鑰認證
5. Private key 私密金鑰
6. Public key 公開金鑰
```bash
$ ssh -i mylab.pem remoteuser@remotehost #透過SSH指定私密金鑰(mylab.pem)以使用者(remoteuser)遠端登入系統(remotehost)
```
### Logging Out
```bash
$ exit #結束遠端連線登出系統
```
---
## Accessing the Command Line Using the Desktop
### Introduction to the GNOME Desktop Environment
1. Desktop environment 桌面環境
2. Compiz 
    由OpenGL驅動的執行於X Window System上的混合視窗管理員，Compiz的混合彩現能力使其可以在窗口管理過程中實現多種視覺效果。
3. Gnome Tweaks  
    GNOME優化工具，讓使用者能夠以直觀、簡單的方式自定義桌面。
### Workspaces
### Starting a Terminal
### Locking the Screen or Logging Out
### Powering off or Rebooting the System
```bash
$ clear #清空終端機
```
```bash
$ useradd user01 #建立帳號(user1)
```
```bash
$ passwd user01 #對帳號(user1)建立密碼或變更密碼
```
```bash
$ passwd #變更此帳號的密碼
```
---
## Executing Commands Using the Bash Shell
### Basic Command Syntax
```bash
$ whoami #查看當前使用者名稱
```
## Examples of Simple Commands
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
```bash
$ passwd #變更此帳號的密碼
```
```bash
$ file <FILE> #查看檔案(<FILE>)格式
```
### Viewing the Contents of Files
```bash
$ ls <PATH> #查看路徑(<PATH>)下檔案名稱
```
```bash
$ ls -l <PATH> #查看路徑(<PATH>)下檔案名稱及詳細資訊
```
```bash
$ ls -l <PATH> | less #查看路徑(<PATH>)下檔案名稱及詳細資訊並可上下瀏覽
```
```bash
$ ls -a <PATH> #查看路徑(<PATH>)下包含隱藏檔案的所有檔案名稱
```
```bash
$ cat <FILE> #查看檔案(<FILE>)內容
```
```bash
$ cat <FILE1> <FILE2> #查看多個檔案(<FILE1>, <FILE2>)內容
```
```bash
$ cat -A <FILE> #查看檔案(<FILE>)內容所有一般及控制字元
```
```bash
$ unix2dos #Unix字元轉Windows字元
```
```bash
$ dos2unix #Windows字元轉Unix字元
```
```bash
$ split -b 50M boot.iso file_ #將檔案(boot.iso)切割成多個檔案(file_1, file_2, ...)
```
```bash
$ cat file_* > boot.iso #將多個檔案(file_1, file_2, ...)重組成檔案(boot.iso)
```
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
```bash
$ wc <FILE> #查看檔案(<FILE>)行數、詞數、字數
```
```bash
$ wc <FILE1> <FILE2> #查看多個檔案(<FILE1>, <FILE2>)行數、詞數、字數、總計
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
1. BASH Completion
    增強BASH自動補齊功能
### Continuing a Long Command on Another Line
### Command History
1. History
    查看曾經下達過的命令，命令歷史紀錄存放在各使用者的家目錄下`~/.bash_history`。
```bash
$ history #查看命令歷史紀錄
```
```bash
$ !<COMMAND> #重下此命令(COMMAND)在命令歷史紀錄中最近一次的命令
```
```bash
$ !<NUMBER> #重下此數字(NUMBER)在命令歷史紀錄中的命令
```
### Editing the Command Line

## Return to [RH124 Red Hat System Administration I](/rh124_red_hat_system_administration_i/README.md)
