# RHCSA 8 Automated Practice Deployment
_Powered by Ansible and Vagrant_ 

## Installation options below:
## macOS
_Gatekeeper will block virtualbox from installing. All you have to do is go to Security & Privacy of System Preferences and click Allow under the General tab and rerun installation._

##### Install all at once with the command below:
`brew install ansible ; brew install python ; brew cask install vagrant ; brew cask install VirtualBox ; brew cask install virtualbox-extension-pack ; vagrant plugin install vagrant-guest_ansible`

##### Alternatively, you can install everything individually below.
- [Latest Version of Vagrant](https://www.vagrantup.com/downloads.html) - (`brew cask install vagrant`)
    - Vagrant Plugin - `vagrant plugin install vagrant-guest_ansible`
- [Latest Version of Virtualbox](https://www.virtualbox.org/wiki/Downloads) (`brew cask install VirtualBox`)
    - Virtual Box Extension Pack (`brew cask install virtualbox-extension-pack`)

##### Once the above software is installed. Do the following if you're running the environment on Mac:
1. Create a separate `~/bin` directory and `cd` to it.  (The directory doesn't have to be ~/bin, it can be anything you want.)
2. Clone the environment repo to it with `git clone https://github.com/rdbreak/rhcsa8env.git`
3. Change to the `rhcsa8env` directory that is now in your `~/bin` directory.
4. Run `vagrant up` to deploy the environment (If the environment has a designated repo VM it will take the longest to deploy the first time only, this is because the repo system has all the packages available to the base release and will be quicker on subsequent deployments.)

## CentOS/RHEL 7 - Install all at once by Copy/Pasting the below command into your terminal as root.
_NOTE - If it's been awhile since you've run yum update, do that first. Reboot if the kernel was updated._
```
systemctl stop packagekit; yum install -y epel-release && yum install -y git binutils gcc make patch libgomp glibc-headers glibc-devel kernel-headers kernel-devel dkms libvirt libvirt-devel ruby-devel libxslt-devel libxml2-devel libguestfs-tools-c ; mkdir ~/Vagrant ; cd ~/Vagrant ; curl -o  vagrant_2.2.5_x86_64.rpm https://releases.hashicorp.com/vagrant/2.2.5/vagrant_2.2.5_x86_64.rpm && yum install -y vagrant_2.2.5_x86_64.rpm && vagrant plugin install vagrant-guest_ansible ; vagrant plugin install vagrant-libvirt ; vagrant plugin install vagrant-guest-ansible ; wget -O /etc/yum.repos.d/virtualbox.repo wget http://download.virtualbox.org/virtualbox/rpm/rhel/virtualbox.repo ; yum install -y VirtualBox-6.0 && systemctl start packagekit
```
##### Also, install the Virtualbox extension pack below
- [Virtual Box Extension Pack](https://www.virtualbox.org/wiki/Downloads)

## Debian
_NOTE - If it's been awhile since you've run apt update, do that first. Reboot if the kernel was updated._

##### Install all at once by Copy/Pasting the below command into your terminal as root.
```
sudo snap install ruby ; sudo apt install ruby-bundler git -y; wget -c https://releases.hashicorp.com/vagrant/2.2.5/vagrant_2.2.5_x86_64.deb ; sudo dpkg -i vagrant_2.2.5_x86_64.deb ; wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add - ; wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add - ; sudo add-apt-repository "deb http://download.virtualbox.org/virtualbox/debian bionic contrib"; sudo apt update; sudo apt install -y virtualbox-6.0 ; vagrant plugin install vagrant-guest_ansible
```
##### Also, install the Virtualbox extension pack below
- [Virtual Box Extension Pack](https://www.virtualbox.org/wiki/Downloads)

##### Once the above software is installed. Do the following if you're running the environment on Linux:
1. Create a separate `~/bin` directory and `cd` to it.  (The directory doesn't have to be ~/bin, it can be anything you want.)
2. Clone the environment repo to it with `git clone https://github.com/rdbreak/rhcsa8env.git`
3. Change to the `rhcsa8env` directory that is now in your `~/bin` directory.
4. Run `vagrant up` to deploy the environment (If the environment has a designated repo VM it will take the longest to deploy the first time only, this is because the repo system has all the packages available to the base release but will be quicker on subsequent deployments.)

## Windows 
- [Latest Version of Vagrant](https://www.vagrantup.com/downloads.html)
    - Vagrant Plugin - Open PowerShell as Administrator and run `vagrant plugin install vagrant-guest_ansible`
- [Latest Version of Virtualbox and Virtual Box Extension Pack](https://www.virtualbox.org/wiki/Downloads)

##### Once the above software is installed. Do the following if you're running the environment on Windows:
1. Create a separate `~/bin` directory and `cd` to it using the same PowerShell as Administrator.  (The directory doesn't have to be ~/bin, it can be anything you want.)
2. Use your browser of choice and navigate to https://github.com/rdbreak/rhcsa8env, press the green “Clone or download” button then the “Download ZIP” button. Or use Github Desktop (See below).
3. Once downloaded, unzip the file and move it to the directory you created earlier, `~/bin` in the above example.
4. Use PowerShell as Administrator again and cd to the `~/bin/rhcsa8env` directory then run `vagrant up` to deploy the environment. (If the environment has a designated repo VM it will take the longest to deploy the first time only, this is because the repo system has all the packages available to the base release but will be quicker on subsequent deployments.)

**Also, don't be spooked by any scary red font during the setup process. There are known issues that won't have a negative affect on the environment.**

_Now the deployment should be up and running!_

## (Recommended) Install Github Desktop to make pulling down changes easier
_NOTE this requires a free Github account_
1. Navigate to https://desktop.github.com/ and download Github Desktop.
2. Create or sign in to your account.
3. Click "Clone a repository from the Internet" and enter "rdbreak/rhcsa8env" and choose a location then "Clone".
4. You are also able to easily pull changes when they're made available.

## Other Useful Information:
You can also use the VirtualBox console to interact with the VMs or through a terminal. If you need to reset the root password, you would need to use the console. I'm constantly making upgrades to the environments, so every once and awhile run `git pull` in the repo directory to pull down changes. If you're using Windows, it's recommended to use Github Desktop so you can easily pull changes that are made to the environment. The first time you run the vagrant up command, it will download the OS images for later use. In other words, it will take longest the first time around but will be faster when it is deployed again. You can run `vagrant destroy -f` to destroy your environment at anytime. **This will erase everything**. This environment is meant to be reuseable, If you run the `vagrant up` command after destroying the environment, the OS image will already be downloaded and environment will deploy faster. Deployment should take around 15 minutes depending on your computer. You shouldn't need to access the IPA server during your practice exams. Everything should be provided that you would normally need during an actual exam. Hope this helps in your studies!

## Included systems:
- repo.eight.example.com
- ipa.eight.example.com
- system1.eight.example.com

## System Details:
> ipa
- 192.168.55.150
- Gateway - 192.168.55.1
- DNS - 8.8.8.8
> system1
- 192.168.55.151
- Gateway - 192.168.55.1
- DNS - 8.8.8.8

There is a Repo/AppStream available to use from `http://repo.eight.example.com/BaseOS` and `http://repo.eight.example.com/AppStream`

## Accessing the systems
Remember to add the IP addresses to your local host file if you want to connect to the guest systems with the hostname.
Username - vagrant
Password - vagrant
- For root - use `sudo` or `sudo su`
Access example - `ssh vagrant@192.168.55.151` or `vagrant ssh system`

## Help
If you're having problems with the environment, please submit an issue by going to the `ISSUES` tab at the top. If you have more questions, looking for practice exams to use against this environment, or just looking for a fantastic Red Hat community to join, please navigate to #practiceexam in the [Red Hat Certs Slack Workspace](https://join.slack.com/t/redhat-certs/shared_invite/enQtNjM4MTA3OTU1NDI0LTRkMzYxOGY3NjEwNTk4ZWQwMGMwMmMyNWYxMDRlZjg4NzgwMDdmZGU2OGNjMzMwNDQ1MTY1NmY1N2U3NTNlYWM).
