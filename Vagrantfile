# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "fgrehm/centos-6-64-lxc"

  config.ssh.insert_key = false

  if Vagrant.has_plugin?('vagrant_cachier')
    config.cache.scope = :box
  end

  config.vm.define 'ruby' do |instance|
    if Vagrant.has_plugin?('vagrant-hosts')
      instance.vm.provision :hosts
    end

    instance.vm.provision 'shell', inline: <<-SHELL
      # install git
      sudo yum install -y git
      # install (the many) dependencies necessary for ruby install
      sudo yum install -y gcc-c++ patch readline readline-devel zlib zlib-devel libyaml-devel libffi-devel openssl-devel make bzip2 autoconf automake libtool bison iconv-devel sqlite-devel tar
      # install rvm
      gpg2 --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
      curl -L get.rvm.io | sudo bash -s stable
      source /etc/profile.d/rvm.sh
      # $profit$
      rvm install 2.1.10
      rvm use 2.1.10 --default
    SHELL

    instance.vm.provision 'shell', inline: <<-SHELL
      # install janus
      curl -L https://bit.ly/janus-bootstrap | bash
    SHELL

  end
  
end
