# Setting up Detection Labs for USCGA Cyber Team

 For the USCGA cyber team we currently utilize virtual box to host the virtualized enviroments. There are current plans to implement this using ESXi for long term but at the moment this is used for testing.

## Automated Script

* Change directories

`cd DetectionLab/Vagrant/`

* Change the permissions to make the file executable

`chmod +x USCGA_build.sh`

* Run the script!!!

`./USCGA_build.sh`

## Manual Set uo

The following commands were used to install virtual box and deploy the lab enviroment.

* Update the box

`sudo apt update`

* Download the keys for virtual box install

`wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -`
`wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add -`

* Add the repo to the apt sources

`sudo apt-add-repository "deb [arch=amd64] https://download.virtualbox.org/virtualbox/debian $(lsb_release -cs) contrib"`

* Update to configure to the new sources

`sudo apt update`

* Install Virtual Box 6.1

`sudo apt install virtualbox-6.1`

* Download and install the virtual box extension pack

`wget https://download.virtualbox.org/virtualbox/6.1.32/Oracle_VM_VirtualBox_Extension_Pack-6.1.32.vbox-extpack`

`sudo VBoxManage extpack install  Oracle_VM_VirtualBox_Extension_Pack-6.1.32.vbox-extpack`

* Add the gpg keys for Vagrant

`curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -`

* Add the repo to our sources

`sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"`

* Update and install Vagrant

`sudo apt-get update && sudo apt-get install vagrant`

* Clone the repo from our repo

`git clone https://github.com/USCGA/DetectionLab.git`

* This just runs system checks. (Pay attention to **RED** test)

`DetectionLab/Vagrant/prepare.sh`

* Build the enviroment!!!

`vagrant up --provider=virtualbox`



