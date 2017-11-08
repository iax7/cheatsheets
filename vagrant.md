# Vagrant
Basic Custom Vagrantfile
```ruby
Vagrant.configure(2) do |config|
  config.ssh.insert_key = false

  config.vm.box = "ubuntu/trusty64"

  # Plugins -------------------------------
  config.proxy.http     = "http://www-proxy.com:80"
  config.proxy.https    = "http://www-proxy.com:80"
  config.proxy.no_proxy = "localhost,127.0.0.1,#{IPS.keys.join(',')},#{IPS.values.join(',')}"
  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true
  config.hostmanager.manage_guest = true
  # ---------------------------------------

  config.vm.network :private_network, ip: "192.168.77.1"

  config.vm.provider :virtualbox do |vb|
    vb.cpus = 1
    vb.memory = 1024
  end

  config.vm.define :vm1, primary: true do |box|
    box.vm.network :private_network, ip: '192.168.77.11'
    box.vm.hostname = "vm1"
  end
```
