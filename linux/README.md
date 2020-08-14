FAQ

Troubleshooting
### Bootprocess

<details>
<summary>Explain Linux boot process</summary><br><b>
  
![alt_text](https://www.golinuxcloud.com/wp-content/uploads/2018/10/linux_boot_process.png)

</b></details>

<details>
<summary>How to Boot into Single User Mode</summary><br><b>
1. First restart your CentOS 7 machine, once boot process starts, wait for the GRUB boot menu to appear as shown in the screen shot below.

![alt_text](https://www.tecmint.com/wp-content/uploads/2017/08/CentOS-7-Grub-Menu.png)

2. Next, select your Kernel version from the grub menu item and press e key to edit the first boot option. Now use the Down arrow key to find the kernel line (starts with “linux16“), then change the argument ro to rw init=/sysroot/bin/sh as shown in the screen shot below.

![alt_text](https://www.tecmint.com/wp-content/uploads/2017/08/Edit-Grub-Boot-Options.png)

3. Once you have finished the task in the previous step, press Ctrl-X or F10 to boot into single user mode (access an emergency shell).

![alt_text](https://www.tecmint.com/wp-content/uploads/2017/08/CentOS-7-Emergency-Shell.png)

4. Now mount root (/) filesystem using the following command.

<code>#chroot /sysroot/</code>

5. At this point, you can perform all the necessary low-level system maintenance tasks. Once you are done, reboot the system using this command.

<code>#reboot -f</code>

</b></details>

#### star: Filesystem

<details>
<summary>Name the Linux specific partition types?</summary><br><b>
0x82                     >          Linux swap
0x83                     >          Linux
0x8e                     >          Linux LVM
0xfd                     >          Linux RAID auto
0x5                      >          Extended
0xf                      >          Windows partition

</b></details>


<details>
<summary>How many partitions are supported by Linux?</summary><br><b>
 
The maximum number of partitions supported by Linux kernel is:
63 for IDE drives
15 for SCSI drives

</b></details>


<details>
<summary>What are the tools used to create or manage partitions?</summary><br><b>
fdisk
sfdisk
parted (GNU) - An advanced partition manipulation tool (create, copy,resize etc.)
</b></details>


<details>
<summary>What is the function of partprobe?</summary><br><b>
Reinitializes the kernel's in memory copy of the partition table.
</b></details>


<details>
<summary>How to create a filesystem?</summary><br><b>
The mkfs command is used to create the filesystem.

 mkfs.ext2 / mkfs.ext3     >          To create ext2/ext3 filesystem
 mkfs.minix                >          minix filesystem
 mkfs.msdos                >          MS-DOS filesystem
 
</b></details>


<details>
<summary>Which command is used to display information about the processes using a filesystem?</summary><br><b>
  The fuser command is used
  fuser  -v  mnt_point
  fuser  -km  mnt_point
</b></details>


<details>
<summary>What are the fields /etc/fstab containd?</summary><br><b>
  This file is referenced each time the system boots to create the desired filesystem hierarchy
  The /etc/fstab fields are:
  Device         >  Special device/filesystem label dev to mount
  Mount_Point    > The path used to access the filesystem
  fs_type        > The filesystem type
  Options        > List of Options (each is separated by a comma)
  Dump frequency >  Level 0 dump freq (0 = never dump, 1 = daily & 2 = every other day)
  fsck Order     > 0 = ignore, 1 = first (root should have this value), 2 to 9 = 2nd, 3rd and so on NFS & CD-ROM s should be ignored (i.e., value 0)
</b></details>


<details>
<summary>How to set up swap partition?</summary><br><b>
  
Steps involved in setting up swap partition.
         Create a partition using a partitioning program (fdisk/sfdisk/parted)
         Set partition id type to 0x82.
         Create the signature on the partition using the mkswap command
         # mkswap  -v1  /dev/hdb3
        Add an entry for the swap in /etc/fstab file as:
        /dev/hdb3   swap   swap   defaults    0   0
        Activate the swap partition using
        # swapon -a
        Check the swap partition status using
        # swapon  -s
</b></details>


<details>
<summary>How to create a swap file?</summary><br><b>
  Ans.  Create a file as
         # dd  if=/dev/zero  of=swapfile   bs=512  count=N
         (Where N is the file size in KB)
         Run the mkswap to create signature
         Activate the swap file with swapon command (OR) initialize it in the startup
         script /etc/rc.d/rc.local
</b></details>


<details>
<summary>When the system runs the fsck and which script invokes it?</summary><br><b>
  Ans.  When the system boots,  the rc.sysinit script runs the fsck on any filesystems
         marked for checking in /etc/fstab file. If any of these filesystems are markes as  
         dirty or have data in the journal, fsck will attempt to repair them. If it succeeds,
         the filesystems will be mounted and boot process continues, else rc.sysinit will 
         run sulogin and will report that fsck needs to be run manually.
</b></details>


<details>
<summary>After upgrading kernel the machine fails to boot, what will you do?</summary><br><b>
he very first thing to be done here is to edit the grub menu at boot stage and make the system boot with alternative kernel (assuming the last kernel is still installed) or else try booting the system with using the rescue option from the grub menu.

Once the node is UP then you can analyse the issue of why the node is failing to boot from new kernel. Many times the kernel is not properly installed and all the libraries are not available which leads to this problem. or the GRUB can be corrupted so you can regerate the initramfs using grub2-mkconfig
<code># grub2-mkconfig -o /boot/grub2/grub.cfg</code>
If there is a kernel panic observed then boot the system with alternate kernel or rescue and then enable kdump. Share the kdump with the support engineers as they can then further try to debug the source of the problem
</b></details>


<details>
<summary>How do you schedule tasks periodically?</summary><br><b>

You can use the commands <code>cron</code> and <code>at</code>.
With cron, tasks are scheduled using the following format:

<code>*/30 * * * * bash myscript.sh</code> Executes the script every 30 minutes.

<minute> <hour> <day of month> <month> <day of week> <command to execute>

The tasks are stored in a cron file, you can write in it using <code>crontab -e</code>

Alternatively if you are using a distro with systemd it's recommended to use systemd timers.

</b></details>

<details>
<summary>How to check which commands you executed in the past?</summary><br><b>

history command or .bash_history file
</b></details>

<details>
<summary>Explain what is setgid and setuid</summary><br><b>
</b></details>

<details>
<summary>What is the purpose of sticky bit?</summary><br><b>
</b></details>

<details>
<summary>You try to delete a file but it fails. Name at least three different reason as to why it could happen</summary><br><b>

* No more disk space
* No more indoes
* No permissions
</b></details>

<details>
<summary>What is systemd?</summary><br>
<b>
Systemd is a daemon (System 'd', d stands from daemon).

A daemon is a program that runs in the background without direct control of the user, although the user can at any time
talk to the daemon.

systemd has many features such as user processes control/tracking, snapshot support, inhibitor locks..


If we visualize the unix/linux system in layers, systemd would fall directly after the linux kernel.

Hardware -> Kernel -> <u>Daemons</u>, System Libraries, Server Display.
</b>
</details>

<details>
<summary>On a system which uses systemd, how would you display the logs?</summary><br><b>

<code>journalctl</code>
</b></details>
<details>
<summary>What are you using for troubleshooting and debugging <b>network</b> issues?</summary><br><b>

<code>dstat -t</code> is great for identifying network and disk issues.
<code>netstat -tnlaup</code> can be used to see which processes are running on which ports.
<code>lsof -i -P</code> can be used for the same purpose as netstat.
<code>ngrep -d any metafilter</code> for matching regex against payloads of packets.
<code>tcpdump</code> for capturing packets
<code>wireshark</code> same concept as tcpdump but with GUI (optional).
</b></details>

<details>
<summary>What are you using for troubleshooting and debugging <b>disk & file system</b> issues?</summary><br><b>

<code>dstat -t</code> is great for identifying network and disk issues.
<code>opensnoop</code> can be used to see which files are being opened on the system (in real time).
</b></details>

<details>
<summary>What are you using for troubleshooting and debugging <b>process</b> issues?</summary><br><b>

<code>strace</code> is great for understanding what your program does. It prints every system call your program executed.
</b></details>

<details>
<summary>What are you using for debugging CPU related issues?</summary><br><b>

<code>top</code> will show you how much CPU percentage each process consumes
<code>perf</code> is a great choice for sampling profiler and in general, figuring out what your CPU cycles are "wasted" on
<code>flamegraphs</code> is great for CPU consumption visualization (http://www.brendangregg.com/flamegraphs.html)
</b></details>

<details>
<summary>You get a call from someone claiming "my system is SLOW". What do you do?</summary><br><b>

* Check with `top` for anything unusual
* Run `dstat -t` to check if it's related to disk or network.
* Check if it's network related with `sar`
* Check I/O stats with `iostat`
</b></details>

<details>
<summary>Explain iostat output</summary><br><b>
</b></details>

<details>
<summary>How to debug binaries?</summary><br><b>
</b></details>

<details>
<summary>What kind of information one can find in /proc?</summary><br><b>
</b></details>

<details>
<summary>What is the difference between CPU load and utilization?</summary><br><b>
</b></details>

<details>
<summary>How you measure time execution of a program?</summary><br><b>
</b></details>

<details>
<summary>How do you find out which Kernel version your system is using?</summary><br><b>
</b></details>

<details>
<summary>What is a Linux kernel module and how do you load a new module?</summary><br><b>
</b></details>

<details>
<summary>Explain user space and kernel space</summary><br><b>
</b></details>

<details>
<summary>What is KVM?</summary><br><b>
</b></details>

