Vagrant.configure(1) do |config|
  config.vm.box = "ubuntu/trusty64"
  
  config.vm.hostname = 'myUbuntu'
  config.vm.provider 'virtualbox' do |virtualbox|
    virtualbox.linked_clone = true
    virtualbox.name = 'myUbubtu'
    virtualbox.gui = true
    virtualbox.memory =  1*1024
    virtualbox.cpus = 1
    virtualbox.customize ['modifyvm', :id, '--vram', 64]
    virtualbox.customize ['modifyvm', :id, '--clipboard', 'bidirectional']
    virtualbox.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    virtualbox.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
  end

  config.vm.network "forwarded_port", guest: 8080, host: 8080, protocol: "tcp"

  config.vm.provision 'shell' do |initscript|
    initscript.path="user-data.sh"
  end
  config.vm.provision "file" do | filecopy|
    filecopy.source= "~/.gitconfig"
    filecopy.destination= ".gitconfig"
  end
end
