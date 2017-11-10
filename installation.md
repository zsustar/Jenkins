- ![#f03c15](https://placehold.it/15/f03c15/000000?text=+) `#f03c15`
- ![#c5f015](https://placehold.it/15/c5f015/000000?text=+) `#c5f015`
- ![#1589F0](https://placehold.it/15/1589F0/000000?text=+) `#1589F0`

- ![#f03c15](https://placehold.it/15/f03c15/000000?text=+) #Install on Ubuntu
#https://wiki.jenkins.io/display/JENKINS/Installing+Jenkins+on+Ubuntu
`sudo apt-get install openjdk-8-jdk
wget -q -O - https://pkg.jenkins.io/debian/jenkins-ci.org.key | sudo apt-key add -
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt-get update
sudo apt-get install --no-install-recommends -y jenkins
sudo apt-get clean`

#update Jenkins
sudo apt install aptitude
sudo aptitude update
sudo aptitude install jenkins

- ![#f03c15](https://placehold.it/15/f03c15/000000?text=+) #Install on RedHat/CentOS
 #https://www.vultr.com/docs/how-to-install-jenkins-on-centos-7
sudo yum install -y java-1.8.0-openjdk.x86_64
sudo yum install -y  wget
echo 'export JAVA_HOME=/usr/lib/jvm/jre-1.8.0-openjdk' | sudo tee -a /etc/profile
echo 'export JRE_HOME=/usr/lib/jvm/jre' | sudo tee -a /etc/profile
source /etc/profile
java -version
echo $JAVA_HOME
echo $JRE_HOME

#Install Jenkins
cd ~
sudo wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat-stable/jenkins.repo
sudo rpm --import http://pkg.jenkins-ci.org/redhat-stable/jenkins-ci.org.key
sudo yum install jenkins

#Start the Jenkins service and set it to run at boot time:
sudo systemctl start jenkins.service
sudo systemctl enable jenkins.service

#Optional: In order to allow visitors access to Jenkins, you need to allow inbound traffic on port 8080:
sudo firewall-cmd --zone=public --permanent --add-port=8080/tcp
sudo firewall-cmd --reload

#Now, test Jenkins by visiting the following address from your web browser:
http://<your-Vultr-server-IP>:8080

#Get Jenkins password
cat /var/lib/jenkins/secrets/initialAdminPassword
cat /var/log/jenkins/jenkins.log
