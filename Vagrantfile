Vagrant.configure("2") do |config|
  config.vm.box = "debian/bookworm64"
  config.ssh.insert_key = false
  config.ssh.username = "vagrant"
  config.vm.synced_folder ".", "/vagrant", disabled: true

  config.vm.provider :virtualbox do |vb|
    vb.memory = "512"
    vb.cpus = 1
  end

  hosts = {
    "host1" => "192.168.18.200",
    "host2" => "192.168.18.201",
    "server1" => "192.168.18.202"
  }

  config.vm.define "server1" do |server1|
    server1.vm.hostname = "server1"
    server1.vm.network "public_network", ip: hosts["server1"]
    server1.vm.provider :virtualbox do |vb|
      vb.memory = "768"
    end
  end

  config.vm.define "host1" do |host1|
    host1.vm.hostname = "host1"
    host1.vm.network "public_network", ip: hosts["host1"]
  end

  config.vm.define "host2" do |host2|
    host2.vm.hostname = "host2"
    host2.vm.network "public_network", ip: hosts["host2"]
  end
end