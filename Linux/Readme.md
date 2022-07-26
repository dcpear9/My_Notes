# Notes

## Linux

 | key word    | Description |
| ----------- | ----------- |
|File System|[<img src="LinuxFileSystem.png" width="250"/>](LinuxFileSystem.png)|
|command Line|Use through shell software. General pattern: command option(s) arguments(s)|
Find commands     |apropos copy      |
| Find more about a command   |  man cp (every Linux has man pages installed)        |
|keyboard shotcuts|Ctrl-A &nbsp; &nbsp;(move to the begining of the line </br> Ctrl-E &nbsp; &nbsp; (Move to the end of the line </br> Ctrl-T &nbsp; &nbsp;(Transpose characters on either side of the cursor (alb->bla) </br> Ctrl-C &nbsp; &nbsp;(Exist a running process </br> Ctrl-Z &nbsp; &nbsp;(Suspend a task (use jobs to see tasks, and fg or bg to manipulate them) </br> Ctrl-D &nbsp; &nbsp;(End of file/end of input) </br> Ctrl-Shift-C &nbsp; &nbsp;(Copy selected text in a terminal) </br> Ctrl-Shift-X &nbsp; &nbsp;(Cut selected text in a terminal) </br> Ctrl-Shift-V &nbsp; &nbsp;(Paste text in a terminal)|
|Root|On every Linux system, there's a superuser account called Root. </br> Root is used to perform administrative tasks (installing software, changing config) </br>Root has the user id of Zero , the only user created during default installation </br> Root has unquestioned access to the system <br> Using root directly is not recommended </br> You can delagate access to its privileges to pther users with <b>sudo</b> (su-do), su and do|
|sudo| the list of users who are allowed to use super user previledges managed in the </br> /etc/sudoers file/ </br> sudo cat /etc/sudoers </br> update with 'visudo' command </br> <b><u>Useful Options for sudo</u></b> </br> sudo -i &nbsp; &nbsp;(Run the target user's shell and switch into their home directory) </br> sudos -s &nbsp; &nbsp;(Run with the invoking user's shell) <br> sudo -l &nbsp; &nbsp;(Show what sudo privileges the user has) </br> sudo -u &nbsp; &nbsp;(Specifiy a user to operate as) </br> <b><u>While Using sudo</u></b> </br> <li> Logs are kept of commands that are run with <b> sudo </b> </br> <li> Each time <b>sudo</b> is used, a five-minute timer is reset <li>Expire the timer with <b>sudo -k</b>|
|Exploring a System| <li> what distro ? </br> <sub>[MOH\deeperera@a-2d0njwwmj50bv ~]$ cat /etc/*release </br>NAME="Amazon Linux" <br>VERSION="2" <br>ID="amzn" <br>ID_LIKE="centos rhel fedora" <br>VERSION_ID="2" <br>PRETTY_NAME="Amazon Linux 2" <br>ANSI_COLOR="0;33" <br>CPE_NAME="cpe:2.3:o:amazon:amazon_linux:2" <br>HOME_URL="https://amazonlinux.com/" <br>Amazon Linux release 2 (Karoo)</sub> </br> <li> hostnamectl </br><sub> hostnamectl command provides a proper API used to control Linux system hostname and change its related settings. The command also helps to change the hostname without actually locating and editing the /etc/hostname file on a given system </sub> </br> <li> Display general information</br>uname -a <br><sub> Displays the operating system name, system node name, operating system release, operating system version, hardware name, and processor type. </sub></br> <li> Uptime </br> <sub>Tell how long the Linux system has been running. w command – Show who is logged on and what they are doing including the uptime of a Linux box </sub> </br> <li> df -h </br><sub> how much space available and free on the disks connected to th system. (-h fro human readable numbers) </sub> </br> <li> free </br><sub>How much free memory</sub> </br> <li> who </br> <sub> Linux is a multi user system. type 'who' to list the users</sub>  </br><code> MOH\deeperera :100         2022-07-24 17:10 (:100) </br>MOH\deeperera pts/0        2022-07-24 17:11 (:100) </br> pts is for users login via ssh</code> <li> systemctl </br> What services are available</sub> <li> &nbsp; &nbsp; systemctl list-unit-files <li>&nbsp; &nbsp; systemctl list-unit-files \|grep enabled </br> <li> systemctl \|grep 'running' <li> systemctl status pcoip (particular system name)</br> <sub>further reading man systemctl, systemmd  <br> <li>ip a  or ifconfig <br><sub>network configuration</sub>| 
|Bourne Again Shell (Bash)|<li> popular and default for many system.<li> available on Mac and Windows subsysytem for linux|
|Scripting basics| commands </br>echo "it is " date "today" <br>it is  date today </br>  echo "it is " $(date) "today" <br>it is  Sun Jul 24 20:44:40 NZST 2022 today </br>  history and then !\<number\>|
|Adding 3rd party repositories with APT||
|Freindly interactive Shell - Fish| <li>type fish to open|
|||
```
[MOH\deeperera@a-2d0njwwmj50bv ~]$ yum info nano
Loaded plugins: amzn_workspaces_filter_updates, halt_os_update_check, priorities, update-motd
Available Packages
Name        : nano
Arch        : x86_64
Version     : 2.9.8
Release     : 2.amzn2.0.1
Size        : 571 k
Repo        : amzn2-core/2/x86_64
Summary     : A small text editor
URL         : https://www.nano-editor.org
License     : GPLv3+
Description : GNU nano is a small and friendly text editor
```
yum list
yum list available
This worked for me on release:

cat /etc/os-release
NAME="Amazon Linux AMI"
VERSION="2018.03"
ID="amzn"
ID_LIKE="rhel fedora"
VERSION_ID="2018.03"
PRETTY_NAME="Amazon Linux AMI 2018.03"
ANSI_COLOR="0;33"
CPE_NAME="cpe:/o:amazon:linux:2018.03:ga"
HOME_URL="http://aws.amazon.com/amazon-linux-ami/"
add repo

sudo yum-config-manager --add-repo http://fishshell.com/files/linux/RedHat_RHEL-6/fish.release:2.repo
clean

sudo yum clean all
install

sudo yum -y install fish
test

    [ec2-user@ip-xxx-xx-x-xx] yum.repos.d]$ fish
Welcome to fish, the friendly interactive shell

