* [Vim help](https://www.cs.oberlin.edu/~kuperman/help/vim/)
* [ssh help](https://askubuntu.com/questions/48555/how-to-set-up-a-ubuntu-server-to-be-securely-available-from-internet), [firewall: ufw](https://www.cyberciti.biz/faq/ufw-allow-incoming-ssh-connections-from-a-specific-ip-address-subnet-on-ubuntu-debian/), [networking](https://unix.stackexchange.com/questions/54975/how-to-check-that-a-daemon-is-listening-on-what-interface)
	- Commands: `grep ^ListenAddress /etc/ssh/sshd_config`, 
	- `lsof -i -n -p`
	- `ss -lp | grep -i ssh` # 
	- `ss -nlput  | grep sshd` # which ports to listen to on every avail ip address 
	- `ip -4 a` or `ip -6 a` # which IP addresses are listening 
	- `lsof -i -n -p` or `ss -lp` or `netstat` also work

* [VNC](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-14-04)
* [IP](https://askubuntu.com/questions/181723/connecting-to-ubuntu-server-via-ssh-externally)
  `test_ip.sh` created

* `grep -r "search term" directory` to find a line in a directory, any file and `grep -r '/usr/local/bin' /etc` to find PATH

sudo ss -nlput | grep sshd
sudo ufw enable; sudo ufw allow ssh; sudo ufw status verbose
