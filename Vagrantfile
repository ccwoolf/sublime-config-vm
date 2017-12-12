# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "geerlingguy/centos7"

  config.vm.provider "virtualbox" do |vb|
     vb.linked_clone = true
  end

  config.vm.provision "shell", inline: <<-SHELL
    # Install a super simple GUI
    sudo yum install -y deltarpm yum-utils epel-release
    sudo yum groupinstall -y X11
    sudo yum install -y openbox dejavu-lgc-sans-fonts dejavu-lgc-sans-mono-fonts

    pushd /home/vagrant
      # Set Openbox to be the session when launching X
      mkdir -pv .config
      cp -Rv /etc/xdg/openbox .config
      echo "exec openbox-session" >> .xinitrc
      chown -vR vagrant:vagrant .xinitrc .config

      # Add Sublime Text repository
      sudo rpm -v --import https://download.sublimetext.com/sublimehq-rpm-pub.gpg
      sudo yum-config-manager --add-repo https://download.sublimetext.com/rpm/stable/x86_64/sublime-text.repo
      sudo yum install -y sublime-text

      # Link Sublime's configuration directory to the Vagrant shared directory
      ln -s /vagrant/sublime-text-3 .config/sublime-text-3
    popd
  SHELL
end
