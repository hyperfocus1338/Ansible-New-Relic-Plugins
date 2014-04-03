Vagrant.configure("2") do |config|

	config.vm.synced_folder "/vagrant", "/vagrant", disabled: true

	config.vm.provider "virtualbox" do |v|

		v.gui = false

#		v.customize ["modifyvm", :id, "--memory", "512"]
		v.customize ["modifyvm", :id, "--memory", "1024"]
#		v.customize ["modifyvm", :id, "--memory", "2048"]

#		v.customize ["modifyvm", :id, "--cpus", "1"]
		v.customize ["modifyvm", :id, "--cpus", "2"]

	end


	config.vm.define "virtualbox" do |virtualbox|

		virtualbox.vm.hostname = "cloudserver"
		virtualbox.vm.box = "saucyserver"
		virtualbox.vm.network "private_network", ip: "192.168.7.5"

	end


	config.vm.provision "ansible" do |ansible|


### NewRelic plugins
#
		ansible.tags = "java", "newrelic", "newrelic_nginx", "newrelic_mysql"


### Separate
#
		ansible.tags = "newrelic"
#		ansible.tags = "newrelic_nginx"
#		ansible.tags = "newrelic_mysql"



### General settings
#
#		ansible.verbose = "v"
#		ansible.verbose = "vv"
#		ansible.verbose = "vvv"
#		ansible.verbose = "vvvv"
		ansible.playbook = "site.yml"



# Hosts
#
		ansible.limit = "all"
#		ansible.limit = "web"
#		ansible.limit = "database"
#		ansible.limit = "cache"

		ansible.inventory_path = "development"

	end

end