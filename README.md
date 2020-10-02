# kali-storage-clean

![Screenshot](kali.jpg)

## fixing the storage problem 

Freeing Disk Space in Kali Linux (Basic steps), Especially the apt-get Cache
Kali is a Debian-based Linux developed with penetration-testers in mind. Think of it as a toolbox.
It is basically a Debian Linux, but with all the penetration testing tools installed, for free.
This includes Metasploit, OpenVAS vulnerability scanners, exploitDB, Hydra, aircrack-ng, John the Ripper, etc.
These come on top Linux's common formidable tools such as OpenSSH (for creating tunnels), netcat, and nmap to name a few.


### here is steps:

* Step 1: Check Disk space and where you are consuming space the most. Use df -h. the '-h' option in df is to format the result in 'human-readable' format. 
        (# df -h).
	
        it seems the entire disk (virtual disk) is full. But we still need to know what folders are the largest, etc. 

* Step 2: Use 'du' to show the top 10-30 consumers of space. 
        You can use this iteratively  going from one folder then digging deeper into its subfolders until you are satisfied that you have pinpointed 
        what folders you need to remove/purge in order to free space. 
        
	The syntax is: 

        du <directory> -ka | sort -n -r | head -n<number to show>

* Step 3: Proceed to delete the files. You can use rm -rf <file_name> to remove the files. you can even use wildcards such as * and ?.For example, you can delete rm -rf      
  /home/archives/* to delete everything in /home/archives.  

        However, since we are dealing with the apt-get archives/cache, there is a safer way of dealing with it instead of doing a rm -rf. Use apt-get clean, or apt-get autoclean. Here's the difference: 
    =>apt-get clean removes all packages downloaded (even those not yet installed) except those locked packages  in /var/apt/cache/archives and /var/apt/cache/archives/partial. 
    =>apt-get autoclean is a little smarter. It removes old packages and archives which are unlikely to be used. For example, outdated packages where a new package is already downloaded. Although, autoclean removes less archives in the apt-get cache, then clean. 
 

* Step 4: Verify the process and if necessary repeat steps 1-3. As shown in the picture above, verify by doing df -h again (step 1), 
        and doing another iterative set of du (step 2). Do steps 1-3 repeatedly until you are satisfied you have purged all the unwanted files. 
   



#### it works for me !

thankyou!
