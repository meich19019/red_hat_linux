# 03 Managing Files From the Command Line
## Describing Linux File System Hierarchy Concepts
### The File-system Hierarchy
1. File-system hierarchy 檔案系統階層  
    定義了Linux作業系統中的主要目錄及目錄內容。
2. Home directory 家目錄  
    在多使用者作業系統上包含該系統特定使用者檔案的檔案系統目錄。
## Specifying Files by Name
### Absolute Paths and Relative Paths
1. Absolute Paths 絕對路徑  
    一個完全確保的名稱，指定檔案系統階層結構中檔案的確切位置。
2. Relative Paths 相對路徑  
    定義一個唯一檔案，僅指定從工作目錄到達該檔案所需的路徑。
3. Working directory 工作目錄  
    使用者在作業系統內所在的目錄。
4. Linux file systems
    1. Fourth extended filesystem (ext4) 第四代擴充套件檔案系統  
        Linux系統下的日誌檔案系統，是ext3檔案系統的後繼版本。
    2. Extents file system (XFS)  
        高效能的日誌檔案系統，特別擅長處理大檔案，同時提供平滑的資料傳輸。
5. Non-Linux file systems
    1. File Allocation Table (FAT) 檔案配置表  
        微軟發明並擁有部分專利的檔案系統，供MS-DOS使用。
    2. Extended File Allocation Table (exFAT)  
        微軟開發的一種較適合於快閃記憶體的檔案系統。
        ```bash
        $ yum install fuse-exfat #安裝套件讀寫exFAT
        ```
    3. New Technology File System (NTFS)
        微軟開發的專用檔案系統，從Windows NT 3.1開始成為Windows NT家族的預設檔案系統。
        ```bash
        $ yum install ntfs-3g #安裝套件讀寫NTFS
        ```
    4. Hierarchical File System (HFS) 分層檔案系統  
        蘋果開發，並使用在Mac OS上的檔案系統。
    5. Hierarchical File System Plus (HFS+)  
        蘋果為替代他們的分層檔案系統(HFS)而開發的一種檔案系統，改善了HFS對磁碟空間的位址定位效率。
## Return to [RH124 Red Hat System Administration I](/rh124_red_hat_system_administration_i/README.md)
