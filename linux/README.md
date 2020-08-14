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

![alt_text](https://zohodiscussions.com/viewImage.do?fileId=18151000001631240&forumGroupURL=site24x7)

Applying that to the load average output (0.5, 1.5, 3.0) that we got above: 

0.5 means the minimum waiting time at the counter. Between 0.00 and 1.0, there is no need to worry. Your servers are safe!
1.5 means the queue is filling up. If the average gets any higher, things are going to start slowing down.
3.00 means there's a considerably long queue waiting, and an extra resource/counter is required to clear up the queue faster. 

</b></details>

<details>
<summary>You get a call from someone claiming "my system is SLOW". What do you do?</summary><br><b>

* Check with `top` for anything unusual
* Run `dstat -t` to check if it's related to disk or network.
* Check if it's network related with `sar`
* Check I/O stats with `iostat`

![alt_text](https://zohodiscussions.com/viewImage.do?fileId=18151000001631240&forumGroupURL=site24x7)

Applying that to the load average output (0.5, 1.5, 3.0) that we got above: 

0.5 means the minimum waiting time at the counter. Between 0.00 and 1.0, there is no need to worry. Your servers are safe!
1.5 means the queue is filling up. If the average gets any higher, things are going to start slowing down.
3.00 means there's a considerably long queue waiting, and an extra resource/counter is required to clear up the queue faster. 

On a single core system this would mean:
-----------------------------------------
The CPU was fully (100%) utilized on average; 1 processes was running on the CPU (1.00) over the last 1 minute.
The CPU was idle by 60% on average; no processes were waiting for CPU time (0.40) over the last 5 minutes.
The CPU was overloaded by 235% on average; 2.35 processes were waiting for CPU time (3.35) over the last 15 minutes.

On a dual-core system this would mean:
-----------------------------------------
The one CPU was 100% idle on average, one CPU was being used; no processes were waiting for CPU time(1.00) over the last 1 minute.
The CPUs were idle by 160% on average; no processes were waiting for CPU time. (0.40) over the last 5 minutes.
The CPUs were overloaded by 135% on average; 1.35 processes were waiting for CPU time. (3.35) over the last 15 minutes.


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
 
On Linux at least, the load average and CPU utilization are actually two different things. Load average is a measurement of how many tasks are waiting in a kernel run queue (not just CPU time but also disk activity) over a period of time. CPU utilization is a measure of how busy the CPU is right now. The most load that a single CPU thread pegged at 100% for one minute can "contribute" to the 1 minute load average is 1. A 4 core CPU with hyperthreading (8 virtual cores) all at 100% for 1 minute would contribute 8 to the 1 minute load average.

</b></details>

<details>
<summary>How you measure time execution of a program?</summary><br><b>
  
![alt_text](https://geek-university.com/wp-content/images/linux/time_command.jpg)

</b></details>

<details>
<summary>How do you find out which Kernel version your system is using?</summary><br><b>
  <code>#uname -r</code>
</b></details>

<details>
<summary>What is a Linux kernel module and how do you load a new module?</summary><br><b>
  To load a kernel module, run modprobe module_name as root. 
</b></details>

<details>
<summary>Explain user space and kernel space</summary><br><b>
Memory get's divided into two distinct areas:

The user space, which is a set of locations where normal user processes run (i.e everything other than the kernel). The role of the kernel is to manage applications running in this space from messing with each other, and the machine.
The kernel space, which is the location where the code of the kernel is stored, and executes under.
</b></details>

<details>
<summary>What is KVM?</summary><br><b>
Kernel-based Virtual Machine is a virtualization module in the Linux kernel that allows the kernel to function as a hypervisor. It was merged into the Linux kernel mainline in kernel version 2.6.20
</b></details>


#### Processes

<details>
<summary>How to run a process in the background and why to do that in the first place?</summary><br><b>

You can achieve that by specifying & at end of the command.
As to why, since some commands/processes can take a lot of time to finish
execution or run forever
</b></details>

<details>
<summary>How can you find how much memory a specific process consumes?</summary><br><b>
</b></details>

<details>
<summary>What signal is used by default when you run 'kill *process id*'?</summary><br><b>
<pre>
The default signal is SIGTERM (15). This signal kills
process gracefully which means it allows it to save current
state configuration.
</pre>
</b></details>

<details>
<summary>What signals are you familiar with?</summary><br><b>

SIGTERM - default signal for terminating a process
SIGHUP - common usage is for reloading configuration
SIGKILL - a signal which cannot caught or ignored

To view all available signals run `kill -l`
</b></details>

<details>
<summary>What <code>kill 0</code> does?</summary><br><b>
</b></details>

<details>
<summary>What <code>kill -0 <PID></code> does?</summary><br><b>
</b></details>

<details>
<summary>What is a trap?</summary><br><b>
</b></details>

<details>
<summary>What happens when you press ctrl + c?</summary><br><b>
</b></details>

<details>
<summary>What are daemons?</summary><br><b>
</b></details>

<details>
<summary>What are the possible states of a process in Linux?</summary><br><b>
<pre>
Running (R)
Uninterruptible Sleep (D) - The process is waiting for I/O
Interruptible Sleep (S)
Stopped (T)
Dead (x)
Zombie (z)
</pre>
</b></details>

<details>
<summary>How do you kill a process in D state?</summary><br><b>
</b></details>

<details>
<summary>What is a zombie process?</summary><br><b>

A process which has finished to run but has not exited.

One reason it happens is when a parent process is programmed incorrectly. Every parent process should execute wait() to get the exit code from the child process which finished to run. But when the parent isn't checking for the child exit code, the child process can still exists although it finished to run.
</b></details>

<details>
<summary>How to get rid of zombie processes?</summary><br><b>

You can't kill a zombie process the regular way with `kill -9` for example as it's already dead.

One way to kill zombie process is by sending SIGCHLD to the parent process telling it to terminate its child processes. This might not work if the parent process wasn't programmed properly. The invocation is `kill -s SIGCHLD [parent_pid]`

You can also try closing/terminating the parent process. This will make the zombie process a child of init (1) which does periodic cleanups and will at some point clean up the zombie process.
</b></details>

<details>
<summary>How to find all the

  * Processes executed/owned by a certain user
  * Process which are Java processes
  * Zombie Processes
</summary><br><b>

If you mention at any point ps command with arugments, be familiar with what these arguments does exactly.
</b></details>

<details>
<summary>What is the init process?</summary><br><b>
</b></details>

<details>
<summary>How to change the priority of a process? Why would you want to do that?</summary><br><b>
</b></details>

<details>
<summary>Can you explain how network process/connection is established and how it's terminated?></summary><br></b>
</b></details>

<details>
<summary>What are system calls? What system calls are you familiar with?</summary><br><b>
</b></details>

<details>
<summary>What <code>strace</code> does? What about <code>ltrace</code>?</summary><br><b>
</b></details>

<details>
<summary>Find all the files which end with '.yml' and replace the number 1 in 2 in each file</summary><br><b>

find /some_dir -iname \*.yml -print0 | xargs -0 -r sed -i "s/1/2/g"
</b></details>

<details>
<summary>How to check how much free memory a system has? How to check memory consumption by each process?</summary><br><b>

You can use the commands <code>top</code> and <code>free</code>
</b></details>

<details>
<summary>You run ls and you get "/lib/ld-linux-armhf.so.3 no such file or directory". What is the problem?</summary><br><b>

The ls executable is built for an incompatible architecture.
</b></details>

<details>
<summary>How would you split a 50 lines file into 2 files of 25 lines each?</summary><br><b>

You can use the <code>split</code> command this way: <code>split -l 25 some_file</code>
</b></details>

<details>
<summary>What is a file descriptor? What file descriptors are you familiar with?</summary><br><b>
Kerberos
File descriptor, also known as file handler, is a unique number which identifies an open file in the operating system.

In Linux (and Unix) the first three file descriptors are:
  * 0 - the default data stream for input
  * 1 - the default data stream for output
  * 2 - the default data stream for output related to errors

This is a great article on the topic: https://www.computerhope.com/jargon/f/file-descriptor.htm
</b></details>

<details>
<summary>What is NTP? What is it used for?</summary><br><b>
</b></details>

<details>
<summary>Explain Kernel OOM</summary><br><b>
</b></details>

##### Linux Security

<details>
<summary>What is chroot? In what scenarios would you consider using it?</summary><br><b>
</b></details>

<details>
<summary>What is SELiunx?</summary><br><b>
</b></details>

<details>
<summary>What is Kerberos?</summary><br><b>
</b></details>

<details>
<summary>What is nftables?</summary><br><b>
</b></details>

<details>
<summary>What firewalld daemon is responsible for?</summary><br><b>
</b></details>

<details>
<summary>Do you have experience with hardening servers? Can you describe the process?</summary><br><b>
</b></details>

##### Linux - Networking

<details>
<summary>How to list all interfaces?</summary><br><b>
</b></details>

<details>
<summary>How to disable an interface?</summary><br><b>
</b></details>

<details>
<summary>What is a network namespace? What is it used for?</summary><br><b>
</b></details>

<details>
<summary>How to check if a certain port is being used?</summary><br><b>

One of the following would work:

```
netstat -tnlp | grep <port_number>
lsof -i -n -P | grep <port_number>
```
</b></details>

<details>
<summary>How can you turn your Linux server into a router?</summary><br><b>
</b></details>

<details>
<summary>What is a virtual IP? In what situation would you use it?</summary><br><b>
</b></details>

<details>
<summary>True or False? The MAC address of an interface is assigned/set by the OS</summary><br><b>

False
</b></details>

<details>
<summary>Can you have more than one default gateway in a given system?</summary><br><b>

Technically, yes.
</b></details>

<details>
<summary>Which port is used in each of the following protocols?:

  * SSH
  * SMTP
  * HTTP
  * DNS
  * HTTPS</summary><br><b>

  * SSH - 22
  * SMTP - 35
  * HTTP - 80
  * DNS - 53
  * HTTPS - 443
</b></details>

<details>
<summary>What is telnet and why is it a bad idea to use it in production? (or at all)</summary><br><b>
</b></details>

<details>
<summary>What is the routing table? How do you view it?</summary><br><b>
</b></details>

<details>
<summary>How can you send an HTTP request from your shell?</summary><br><b>
<br>
Using nc is one way<br>
</b></details>

<details>
<summary>What are packet sniffers? Have you used one in the past? If yes, which packet sniffers have you used and for what purpose?</summary><br><b>
</b></details>

<details>
<summary>How to list active connections?</summary><br><b>
</b></details>

<details>
<summary>How to trigger neighbor discovery in IPv6?</summary><br><b>

One way would be `ping6 ff02::1`
</b></details>

##### Linux DNS

<details>
<summary>What the file <code>/etc/resolv.conf</code> is used for? What does it include?</summary><br><b>
</b></details>

<details>
<summary>What commands are you using for performing DNS queries (or troubleshoot DNS related issues)?</summary><br><b>

You can specify one or more of the following:

 * <code>dig</code>
 * <code>host</code>
 * <code>nslookup</code>
</b></details>

##### Packaging

<details>
<summary>Do you have experience with packaging? (as in building packages) Can you explain how does it works?</summary><br><b>
</b></details>

<details>
<summary>RPM: explain the spec format(what it should and can include)</summary><br><b>
</b></details>

<details>
<summary>How do you list the content of a package without actually installing it?</summary><br><b>
</b></details>

<details>
<summary>How to know to which package a file on the system belongs to? Is it a problem if it doesn't belongs to any package?</summary><br><b>
</b></details>

<details>
<summary>Where repositories are stored? (based on the distribution you are using)</summary><br><b>
</b></details>

<details>
<summary>What is an archive? How do you create one in Linux?</summary><br><b>
</b></details>

<details>
<summary>How to extract the content of an archive?</summary><br><b>
</b></details>

<details>
<summary>Why do we need package managers? Why not simply creating archives and publish them?</summary><br><b>

Package managers allow you to manage packages lifecycle as in installing, removing and update the packages.<br>
In addition, you can specify in a spec how a certain package will be installed - where to copy the files, which commands to run prior to the installation, post the installation, etc.
</b></details>

##### Applications and Services

<details>
<summary>What can you find in /etc/services?</summary><br><b>
</b></details>

<details>
<summary>How to make sure a Service starts automatically after a reboot or crash?</summary><br><b>

Depends on the init system.

Systemd: <code> systemctl enable [service_name] </code>
System V: <code> update-rc.d [service_name] </code> and add this line <code> id:5678:respawn:/bin/sh /path/to/app </code> to /etc/inittab
Upstart: add Upstart init script at /etc/init/service.conf
</b></details>

<details>
<summary>You run <code>ssh 127.0.0.1</code> but it fails with "connection refused". What could be the problem?</summary><br><b>

1. SSH server is not installed
2. SSH server is not running
</b></details>

<details>
<summary>How to print the shared libraries required by a certain program? What is it useful for?</summary><br><b>
</b></details>

<details>
<summary>What is CUPS?</summary><br><b>
</b></details>

<details>
<summary>What types of web servers are you familiar with?</summary><br><b>

Nginx, Apache httpd.
</b></details>

##### Users

<details>
<summary>How do you create users? Where user information is stored?</summary><br><b>
</b></details>

<details>
<summary>Which file stores information about groups?</summary><br><b>
</b></details>

<details>
<summary>How do you change/set the password of a user?</summary><br><b>
</b></details>

<details>
<summary>Which file stores users passwords? Is it visible for everyone?</summary><br><b>
</b></details>

<details>
<summary>Do you know how to create a new user without using adduser/useradd command?</summary><br><b>
</b></details>

<details>
<summary>What information is stored in /etc/passwd? explain each field</summary><br><b>
</b></details>

<details>
<summary>How to add a new user to the system without providing him the ability to log-in into the system?</summary><br><b>

`adduser user_name --shell=/bin/false --no-create-home`
You can also add a user and then edit /etc/passwd.
</b></details>

<details>
<summary>How to switch to another user? How to switch to root?</summary><br><b>

su command.
Use su - to switch to root
</b></details>

<details>
<summary>What is the UID the root user? What about a regular user?</summary><br><b>
</b></details>

<details>
<summary>What can you do if you lost/forogt the root password?</summary><br><b>

Re-install the OS IS NOT the right answer :)
</b></details>

<details>
<summary>What is sudo? How do you set it up?</summary><br><b>
</b></details>

<details>
<summary>What is /etc/skel?</summary><br><b>
</b></details>

<details>
<summary>How to see a list of who logged-in to the system?</summary><br><b>

Using the last command.
</b></details>

#### Linux - Hardware

<details>
<summary>Where can you find information on the processor?</summary><br><b>

/proc/cpuinfo
</b></details>

<details>
<summary>How can you print information on the BIOS, motherboard, processor and RAM?</summary><br><b>

dmidecoode
</b></details>

<details>
<summary>How can you print all the information on connected block devices in your system?</summary><br><b>

lsblk
</b></details>

#### Linux - Random

<details>
<summary>Give 5 commands which are two letters long</summary><br><b>

ls, wc, dd, df, du, ps, ip, cp, cd ...
</b></details>

<details>
<summary>What ways are there for creating a new empty file?</summary><br><b>

  * touch new_file
  * echo "" > new_file
</b></details>

<details>
<summary>How `cd -` works? How does it knows the previous location?</summary><br><b>

$OLDPWD
</b></details>

<details>
<summary>List three ways to print all the files in the current directory</summary><br><b>

* ls
* find .
* echo *
</b></details>

<details>
<summary>What is '|'? What is it used for?</summary><br><b>
</b></details>

<details>
<summary>How to count the number of lines in a file? What about words?</summary><br><b>
</b></details>

<details>
<summary>You define x=2 in /etc/bashrc and x=6 ~/.bashrc you then login to the system. What would be the value of x?</summary><br><b>
</b></details>

<details>
<summary>What is the difference between man and info?</summary><br><b>

A good answer can be found [here](https://askubuntu.com/questions/9325/what-is-the-difference-between-man-and-info-documentation)
</b></details>

<details>
<summary>Explain "environment variables". How do you list all environment variables?</summary><br><b>
</b></details>

<details>
<summary>How to create your own environment variables?</summary><br><b>

`X=2` for example. But this will persist to new shells. To have it in new shells as well, use `export X=2`
</b></details>

<details>
<summary>What a double dash (--) mean?</summary><br><b>

It's used in commands to mark the end of commands options. One common example is when used with git to discard local changes: `git checkout -- some_file`
</b></details>

#### Commands

<details>
<summary>What the <code>lsof</code> command does? Have you used it? What for?</summary><br><b>
</b></details>

<details>
<summary>What the <code>awk</code> command does? Have you used it? What for?</summary><br><b>
</b></details>

<details>
<summary>What commands you can use for searching files and/or directories?</summary><br><b>

  * find
  * locate
</b></details>

<details>
<summary>How can you check what is the path of a certain command?</summary><br><b>

  * whereis
  * which
</b></details>

<a name="linux-advanced"></a>
#### :star: Advanced

#### System Calls

<details>
<summary>Explain the fork() system call</summary><br><b>

fork() is used for creating a new process. It does so by cloning the calling process but the child process has its own PID and any memory locks, I/O operations and semaphores are not inherited.
</b></details>

<details>
<summary>Explain the exec() system call</summary><br><b>
</b></details>

<details>
<summary>What system call is used for listing files?</summary><br><b>
</b></details>

<details>
<summary>What system call is used for creating a new process?</summary><br><b>
</b></details>

<details>
<summary>What are the differences between exec() and fork()?</summary><br><b>
</b></details>

<details>
<summary>Why do we need the wait system call?</summary><br><b>

wait() is used by a parent process to wait for the child process to finish execution.
If wait is not used by a parent process then a child process might become a zombie process.
</b></details>

<details>
<summary>What execve() does?</summary><br><b>

Executes a program. The program is passed as a filename (or path) and must be a binary executable or a script.
</b></details>

<details>
<summary>What is the return value of malloc?</summary><br><b>
</b></details>

<details>
<summary>Explain the pipe() system call. What does it used for?</summary><br><b>

[Unix pipe implementation](https://toroid.org/unix-pipe-implementation)

"Pipes provide a unidirectional interprocess communication channel. A pipe has a read end and a write end. Data written to the write end of a pipe can be read from the read end of the pipe.
A pipe is created using pipe(2), which returns two file descriptors, one referring to the read end of the pipe, the other referring to the write end."
</b></details>

<details>
<summary>What happens when you execute <code>ls -l</code>?</summary><br><b>

* Shell reads the input using getline() which reads the input file stream and stores into a buffer as a string
* The buffer is broken down into tokens and stored in an array this way: {"ls", "-l", "NULL"}
* Shell checks if an expansion is required (in case of ls *.c)

* Once the program in memory, its execution starts. First by calling readdir()

Notes:

* getline() originates in GNU C library and used to read lines from input stream and stores those lines in the buffer
</b></details>

<details>
<summary>What happens when you execute <code>ls -l *.log</code>?</summary><br><b>
</b></details>

<details>
<summary>What readdir() system call does?</summary><br><b>


</b></details>

#### Linux Filesystem & Files

<details>
<summary>How to create a file of a certain size?</summary><br><b>

There are a couple of ways to do that:
  
  * dd if=/dev/urandom of=new_file.txt bs=2MB count=1
  * truncate -s 2M new_file.txt
  * fallocate -l 2097152 new_file.txt
</b></details>

<details>
<summary>Can you describe how processes are being created?</summary><br><b>
</b></details>

<details>
<summary>What does the following block do?:

```
open("/my/file") = 5
read(5, "file content")
```
</summary><br><b>

These system calls are reading the file <code>/my/file</code> and 5 is the file descriptor number.
</b></details>

<details>
<summary>Describe three different ways to remove a file (or its content)</summary><br><b>
</b></details>

<details>
<summary>What is the difference between a process and a thread?</summary><br><b>
</b></details>

<details>
<summary>You found there is a server with high CPU load but you didn't find a process with high CPU. How is that possible?</summary><br><b>
</b></details>

##### Linux Advanced - Networking

<details>
<summary>When you run <code>ip a</code> you see there is a device called 'lo'. What is it and why do we need it?</summary><br><b>
</b></details>

<details>
<summary>What the <code>traceroute</code> command does? How does it works?</summary><br><b>

Another common way to task this questions is "what part of the tcp header does traceroute modify?"
</b></details>

<details>
<summary>What is network bonding? What types are you familiar with?</summary><br><b>
</b></details>

<details>
<summary>How to link two separate network namespaces so you can ping an interface on one namespace from the second one?</summary><br><b>
</b></details>

<details>
<summary>What are cgroups?</summary><br><b>
</b></details>

<details>
<summary>Explain Process Descriptor and Task Structure</summary><br><b>
</b></details>

<details>
<summary>What are the differences between threads and processes?</summary><br><b>
</b></details>

<details>
<summary>Explain Kernel Threads</summary><br><b>
</b></details>

<details>
<summary>What happens when socket system call is used?</summary><br><b>

This is a good article about the topic: https://ops.tips/blog/how-linux-creates-sockets
</b></details>

<details>
<summary>You executed a script and while still running, it got accidentally removed. Is it possible to restore the script while it's still running?</summary><br><b>
</b></details>

#### Memory

<details>
<summary>What is the difference between MemFree and MemAvailable in /proc/meminfo?</summary><br><b>

MemFree - The amount of unused physical RAM in your system
MemAvailable - The amount of available memory for new workloads (without pushing system to use swap) based on MemFree, Active(file), Inactive(file), and SReclaimable.
</b></details>

#### Distribution

<details>
<summary>What is a Linux distribution?</summary><br><b>
</b></details>

<details>
<summary>What Linux distributions are you familiar with? List at least four?</summary><br><b>
</b></details>

<details>
<summary>What are the components of a Linux distribution?</summary><br><b>

* Kernel
* Utilities
* Services
* Software/Packages Management
</b></details>

#### Linux Advanced - Misc

<details>
<summary>Wildcards are implemented on user or kernel space?</summary><br><b>
</b></details>

<details>
<summary>Why there are different sections in man? What is the difference between the sections?</summary><br><b>
</b></details>

## Operating System

<details>
<summary>What is an operating system?</summary><br><b>

There are many ways to answer that. For those who look for simplicity, the book "Operating Systems: Three Easy Pieces" offers nice version:

"responsible for making it easy to run programs (even allowing you to seemingly run many at the same time), allowing programs to share memory, enabling programs to interact with devices, and other fun stuff like that"
</b></details>

<details>
<summary>What is POSIX?</summary><br><b>
</b></details>

#### Processes

<details>
<summary>Can you explain what is a process?</summary><br><b>

A process is a running program. A program is one or more instructions and the program (or process) is executed by the operating system.
</b></details>

<details>
<summary>If you had to design an API for processes in an operating system, what would this API look like?</summary><br><b>

It would support the following:

* Create - allow to create new processes 
* Delete - allow to remove/destroy processes
* State - allow to check the state of the process, whether it's running, stopped, waiting, etc.
* Stop - allow to stop a running process
</b></details>

<details>
<summary>How a process is created?</summary><br><b>

* The OS is reading program's code and any additional relevant data
* Program's bytes are loaded into the memory or more specifically, into the address space of the process.
* Memory is allocated for program's stack (aka run-time stack). The stack also initialized by the OS with data like argv, argc and parameters to main()
* Memory is allocated for program's heap which is required for data structures like linked lists and hash tables
* I/O initialization tasks like in Unix/Linux based systems where each process has 3 file descriptors (input, output and error)
* OS is running the program, strarting from main()

Note: The loading of the program's code into the memory done lazily which means the OS loads only partial relevant pieces required for the process to run and not the entire code.
</b></details>

<details>
<summary>True or False? The loading of the program into the memory is done eagerly (all at once)</summary><br><b>

False. It was true in the past but today's operating systems perform lazy loading which means only the relevant pieces required for the process to run are loaded first.
</b></details>

<details>
<summary>What are different states of a process?</summary><br><b>

* Running - it's executing instructions
* Ready - it's ready to run but for different reasons it's on hold
* Blocked - it's waiting for some operation to complete. For example I/O disk request
</b></details>

<details>
<summary>What is Inter Process Communication (IPC)?</summary><br><b>
</b></details>

#### Concurrency

<details>
<summary>Explain what is Semaphore and what its role in operating systems</summary><br><b>
</b></details>

#### Memory

<details>
<summary>What is cache? What is buffer?</summary><br><b>

Buffer: Reserved place in RAM which is used to hold data for temporary purposes
Cache: Cache is usually used when processes reading and writing to the disk to make the process faster by making similar data used by different programs easily accessible.
</b></details>

## Network

<a name="virtualization-beginner"></a>
#### :baby: Beginner


<details>
<summary>How to create a NIC Channel Bonding in Linux</summary><br><b>
1. As root, create a Bond0 Configuration File: # vi /etc/sysconfig/network-scripts/ifcfg-bond0
2. Add the following lines to the Bond0 Configuration File:

DEVICE=bond0
IPADDR=192.168.1.10
NETWORK=192.168.1.0
NETMASK=255.255.255.0
USERCTL=no
BOOTPROTO=none
ONBOOT=yes
BONDING_OPTS="mode=0 miimon=100"

3. Open the configuration file for eth0:

<code> # vi /etc/sysconfig/network-scripts/ifcfg-eth0 </code>
4. Edit eth0 configuration file adding the "MASTER" and "SLAVE" parameters:

DEVICE=eth0
USERCTL=no
ONBOOT=yes
MASTER=bond0
SLAVE=yes
BOOTPROTO=none

Repeat steps #3 and #4 for eth1.
5. Open the kernel modules configuration file
RHEL5 # vi /etc/modprobe.conf
RHEL6 # vi /etc/modprobe.d/modprobe.conf

6. Add the following line to modprobe.conf file:

alias bond0 bonding
options bond0 mode=balance-rr miimon=100


7. Load the bonding Module:

<code># modprobe bonding </code>

Restart Network service:

<code># service network restart</code>

Check if the bonding interface was created successfully looking at the output of the ifconfig command:

<code># ifconfig</code>
</b></details>
