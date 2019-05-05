Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.provider "virtualbox" do |v|
    v.memory = 2048
    v.cpus = 2
#  config.vm.provision "file", source: "ansible", destination: "/opt/ansible"
  config.vm.network "forwarded_port", guest: 5000, host: 5000
  end
   config.vm.provision "shell", inline: <<-SHELL
     apt-get update
     apt-get install -y software-properties-common
     apt-add-repository ppa:ansible/ansible
     apt-get update
     apt-get install -y ansible
     ansible-playbook -i hosts /vagrant/ansible/playbook.yml	
   SHELL
end
