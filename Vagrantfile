#   Install with command

vagrant plugin 'vagrant-hostsupdater'

Vagrant.configure("2") do |config|
  config.vm.define "webserver" do |machine|
    machine.hostsupdater.aliases = ["phpmyadmin.dev", "webdb.dev", "phppgadmin.dev"]
    machine.vm.network :private_network, ip: "10.0.0.10"

    machine.vm.synced_folder ".", "/vagrant", :disabled => true, :nfs => true
    machine.vm.synced_folder "./www", "/var/www", :disabled => false, :nfs => true

    machine.vm.provider :virtualbox do |vb, override|
      vb.customize ["modifyvm", :id, "--memory", "256"]
      vb.customize ["modifyvm", :id, "--cpus", "1"]
      override.vm.box = "webdb"
      override.vm.box_url = "https://www.dropbox.com/s/cf0u7gze8myz5cf/webdb.box?dl=1"
    end
  end
end
