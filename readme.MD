### Prerequisites
 * install jdk
```
curl -L -b "oraclelicense=a" -O https://download.oracle.com/otn-pub/java/jdk/8u202-b08/1961070e4c9b4e26a04e7f5a083f551e/jdk-8u202-linux-x64.rpm
sudo yum localinstall jdk-8u162-linux-x64.rpm
java -version
```
* Either set the jdk path to .bash_profile or to profile.d
    * use following command to get the path
```
rpm -qc $(rpm -qa | grep jdk)
```

### Installation
```
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat/jenkins.io.key
yum update
yum install jenkins -y
```

### Start jenkins daemon
```
sysmtemctl start jenkins
```

### Make it persistent(start on boot)
```
systemctl enable jenkins
```

* Execute http://<ip/domain>:8080 on browser 
    * To check initial unlock code 
    ```sudo cat /var/lib/jenkins/secrets/initialAdminPassword```

## Troubleshoot
* Cannot access 8080
```
firewall-cmd --list-port
firewall-cmd --add-port=8080/tcp --permanent
firewall-cmd --reload
```
