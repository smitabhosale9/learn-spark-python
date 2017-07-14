# Learn Spark2 with Python

1. [Set up your machine](https://github.com/soumendra/learn-spark-python/blob/master/setting-up.md)
2. [Go through the pre-class reading list](https://github.com/soumendra/learn-spark-python/blob/master/pre-course-reading.md)

# Setting up AWS instance

When you are logging into a new ec2 instance for the first time, execute the following:

```bash
sudo apt-get update -y
sudo apt-get upgrade -y
sudo apt-get install -y python-dev software-properties-common curl default-jre 
sudo apt-get install -y default-jdk python-software-properties byobu vim

sudo apt-get install git git-core
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
```
* Set up anaconda - https://github.com/soumendra/python-machinelearning-setup
* clone and install from spark.yml


```bash
jupyter notebook --generate-config
mkdir certs
cd certs
cd ~/.jupyter
vim jupyter_notebook_config.py
```

content:

> c = get_config()

> c.NotebookApp.certfile = u'/home/ubuntu/certs/mycert.pem'

> c.NotebookApp.ip = '*'

> c.NotebookApp.open_browser = False 

> c.NotebookApp.port = 8888
