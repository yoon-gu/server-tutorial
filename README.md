# Server Settings
## IPython Notebook Server
1. `sudo apt-get update`
1. `sudo apt-get install python-dev python-pip`
1. `sudo pip install ipython`
1. `sudo apt-get install python-numpy python-scipy python-matplotlib ipython ipython-notebook python-pandas python-sympy python-nose`
1. `sudo pip install jupyter`
1. `ipython profile create nbserver`
1. `from IPython.lib import passwd`
1. `passwd()`
1. `cd /home/ubuntu/certificates/`
1. `openssl req -x509 -nodes -days 365 -newkey rsa:1024 -keyout mycert.pem -out mycert.pem`
1. `nano ~/.ipython/profile_nbserver/ipython_config.py`
1. Copy and paste
```
# Configuration file for ipython.

#------------------------------------------------------------------------------
# Configurable configuration
#------------------------------------------------------------------------------
c = get_config()
c.IPKernelApp.pylab = 'inline'
c.NotebookApp.certfile = u'/home/ubuntu/certificates/mycert.pem'
c.NotebookApp.ip = '*'
c.NotebookApp.open_browser = False
c.NotebookApp.password = u'YOURpasswordKey'
c.NotebookApp.port = 8888
#--------------------------------
```
1. Open port 8888 in AWS EC2
1. `jupyter notebook --profile=nbserver --ip=0.0.0.0`
1. Done