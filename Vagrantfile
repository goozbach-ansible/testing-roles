# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.provision :shell, :inline => "sudo /usr/bin/yum -y install python-simplejson && echo 'success!' || echo 'failed python-json provisioning'"
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/site.yml"
    ansible.groups = {
      "allEL" => ["cent5", "cent6", "cent7"],
      "el5" => ["cent5"],
      "el6" => ["cent6"],
      "el7" => ["cent7"],
      "gt5" => ["cent5", "cent6", "cent7"],
      "gt6" => ["cent6", "cent7"],
      "gt7" => ["cent7"],
    }
  end

  config.vm.define "cent5" do |cent5|
    cent5.vm.box = "centos5-x86_64"
    cent5.ssh.forward_agent = true
  end

  config.vm.define "cent6" do |cent6|
    cent6.vm.box = "CentOS-6.5_x86_64-20140116"
    cent6.ssh.forward_agent = true
  end

  config.vm.define "cent7" do |cent7|
    cent7.vm.box = "centos7-x86_64"
    cent7.ssh.forward_agent = true
  end
end
