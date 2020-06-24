Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/bionic64"

    config.vm.define "ansible_server" do |ansible|
        ansible.vm.network "public_network", ip: "192.168.15.28"

        ansible.vm.provision "shell", inline: "sudo apt-get update && sudo apt-get install -y software-properties-common && sudo apt-add-repository --yes --update ppa:ansible/ansible && sudo apt-get install -y ansible"

        #Command for testing connection to the wordpress machine through ansible-ssh 
        #ansible.vm.provision "shell", inline: "ansible -vvvv wordpress -u vagrant --private-key /vagrant/ssh_key_auth -i /vagrant/config/ansible/hosts -m shell -a 'echo Hello, world'"
    end

    config.vm.define "phpweb" do |phpweb|
        phpweb.vm.network "public_network", ip: "192.168.15.29"

        phpweb.vm.provision "shell", inline: "cat /vagrant/ssh_key_auth.pub >> .ssh/authorized_keys"

      end
  end