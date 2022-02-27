# Report iSecurity Challenge

Everything I done (and works) during the challenge.

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

## RUNNING LOGSTASH

Every change made in the conf file:
```bash
$ systemctl restart logstash.service
```

Follow what logstash doing (already running the pipeline or closing output log file).
```bash
$ tail -f /var/log/logstash/logstash-plain.log -n 5 //Follow what logstash doing
```

Parsing to logstash the sample log via TCP using NetCat when pipeling is running.
```
$ nc -w 3 127.0.0.1 5000 < /opt/data/fortigate-sample-logs.txt
```

See the output content after logstash closed the log file (using VIM):
```bash
$ vi /opt/data/logstash-log-2021.02.27.txt
```

Some VIM commands:
```
:1,$d => clear all content of a file
:x    => save and exit commmand
:q    => just exit file
```
