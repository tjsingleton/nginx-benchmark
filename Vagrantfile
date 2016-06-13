Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  
  config.cache.scope = :box if Vagrant.has_plugin?("vagrant-cachier")

  if Vagrant.has_plugin?("vagrant-hostmanager")
    config.hostmanager.enabled = true
    config.hostmanager.manage_host = true
    config.hostmanager.manage_guest = true

    config.vm.hostname = "nginx-benchmark.vagrant.vm"
  end

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y nginx
    cp -f /vagrant/nginx/example.conf /etc/nginx/sites-enabled
    ln -f -s /etc/nginx/sites-enabled/example.conf /etc/nginx/sites-available
    /etc/init.d/nginx reload
  SHELL
end
