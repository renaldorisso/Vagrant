# -*- mode: ruby -*-

# vi: set ft=ruby :

boxes = [
    {
        :name => "server1",
        :eth1 => "192.168.56.10",
        :mem => "1024",
        :cpu => "1"
    },
    {
        :name => "server2",
        :eth1 => "192.168.56.11",
        :mem => "1024",
        :cpu => "2"
    },
    {
        :name => "server3",
        :eth1 => "192.168.56.12",
        :mem => "2048",
        :cpu => "2"
    }
]

Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/bionic64"

  # Turn off shared folders
  # config.vm.synced_folder ".", "/vagrant", id: "vagrant-root", disabled: true

  boxes.each do |opts|
    config.vm.define opts[:name] do |config|
      config.vm.hostname = opts[:name]
       
      config.vm.provider "virtualbox" do |v|
        v.memory = opts[:mem]
        v.cpus = opts[:cpu]
      end

      config.vm.provider "virtualbox" do |v|
        v.customize ["modifyvm", :id, "--name", opts[:name]]
        v.customize ["modifyvm", :id, "--memory", opts[:mem]]
        v.customize ["modifyvm", :id, "--cpus", opts[:cpu]]
      end

      config.vm.network :private_network, ip: opts[:eth1]
    end
  end
end
