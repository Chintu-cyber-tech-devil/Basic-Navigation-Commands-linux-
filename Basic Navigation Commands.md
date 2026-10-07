1) print curent directory (Whoami) /  (home/kali) 

└─$  pwd       

2) List file and Folder 

└─$  ls      (simple list ) 

└─$  ls-la   (detailed list with hiden list ) 

└─$  ls-lh   (human-readble file size ) 


3) Change directory

└─$  mkdir myproject     ( create  a folder ) 
└─$  mkdir -p a/b/c      (Create nested folder) 
└─$  rmdir  myproject     (remove empty folder ) 

Create files 
└─$ touch myfile.txt          ( Create emty file ) 
└─$  echo "Hello" > file.txt   (create file with txt ) 
└─$   nano myfile.txt           ( open file in nano editor ) 

View file contents 
└─$  cat file.txt          ( Show entire file ) 
└─$  head -5 file.txt      ( show first  5 terms ) 
└─$  tails -5 file.txt     ( show last 5 lines ) 
└─$  less file.txt         ( Scroll through fill (press q to quiet ) 
7) Copy, Move, Rename, Delete

└─$ cp file.txt backup.txt             => copy file
└─$ cp -r folder1 folder2              => copy folder recursively
└─$ mv file.txt newname.txt            => rename file
└─$ mv file.txt /home/kali/Desktop/    => move file
└─$ rm file.txt                        => delete file
└─$ rm -rf folder                      => delete folder (careful)


              User & Password Commands

8) Who am I?

└─$ whoami                             => shows current username


9) Kali:

└─$ id                                 => shows user ID, group ID,
                                         and groups


10) Switch users

└─$ su root                            => switch to root user (root pass)
└─$ su - john                          => switch to user "john"
└─$ sudo su                            => become root using sudo
└─$ exit                               => go back to previous user


11) Run commands as root

└─$ sudo apt update                    => run single command as root
└─$ sudo -i                            => run single command as root


12) Change password

└─$ passwd                             => change your password
└─$ sudo passwd john                   => change another user's password
                                      => change your password

13) Add / Delete users

└─$ sudo adduser john                  => create new user john
└─$ sudo deluser john                  => delete user "john"
└─$ sudo usermod -aG sudo john         => give john sudo access


                System Information Commands

14) System info

└─$ uname -a                           => full system info (kernel, architecture)
└─$ hostname                           => show computer name
└─$ uptime                             => how long system has been running
└─$ date                               => current date and time


15) Disk & Memory

└─$ df -h                              => disk space usage (human readable)
└─$ free -h                            => RAM usage
└─$ du -sh folder/                     => folder size


16) Process management

└─$ top                                => live process monitor (press q to quit)
└─$ htop                               => better process monitor (colorful)
└─$ ps aux                             => list all running processes
└─$ kill 1234                          => kill process by PID
└─$ killall firefox                    => kill process by name



                          File Permissions

                                                => 7=rwx | 6=rw | 5=rx | 4=r

17) View permissions

└─$ ls -la

-rwxr-xr-- 1 kali kali 606 Apr 10 09:01.sh

r = read (4), w = write (2), x = execute (1)

+ owner | group | other


18) Change permissions

└─$ chmod 755 script.sh               => rwx for owner, rx for group/other
└─$ chmod +x script.sh                => add execute permission for everyone
└─$ chmod 644 file.txt                => rw for owner, read-only for others


19) Change ownership

└─$ sudo chown root file.txt          => change owner to root
└─$ sudo chown kali:kali file.txt    => change owner and group
└─$ sudo chown -R kali folder/        => change ownership recursively


                         Network Commands

20) Check your IP address

└─$ ip a                               => show all network interfaces & IP
└─$ ifconfig                           => same (older command)
└─$ hostname -I                        => quick - just show your IP


21) Test connectivity

└─$ ping google.com                    => check if you can reach a host
└─$ ping -c 4 google.com               => send only 4 pings


22) Network Connections

└─$ ss -tulng                          => show open ports & listening services
└─$ netstat -tulng                     => same (older command)


23) DNS lookup

└─$ nslookup google.com                => find IP of a domain
└─$ dig google.com                     => get detailed DNS info


24) Download files

└─$ wget https://example.com/file.zip  => download a file
└─$ curl https://example.com           => fetch web content

                         Package Management & Updates

25) Update & Upgrade Kali (do this regularly!)

└─$ sudo apt update                    => refresh package lists
└─$ sudo apt upgrade -y               => upgrade all installed packages
└─$ sudo apt full-upgrade -y           => full system upgrade


26) Install & Remove packages

└─$ sudo apt install nmap              => install a package
└─$ sudo apt remove nmap               => remove a package
└─$ sudo apt purge nmap                => remove + delete config files
└─$ sudo apt autoremove                => remove unused dependencies


27) Search for packages

└─$ apt search wireshark               => find a package
└─$ apt show nmap                      => show package details
└─$ dpkg -l | grep nmap                => check if package is installed


                         Search & Find Commands

28) Find files

└─$ find / -name "password.txt"        => search entire system
└─$ find /home -name "*.txt"           => find all .txt files in /home
└─$ find . -type f -size +10M           => find files larger than 10M
└─$ locate passwords.txt                => fast search (uses database)


29) Search inside files

└─$ grep "password" file.txt           => search for text in a file
└─$ grep -r "admin" /var/log/          => search recursively in folder
└─$ grep -i "error" log.txt            => case-insensitive search
└─$ grep -n "root" /etc/passwd         => show line numbers


30) Command history

└─$ history                            => show all previous commands
└─$ history | grep nmap                => find specific commands in history
└─$ !42                               => re-run command #42 from history


                         Using Tools - Quick

1) Nmap - Scan a target

└─$ nmap 192.168.1.1                   => basic port scan
└─$ nmap -sV 192.168.1.1              => detect service version
└─$ nmap -A 192.168.1.0/24            => aggressive scan entire network


2) Hydra - Brute force SSH login

└─$ hydra -l admin -P wordlist.txt ssh://192.168.1.1


3) Nikto - Web Server Scanner

└─$ nikto -h http://target.com


4) Gobuster - Directory brute force

└─$ gobuster dir -u http://target.com -w /usr/share/wordlists/dirb/common.txt


5) SQLMap - Test for SQL Injection

└─$ sqlmap -v "http://target.com/page?id=1" --dbs




                 Important Files & Wordlists

1) Important system files

└─$ cat /etc/passwd                    => list of all users on the system
└─$ cat /etc/shadow                    => password hashes (need root)
└─$ cat /etc/hosts                     => local DNS mappings
└─$ cat /etc/resolv.conf               => DNS server settings


2) Pre-installed Wordlists (for password cracking)

└─$ ls /usr/share/wordlists/           => rockyou.txt.gz, dirb/dirbuster/
                                         wfuzz/ | fasttrack.txt


3) Unzip rockyou (most famous wordlist - 14 million passwords!)

└─$ sudo gzip -d /usr/share/wordlists/rockyou.txt.gz


4) Kali tools location

└─$ ls /usr/share/                     => most tools store data here
└─$ which nmap                         => find where a tool is installed
