# Set Up Server With Ubuntu 20.04

## SSH as Root
Login to your public IP server as a root admin. In other Linux distros the root user may be named differently. <br> 
<code>ssh root@xxxx.xxxx.xxxx.xxxx</code> <br>
## Create a new user with <br> 
<code>adduser newuser</code> <br>
Add sudo privileges to the user with <br>
<code>usermod -aG sudo newuser </code> <br> 
## Uncomplicated Firewall 
Check applications being managed by UFW <br> 
<code>ufw app list</code> <br> 
OpenSSH should be available. Make sure it is allowed <br> 
<code>allow OpenSSH</code>
Then enable the firewall <br> 
<code>ufw enable</code>
Now check the firewall status <br> 
<code>ufw status</code> <br>
OpenSSH for v4 and v6 should be allowed from anywhere. <br>
## Move your SSH key
If you use SSH keys to login rather than a passphrase, then you will need to copy it from the root user's directory into the newuser's one, change the permissions with <code>cmod</code> to read and execute or 755, and change the ownership of files with <code>chown</code> <br>
However, <code>rsync</code> can do this is one command <br>
<code>rsync --archive --chown=newuser:newuser ~/.ssh /home/newuser </code> 