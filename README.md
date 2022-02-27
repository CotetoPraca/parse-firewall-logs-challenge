# Report iSecurity Challenge

## FIRST STEPS

Accessing the VM:
```bash
$ ssh -p <port> <user>@<ip_adress>
```

VM just asked for a reboot
```bash
$ sudo reboot
```

Updatin all outdated things in VM
```bash
$ sudo apt-get upgrade
```

Checking if Java is installed:
```bash
$ java -version
```

Installing Java on VM:
```bash
$ apt install default -jre
```

Checking again, just in case:
```bash
$ java -version
```


## INSTALLING LOGSTASH

Adding Elastic package repository to VM repository:
```bash
$ echo "deb https://artifacts.elastic.co/packages/8.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-8.x.list
```

Updating any pendences and installing logstash:
```bash
$ sudo apt-get update
$ sudo apt-get install logstash
```

Checking logstash service health:
```bash
$ sudo systemctl status logstash
```

Enabling the service on boot up and starting it:
```bash
$ sudo systemctl enable logstash 
$ sudo systemctl start logstash
```

Checking if it running in fact:
```bash
$ sudo lsof -i -P -n | grep logstash
```

## SETTING UP LOGSTASH

Opening logstash conf file directory:
```bash
$ cd /etc/logstash/conf.d
```

Creating or opening (if its already created) the conf file with VIM:
```bash
$ vi syslog.conf
```


