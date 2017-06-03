* [Vim help](https://www.cs.oberlin.edu/~kuperman/help/vim/)
* [ssh help](https://askubuntu.com/questions/48555/how-to-set-up-a-ubuntu-server-to-be-securely-available-from-internet), [firewall: ufw](https://www.cyberciti.biz/faq/ufw-allow-incoming-ssh-connections-from-a-specific-ip-address-subnet-on-ubuntu-debian/), [networking](https://unix.stackexchange.com/questions/54975/how-to-check-that-a-daemon-is-listening-on-what-interface)
	- Commands: `grep ^ListenAddress /etc/ssh/sshd_config`, 
	- `lsof -i -n -p`
	- `ss -lp | grep -i ssh` # 
	- `ss -nlput  | grep sshd` # which ports to listen to on every avail ip address 
	- `ip -4 a` or `ip -6 a` # which IP addresses are listening 
	- `lsof -i -n -p` or `ss -lp` or `netstat` also work
* [HW troubleshooting](https://askubuntu.com/questions/14008/i-have-a-hardware-detection-problem-what-logs-do-i-need-to-look-into/61547)
	- `lshw`, `sudo lshw -class network`, `lsusb`, `lspci`
	- `rfkill list all`: wireless card is soft-blocked?
	- `/var/log/udev` and `/var/log/dmesg` for udev and kernel issues
	- `dmesg` or `ls -lrt /var/log` for details
* [VNC](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-14-04)
* [IP](https://askubuntu.com/questions/181723/connecting-to-ubuntu-server-via-ssh-externally)
  `test_ip.sh` created
* [BigDL](https://software.intel.com/en-us/articles/bigdl-scale-out-deep-learning-on-apache-spark-cluster)
	- Requires Java8 from Oracle; Maven
	- Installing [Spark](https://gist.github.com/domderen/27caeb7eb02118d71279)
	- BigDL build instructions
	- Requires Spark cluster running - [inst](https://github.com/amplab/spark-ec2): standalone ok
* [Oracle Java8](https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-get-on-ubuntu-16-04)
	```bash
	sudo add-apt-repository ppa:webupd8team/java
	sudo apt-get update
	sudo apt-get install oracle-java8-installer 
	sudo update-alternatives --config java 
	sudo vi /etc/environment # SetJAVA_HOME
	source /etc/environment
	```

* `grep -r "search term" directory` to find a line in a directory, any file and `grep -r '/usr/local/bin' /etc` to find PATH
* Fresh R install [R and Finance](https://msperlin.github.io/2017-06-01-Instaling-R-in-Linux/)
	```bash
	#!/bin/bash
	# Adds R to apt and install it
	#
	# Instructions:
	# sudo chmod 700 InstallR.sh
	# ./FirstTimeInstallR.sh

	# Install R

	sudo echo "deb http://cran.rstudio.com/bin/linux/ubuntu trusty/" | sudo tee -a /etc/apt/sources.list

	gpg --keyserver keyserver.ubuntu.com --recv-key E084DAB9
	gpg -a --export E084DAB9 | sudo apt-key add -

	sudo apt-get update
	sudo apt-get install -y r-base r-base-dev r-cran-xml r-cran-rjava libcurl4-openssl-dev
	sudo apt-get install -y libssl-dev libxml2-dev openjdk-7-* libgdal-dev libproj-dev libgsl-dev
	sudo apt-get install -y xml2 default-jre default-jdk mesa-common-dev libglu1-mesa-dev freeglut3-dev 
	sudo apt-get install -y mesa-common-dev libx11-dev r-cran-rgl r-cran-rglpk r-cran-rsymphony r-cran-plyr 
	sudo apt-get install -y  r-cran-reshape  r-cran-reshape2 r-cran-rmysql

	sudo R CMD javareconf 

	# install RStudio 1-0.143-amd64
	# Link and version at: https://www.rstudio.com/products/rstudio/download2/

	sudo apt-get install gdebi-core
	wget https://download1.rstudio.org/rstudio-1.0.143-amd64.deb
	sudo gdebi -n rstudio-1.0.143-amd64.deb
	rm rstudio-1.0.143-amd64.deb
	```

sudo ss -nlput | grep sshd
sudo ufw enable; sudo ufw allow ssh; sudo ufw status verbose
