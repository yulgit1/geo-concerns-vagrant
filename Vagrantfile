# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.
	
	config.vm.hostname = "geo-concerns"

	config.vm.box = "ubuntu/trusty64"

	config.vm.network :forwarded_port, guest: 3000, host: 3000 # Rails
	config.vm.network :forwarded_port, guest: 8983, host: 8983 # Solr 5.4
	config.vm.network :forwarded_port, guest: 8984, host: 8984 # Fedora 4.5

  config.vm.provider "virtualbox" do |v|
  	v.memory = 2048
  end

  shared_dir = "/vagrant"

  config.vm.provision "shell", path: "./install_scripts/bootstrap.sh", args: shared_dir
  config.vm.provision "shell", path: "./install_scripts/java.sh", args: shared_dir
  config.vm.provision "shell", path: "./install_scripts/ruby.sh", args: shared_dir
  config.vm.provision "shell", path: "./install_scripts/fits.sh", args: shared_dir
  config.vm.provision "shell", path: "./install_scripts/geo.sh", args: shared_dir
  config.vm.provision "shell", path: "./install_scripts/geo-concerns.sh", args: shared_dir, privileged: false
  config.vm.provision "shell", path: "./install_scripts/cleanup.sh", args: shared_dir
  config.vm.provision "shell", path: "./install_scripts/zerodisk.sh", args: shared_dir
end
