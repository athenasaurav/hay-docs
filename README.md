# Deployment Guide

## Install and upgrade PIP
```
sudo apt update
sudo apt install python3-pip
```
## Create Virtual Env
```
pip3 install virtualenv
virtualenv test
source test/bin/activate
```
## Prepare for Elastic Search
```
apt-get update -y
apt-get upgrade -y

apt-get install apt-transport-https ca-certificates gnupg2 -y
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | apt-key add -
sh -c 'echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" > /etc/apt/sources.list.d/elastic-7.x.list'
```
## Install Elastic search
```
apt-get update -y
apt-get install elasticsearch -y
```
## Start Elastic Search
```
systemctl start elasticsearch
systemctl enable elasticsearch
```
Note : Sometimes this work on Linode : ```systemctl restart elasticsearch```

## Test Elastic Search

```curl -X GET "localhost:9200"```

## Git Clone Aurelius
```
git clone https://github.com/athenasaurav/hay-docs.git
cd hay-docs
```

## Install requirments
```pip3 install -r requirements.txt```

## Solve Milvus Error
```
pip3 uninstall pymilvus
pip3 install pymilvus==1.1.2
```

Check first if Tmux is installed or not by trying to install tmux ```sudo apt-get install tmux```

# Deploying using Tmux

Firstly use command ```tmux``` to open a tmux screen. 

By default tmux start the screen numbering from 0. You can specify name parameter to name something different the screen which will be easy to remember.

To create a Tmux session with a custom name easy to remember use the following command ```tmux new -s <sessionname or sessionnumber>```

then in the new screen run ```python3 app.py``` (on Python 3)

Voila! you bot has started running.


You can now close the SSH window or come out of screen by pressing `ctrl`+`b` and then `d`

If you would like to see whats happening in your program you can write ```tmux attach -t <screenname or screennumber>```

NOTE: we have deployed with a name ```Bot```.

To kill the screen, run command ```tmux kill-session```

