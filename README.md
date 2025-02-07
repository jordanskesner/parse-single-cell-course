# parse-single-cell-course
Code and notes associated with the single cell RNA-seq analysis course offered by Parse Biosciences


## Notes on getting this notebook running on windows
# attempt 1: run jupyter notebook on windows subsystem for linux and access remotely
# activate windows subsystem for linux and install ubuntu
# create a and activate a new python env
# sudo apt install python3 python3-pip python3-venv
# python3 -m venv jupyter
# source jupyter/bin/activate
#  install jupyter notebook in the venv
# pip install jupyter-notebook
# generate config file
# jupyter notebook --generate-config
# set password
# jupyter notebook password
# startup the server
# jupyter notebook --no-browser --port=8080

## install ssh
sudo apt install openssh-server
## enable server
## had to restart terminal
sudo systemctl enable ssh
## check status
sudo systemctl status ssh
## got error:
## System has not been booted with systemd as init system (PID 1). Can't operate.
## Failed to connect to bus: Host is down
## trying solution from: https://askubuntu.com/questions/1379425/system-has-not-been-booted-with-systemd-as-init-system-pid-1-cant-operate
## open administrator powershell:
## download package: https://github.com/microsoft/WSL/releases/tag/2.4.10
Add-AppxPackage <path.to>/Microsoft.WSL_1.0.0.0_x64_ARM64.msixbundle
## confirm
wsl --version
## start the wsl
wsl ~
##
sudo -e /etc/wsl.conf
## make sure the below is in the file:
[boot]
systemd=true
## exit ubuntu, in powershell
wsl --shutdown
## check again in ubuntu
sudo systemctl status
## did not work. trying to restart windows and try again
#### the issue was solved by using the 'service' command instead of systemctl, as detailed in the link below:
https://linuxhandbook.com/system-has-not-been-booted-with-systemd/

#### continue with setting up ssh
## check ipaddresss
sudo apt install net-tools
ifconfig

## start the server and open in browser
source jupyter/bin/activate
jupyter notebook --no-browser --port=8080
## go to web browser in windows and enter address
http://localhost:8080/tree
# works! #

## additional note, dont try to put large filesizes in a github repo

## the host windows machine can be accessed from the ubuntu terminal at /mnt/, 
## so can easily copy the larger files into a local folder


## dont forget to generate an auth token for github for the new ubuntu terminal, after authing (requires a push?), use:
# git config --global credential.helper store
# to store the creds