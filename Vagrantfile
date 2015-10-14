# -*- mode: ruby -*-
# vi: set ft=ruby :

$script = <<SCRIPT

# Enable Swappiness
/bin/dd if=/dev/zero of=/var/swap.1 bs=1M count=1024
/sbin/mkswap /var/swap.1
/sbin/swapon /var/swap.1

# Setting Aliasses
curl https://raw.githubusercontent.com/bbredewold/snippets/master/aliasses.txt -o /home/vagrant/.bash_aliases; source /home/vagrant/.bash_aliases

SCRIPT

Vagrant.configure("2") do |config|

  config.vm.box = "scotch/box"
  config.vm.network "private_network", ip: "192.168.33.10"
  config.vm.hostname = "scotchbox"
  config.vm.synced_folder ".", "/var/www/public", :mount_options => ["dmode=777", "fmode=666"]
  config.vm.provision :shell, inline: $script
  config.vm.provision :shell, path: "bootstrap.sh"

end
