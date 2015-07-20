Vagrant.configure(2) do |config|

	#Allocate CPU and Memory resouces to this VM	
	config.vm.provider "virtualbox" do |v|
	    v.memory = 2048
	    v.cpus = 2
	end

	#VM configurations
	config.vm.hostname = "myTV.vagrant.vm"
	config.vm.box = "mytv-meanio-opscode_ubuntu-12.04_chef"
	config.vm.box_url = "https://dl.dropboxusercontent.com/u/56059290/vagrant%20boxes/mytv.box"
	config.vm.network :forwarded_port, guest: 3000, host: 3000
	config.vm.network :forwarded_port, guest: 27017, host: 27017
	config.vm.network :forwarded_port, guest: 80, host: 8080, auto_correct: true
	config.vm.network :forwarded_port, guest: 8000, host: 8000, auto_correct: true
  	config.vm.network :private_network, ip: "124.25.162.14"

  	#Scripts to install dependencies
  	$script = <<-SCRIPT
  		cd /vagrant/
  		npm install
  		bower install  
      mkdir -p logs
      chmod +x run-app         
    SCRIPT

  	#Start Provision
  	config.vm.provision "shell", inline: $script, privileged: false

end
