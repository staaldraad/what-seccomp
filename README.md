# What

A simple binary to check which syscalls are available to the current user.

# How

Each syscall is invoked and the errno is checked. If the errno is EPERM or EACCES it is likely that the action was blocked due to seccomp (if filtering is enabled)

# Installation

Via go:

```
go get github.com/staaldraad/what-seccomp
```

# Example 

```
$ what-seccomp 

Seccomp: filtering
Checking available syscalls...

Allowed Syscalls:
        READ WRITE OPEN CLOSE STAT FSTAT LSTAT POLL LSEEK MMAP MPROTECT MUNMAP BRK RT_SIGACTION RT_SIGPROCMASK IOCTL PREAD64 PWRITE64 READV WRITEV ACCESS PIPE SCHED_YIELD MREMAP MSYNC MINCORE MADVISE SHMGET SHMAT SHMCTL DUP DUP2 NANOSLEEP GETITIMER ALARM SETITIMER GETPID SENDFILE SOCKET CONNECT ACCEPT SENDTO RECVFROM SENDMSG RECVMSG SHUTDOWN BIND LISTEN GETSOCKNAME GETPEERNAME SOCKETPAIR SETSOCKOPT GETSOCKOPT EXECVE WAIT4 KILL UNAME SEMGET SEMOP SEMCTL SHMDT MSGGET MSGSND MSGRCV MSGCTL FCNTL FLOCK FSYNC FDATASYNC TRUNCATE FTRUNCATE GETDENTS GETCWD CHDIR FCHDIR RENAME MKDIR RMDIR CREAT LINK UNLINK SYMLINK READLINK CHMOD FCHMOD CHOWN FCHOWN LCHOWN UMASK GETTIMEOFDAY GETRLIMIT GETRUSAGE SYSINFO TIMES GETUID GETGID SETUID SETGID GETEUID GETEGID SETPGID GETPPID GETPGRP SETREUID SETREGID GETGROUPS SETGROUPS SETRESUID GETRESUID SETRESGID GETRESGID GETPGID SETFSUID SETFSGID GETSID CAPGET CAPSET RT_SIGPENDING RT_SIGTIMEDWAIT RT_SIGQUEUEINFO RT_SIGSUSPEND SIGALTSTACK UTIME MKNOD PERSONALITY STATFS FSTATFS GETPRIORITY SETPRIORITY SCHED_SETPARAM SCHED_GETPARAM SCHED_SETSCHEDULER SCHED_GETSCHEDULER SCHED_GET_PRIORITY_MAX SCHED_GET_PRIORITY_MIN SCHED_RR_GET_INTERVAL MLOCK MUNLOCK MLOCKALL MUNLOCKALL MODIFY_LDT PRCTL ARCH_PRCTL ADJTIMEX SETRLIMIT CHROOT SYNC GETTID READAHEAD SETXATTR LSETXATTR FSETXATTR GETXATTR LGETXATTR FGETXATTR LISTXATTR LLISTXATTR FLISTXATTR REMOVEXATTR LREMOVEXATTR FREMOVEXATTR TKILL TIME FUTEX SCHED_SETAFFINITY SCHED_GETAFFINITY SET_THREAD_AREA IO_SETUP IO_DESTROY IO_GETEVENTS IO_SUBMIT IO_CANCEL GET_THREAD_AREA EPOLL_CREATE EPOLL_CTL_OLD EPOLL_WAIT_OLD REMAP_FILE_PAGES GETDENTS64 SET_TID_ADDRESS RESTART_SYSCALL SEMTIMEDOP FADVISE64 TIMER_CREATE TIMER_SETTIME TIMER_GETTIME TIMER_GETOVERRUN TIMER_DELETE CLOCK_GETTIME CLOCK_GETRES CLOCK_NANOSLEEP EPOLL_WAIT EPOLL_CTL TGKILL UTIMES MQ_OPEN MQ_UNLINK MQ_TIMEDSEND MQ_TIMEDRECEIVE MQ_NOTIFY MQ_GETSETATTR WAITID IOPRIO_SET IOPRIO_GET INOTIFY_INIT INOTIFY_ADD_WATCH INOTIFY_RM_WATCH OPENAT MKDIRAT MKNODAT FCHOWNAT NEWFSTATAT UNLINKAT RENAMEAT LINKAT SYMLINKAT READLINKAT FCHMODAT FACCESSAT SET_ROBUST_LIST GET_ROBUST_LIST SPLICE TEE SYNC_FILE_RANGE VMSPLICE EPOLL_PWAIT SIGNALFD TIMERFD_CREATE EVENTFD FALLOCATE TIMERFD_SETTIME TIMERFD_GETTIME ACCEPT4 SIGNALFD4 EVENTFD2 EPOLL_CREATE1 DUP3 PIPE2 INOTIFY_INIT1 PREADV PWRITEV RT_TGSIGQUEUEINFO RECVMMSG FANOTIFY_MARK PRLIMIT64 SYNCFS SENDMMSG GETCPU

Blocked Syscalls:
        PTRACE SYSLOG SETSID USELIB USTAT SYSFS VHANGUP PIVOT_ROOT _SYSCTL ACCT SETTIMEOFDAY MOUNT UMOUNT2 SWAPON SWAPOFF REBOOT SETHOSTNAME SETDOMAINNAME IOPL IOPERM CREATE_MODULE INIT_MODULE DELETE_MODULE GET_KERNEL_SYMS QUERY_MODULE QUOTACTL NFSSERVCTL GETPMSG PUTPMSG AFS_SYSCALL TUXCALL SECURITY LOOKUP_DCOOKIE CLOCK_SETTIME VSERVER MBIND SET_MEMPOLICY GET_MEMPOLICY KEXEC_LOAD ADD_KEY REQUEST_KEY KEYCTL MIGRATE_PAGES FUTIMESAT UNSHARE MOVE_PAGES UTIMENSAT PERF_EVENT_OPEN FANOTIFY_INIT NAME_TO_HANDLE_AT OPEN_BY_HANDLE_AT CLOCK_ADJTIME SETNS PROCESS_VM_READV PROCESS_VM_WRITEV KCMP FINIT_MODULE
```

