# 13 Archiving and Transferring Files
## Managing Compressed tar Archives
### The tar Command
### Selected tar Options
1. Tape archive (tar)
    1. `-c`  
        建立打包檔案。
    2. `-x`  
        解開打包檔案。
    3. `-t`  
        查看打包檔案內容。
    4. `-v`  
        查看過程詳細資訊。
    5. `-f`  
        指定檔案。
    6. `-p`  
        使用原來的權限。
    7. `-z`  
        使用GNU zip (gzip)壓縮或解壓縮。
    8. `-j`  
        使用bzip2壓縮或解壓縮。
    9. `-J`  
        使用xz壓縮或解壓縮。
2. GNU zip (gzip)
    ```bash
    $ gzip <SOURCE_FILE>
    ```
    ```bash
    $ gzip -d <GZ_FILE>
    ```
3. GNU unzip (gunzip)
    ```bash
    $ gunzip <GZ_FILE>
    ```
4. Bzip2 (bzip2)
    ```bash
    $ bzip2 <SOURCE_FILE>
    ```
    ```bash
    $ bzip2 -d <BZ2_FILE>
    ```
5. Bunzip2 (bunzip2)
    ```bash
    $ bunzip2 <BZ2_FILE>
    ```
6. Xz (xz)
    ```bash
    $ xz <SOURCE_FILE>
    ```
    ```bash
    $ xz -d <XZ_FILE>
    ```
7. Unxz (unxz)
    ```bash
    $ unxz <XZ_FILE>
    ```
8. Zip (zip)
    ```bash
    $ zip <FILE_NAME> <SOURCE_FILE>
    ```
    ```bash
    $ zip -ry <FILE_NAME> <SOURCE_DIRECTORY>
    ```
9. Unzip (unzip)
    ```bash
    $ unzip <ZIP_FILE>
    ```
### Listing Options of the tar Command
### Archiving Files and Directories
1. Tape archive (tar)
    ```bash
    $ tar -cf <FILE_NAME> <SOURCE_FILE1|SOURCE_DIRECTOR1> <SOURCE_FILE2|SOURCE_DIRECTOR2> ...
    ```
### Listing Contents of an Archive
1. Tape archive (tar)
    ```bash
    $ tar -tf <TAR_FILE>
    ```
### Extracting Files from an Archive
1. Tape archive (tar)
    ```bash
    $ tar -xf <TAR_FILE>
    ```
    ```bash
    $ tar -xpf <TAR_FILE>
    ```
### Creating a Compressed Archive
1. Tape archive (tar)
    ```bash
    $ tar -czf <FILE_NAME> <SOURCE_FILE1|SOURCE_DIRECTOR1> <SOURCE_FILE2|SOURCE_DIRECTOR2> ...
    ```
    ```bash
    $ tar -cjf <FILE_NAME> <SOURCE_FILE1|SOURCE_DIRECTOR1> <SOURCE_FILE2|SOURCE_DIRECTOR2> ...
    ```
    ```bash
    $ tar -cJf <FILE_NAME> <SOURCE_FILE1|SOURCE_DIRECTOR1> <SOURCE_FILE2|SOURCE_DIRECTOR2> ...
    ```
### Extracting a Compressed Archive
1. Tape archive (tar)
    ```bash
    $ tar -xzf <TAR_GZ_FILE>
    ```
    ```bash
    $ tar -xjf <TAR_BZ2_FILE>
    ```
    ```bash
    $ tar -xJf <TAR_XZ_FILE>
    ```
## Transferring Files Between Systems Securely
### Transferring Files Using Secure Copy
1. Secure copy (scp)
    ```bash
    $ scp <FILE1> <FILE2> ... <REMOTE_USER>@<REMOTE_HOST>:<REMOTE_DIRECTORY>
    ```
    ```bash
    $ scp <REMOTE_USER1>@<REMOTE_HOST1>:<REMOTE_FILE1> <REMOTE_USER2>@<REMOTE_HOST2>:<REMOTE_FILE2> ... <DIRECTORY>
    ```
    ```bash
    $ scp -r <DIRECTORY1> <DIRECTORY2> ... <REMOTE_USER>@<REMOTE_HOST>:<REMOTE_DIRECTORY>
    ```
    ```bash
    $ scp -r <REMOTE_USER1>@<REMOTE_HOST1>:<REMOTE_DIRECTORY1> <REMOTE_USER2>@<REMOTE_HOST2>:<REMOTE_DIRECTORY2> ... <DIRECTORY>
    ```
### Transferring Files Using the Secure File Transfer
1. Secure file transfer program (sftp)
    ```bash
    $ sftp <REMOTE_USER>@<REMOTE_HOST>
    ```
    1. `ls`
    2. `cd`
    3. `mkdir`
    4. `rmdir`
    5. `pwd`
    6. `put`
        ```bash
        sftp> put <FILE>
        ```
    7. `get`
        ```bash
        sftp> get <REMOTE_FILE>
        ```
    8. `exit`
## Synchronizing Files Between Systems Securely
### Synchronize Files and Directories with rsync
1. Remote sync (rsync)
    1. `-a`  
        包含以下選項。
        1. `-r`  
            遞迴同步整個目錄。
        2. `-l`  
            保留Soft link。
        3. `-p`  
            保留權限。
        4. `-t`  
            保留時間紀錄。
        5. `-g`  
            保留所屬群組。
        6. `-o`  
            保留所屬使用者。
        7. `-D`  
            保留設備檔。
    8. `-v`  
        查看過程詳細資訊。
    9. `-A`  
        保留ACL。
    10. `-X`  
        保留SELinux標籤。
    11. `-H`  
        保留Hard link。
    ```bash
    $ rsync -avAXH <FILE1|DIRECTORY1> <FILE2|DIRECTORY2> ... <REMOTE_USER>@<REMOTE_HOST>:<REMOTE_DIRECTORY>
    ```
    ```bash
    $ rsync -avAXH <REMOTE_USER1>@<REMOTE_HOST1>:<REMOTE_FILE1|REMOTE_DIRECTORY1> <REMOTE_USER2>@<REMOTE_HOST2>:<REMOTE_FILE2|REMOTE_DIRECTORY2> ... <DIRECTORY>
    ```
## Return to [RH124 Red Hat System Administration I](/rh124_red_hat_system_administration_i/README.md)
