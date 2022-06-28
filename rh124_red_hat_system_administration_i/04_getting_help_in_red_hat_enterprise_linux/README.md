# 04 Getting Help in Red Hat Enterprise Linux
## Reading Manual Page
### Introducing the man command
1. Manual pages (man)  
    查詢指令的檔案存放在`/usr/share/doc`，另外查詢指令的網址在[http://www.redhat.com/docs](https://www.redhat.com/docs)。
    ```bash
    $ man <COMMAND> #查看命令(<COMMAND>)詳細資訊，常見符號有[]選項、<>必填、...可多個、|選項
    $ man passwd
    ```
    ```bash
    $ man <SECTION> <COMMAND> #查看命令(<COMMAND>)的指定章節(<SECTION>)
    $ man 5 passwd
    ```
2. Print manual pages
    ```bash
    $ man -t fdisk > fdisk.ps #將資料轉為PostScript(ps)格式
    $ ps2pdf fdisk.ps #將ps格式轉為pdf格式
    ```
### Navigate and Search Man Pages
1. Navigating man pages
    1. `Space`  
        向下捲動一個視窗。
    2. `b`  
        向上捲動一個視窗。
    3. `g`  
        移至頁首。
    4. `G`  
        移至頁尾。
    5. `/<REGEX_KEYWORD>`  
        向下查詢正規表達式關鍵字(`<REGEX_KEYWORD>`)。
    6. `n`  
        向下查看查詢結果。
    7. `N`  
        向上查看查詢結果。
    8. `q`  
        離開。
### Searching for man pages by keyword
1. Searching for man pages by keyword
    ```bash
    $ mandb #初始化或手動更新索引快取資料庫
    $ whatis <COMMAND> #查看命令(<COMMAND>)摘要
    $ man -k <KEYWORD> #查看包含關鍵字(<KEYWORD>)的指令摘要
    ```
## Reading Info Documentation
### Introducing GNU Info
1. Pinfo (pinfo)
    ```bash
    $ pinfo #用選項選擇查看命令及詳細資訊
    ```
    ```bash
    $ pinfo <COMMAND> #用選項查看命令(<COMMAND>)詳細資訊
    ```
### Comparing GNU Info and Man Page Navigation
1. Navigating pinfo
    1. `Space`  
        向下捲動一個視窗。
    2. `b`  
        向上捲動一個視窗。
    3. `/<REGEX_KEYWORD>`  
        向下查詢正規表達式關鍵字(`<REGEX_KEYWORD>`)。
    4. `q`  
        離開。
## Return to [RH124 Red Hat System Administration I](/rh124_red_hat_system_administration_i/README.md)
