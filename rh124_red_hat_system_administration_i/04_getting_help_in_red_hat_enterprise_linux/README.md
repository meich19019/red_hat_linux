# 04 Getting Help in Red Hat Enterprise Linux
## Introducing the man command
1. Manual pages (man)
    ```bash
    $ man <COMMAND> #查看指令(<COMMAND>)詳細資訊，常見符號有[]選項、<>必填、...可多個、|選項
    $ man passwd
    ```
    ```bash
    $ man <SECTION> <COMMAND> #查看指令(<COMMAND>)的指定章節(<SECTION>)
    $ man 5 passwd
    ```
    ```bash
    $ mandb #初始化或手動更新索引快取資料庫
    $ whatis <COMMAND> #查看指令(<COMMAND>)摘要
    $ man -k <KEYWORD> #查看包含關鍵字(<KEYWORD>)的指令摘要
    ```
## Return to [RH124 Red Hat System Administration I](/rh124_red_hat_system_administration_i/README.md)
