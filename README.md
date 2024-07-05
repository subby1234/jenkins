# jenkins
https://www.jenkins.io/doc/tutorials/tutorial-for-installing-jenkins-on-AWS/

sudo yum update –y

sudo dnf install java-11-amazon-corretto -y


java --version
--------------------------------------

sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo

sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key

sudo yum upgrade
.......................................

sudo yum install jenkins -y

sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins

...................................

Default port: 8080: SG

ip:8080
sudo cat /var/lib/jenkins....... for password
........................................................

.........................................................

........................................................
MASTER / SLAVE ARCHITECTURE

MASTER: JENKINS INSTALL IS REQUIRED 


........................

sudo su .......... change to root user
cat /etc/passwd
jenkins:x:992:992:Jenkins Automation Server:/var/lib/jenkins:/bin/false


chsh -s /bin/bash jenkins
-bash: chsh: command not found

sudo yum install util-linux-user

sudo chsh -s /bin/bash jenkins

jenkins:x:992:992:Jenkins Automation Server:/var/lib/jenkins:/bin/bash
..................................
.
su - jenkins......... login as jenkins
[jenkins@ip-172-31-43-188 ~]$

Now generate public and private key

ssh-keygen
cd .ssh

copy public key to slave machine........
ssh-copy-id jenkins@public ip (slave)

test if you can take remote access of the slave machine
ssh jenkins@ip ...will be denied......( unless you are done with slave set up: restarted sshd ).............


.....................


SLAVE

slave: Only java install is required 
........................

sudo useradd jenkins
sudo passwd jenkins

su - jenkins
.......................................


ADD SUDO PRIVILEDGES TO JENKINS

exit ........logout from jenkins

Either use:sudo visudo 

Or :


cd /etc/
sudo vi sudoer
.......................................

stroll down to: where you will see
# %wheel        ALL=(ALL)       NOPASSWD: ALL        : add 
jenkins         ALL=(ALL)       NOPASSWD: ALL
...................................................

still using jenkins user:

cd /etc/
cd ssh
ls -al
.
.
.
sudo vi ssh_config

search for: PasswordAuthentication no
change NO to YES
AND RESTART SSHD:
sudo systemctl restart sshd




























































































































































































