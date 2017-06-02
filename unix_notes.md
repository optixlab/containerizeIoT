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

sudo ss -nlput | grep sshd
sudo ufw enable; sudo ufw allow ssh; sudo ufw status verbose
