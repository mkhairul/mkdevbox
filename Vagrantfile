Vagrant.configure(2) do |config|

    config.vm.box = "bento/ubuntu-19.10"
    config.vm.box_check_update = true
    config.vm.hostname = "mkdev"
    config.vm.define "mkdev"

    config.vm.network :forwarded_port, guest: 80, host: 8000
    config.vm.network :forwarded_port, guest: 3306, host: 3306
	config.vm.network :forwarded_port, guest: 8888, host: 8888
	config.vm.network :forwarded_port, guest: 8001, host: 8001
	config.vm.network :forwarded_port, guest: 8002, host: 8002
	config.vm.network :forwarded_port, guest: 9527, host: 9527

    config.vm.network "private_network", ip: "192.168.2.2"

    config.vm.provider :virtualbox do |v|
		v.name = "dev"
		v.customize ["modifyvm", :id, "--ioapic", "on"]
        v.customize ["modifyvm", :id, "--memory", "4096"]
        v.customize ["modifyvm", :id, "--vram", "32"]
	    v.customize ["modifyvm", :id, "--cpus", "4"]
		v.customize ["setextradata", :id, "VBoxInternal2/SharedFoldersEnableSymlinksCreate/v-root", "1"]
    end
    
    # set project folder here:
    config.vm.synced_folder "../work", "/var/www"

	config.vm.provision "shell", path: "./scripts/setup.sh", privileged: false
end
