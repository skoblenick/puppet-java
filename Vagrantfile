# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "mountain64"

  config.vm.provider :virtualbox do |vb|
    config.vm.box_url = "http://localhost/boxes/mountain64.box"
    vb.gui = true
  end

  config.vm.provider :vmware_fusion do |v|
    config.vm.box_url = "http://localhost/boxes/mountain64_vmware.box"
    v.gui = true

    v.vmx["memsize"] = "2048"
  end

  config.vm.provision :shell, :path => ".puppet/installer/setup.sh", :args => "-c /vagrant/.puppet/installer/config.json"

  config.vm.provision :shell, :path => ".puppet/module.sh"

  config.vm.provision :puppet do |puppet|
    puppet.options = "--verbose --debug"
    puppet.manifests_path = ".puppet/manifests"
    puppet.manifest_file = "site.pp"
  end

end