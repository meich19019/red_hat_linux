# 08 Monitoring and Managing Linux Processes
## Listing Processes
### Definition of a Process
1. Process
2. Process Identification (PID)
3. Parent's Process Identification (PPID)
4. Processes tree (pstree)
    ```bash
    $ pstree
    ```
### Describing Process States
1. Linux process states
    1. Running TASK_RUNNING (R)
    2. Sleeping TASK_INTERRUPTIBLE (S)
    3. Sleeping TASK_UNINTERRUPTIBLE (D)
    4. Sleeping TASK_KILLABLE (K)
    5. Sleeping TASK_REPORT_IDLE (I)
    6. Stopped TASK_STOPPED (T)
    7. Stopped TASK_TRACED (T)
    8. Zombie EXIT_ZOMBIE (Z)
    9. Zombie EXIT_DEAD (X)
2. Process ID of (pidof)
    ```bash
    $ pidof <COMMAND>
    ```
3. Table of processes (top)
    ```bash
    $ top
    ```
### Listing Processes
1. Process Status (ps)
    ```bash
    $ ps
    ```
    ```bash
    $ ps a
    ```
    ```bash
    $ ps x
    ```
    ```bash
    $ ps u
    ```
    ```bash
    $ ps l
    ```
    ```bash
    $ ps o
    ```
    ```bash
    $ ps --sort
    ```
    ```bash
    $ ps aux
    ```
    ```bash
    $ ps lax
    ```
    ```bash
    $ ps -ef
    ```
## Controlling Jobs
### Describing Jobs and Sessions
1. Job
2. Foreground process
3. Background process
4. Session
### Running Jobs in the Background
1. Foreground and Background
    ```bash
    $ sleep 10000
    ```
    ```bash
    $ sleep 10000 &
    ```
    ```bash
    $ Ctrl+z
    ```
2. Foreground (fg)
    ```bash
    $ fg %<JOB_NUMBER>
    ```
3. Jobs (jobs)
    ```bash
    $ jobs
    ```
4. Background (bg)
    ```bash
    $ bg %<JOB_NUMBER>
    ```
## Killing Processes
### Process control using signals
1. Signal
2. Kill (kill)
    ```bash
    $ kill -l
    ```
    ```bash
    $ kill <PID>
    $ kill -15 <PID>
    ```
    ```bash
    $ kill -<SIGNAL_NUMBER|SIGNAL_NAME> <PID>
    ```
3. Killall (killall)
    ```bash
    $ killall <COMMAND>
    ```
    ```bash
    $ killall -u <USER> <COMMAND>
    ```
4. Process kill (pkill)
    ```bash
    $ pkill <COMMAND>
    ```
### Logging Users Out Administratively
1. Who and What (w)
    ```bash
    $ w
    ```
2. Process Global search a Regular Expression and Print (pgrep)
    ```bash
    $ pgrep -l -u <USER>
    ```
## Monitoring Process Activity
### Describing Load Average
1. Uptime (uptime)
    ```bash
    $ uptime
    ```
2. List CPU (lscpu)
    ```bash
    $ lscpu
    ```
### Real-time Process Monitoring
1. Table of processes (top)
    ```bash
    $ top
    ```
## Return to [RH124 Red Hat System Administration I](/rh124_red_hat_system_administration_i/README.md)
