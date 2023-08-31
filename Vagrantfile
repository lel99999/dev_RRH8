Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox" do |v|
    v.memory = "1024"
    v.cpus = 2
    v.customize ["modifyvm", :id, "--cpuexecutioncap", "70"]
  end
# config.trigger.after :up do |trigger|
#   run "subscription-manager register --username <username> --password <password> --auto-attach
#   trigger.name = "After-Up Trigger ..."
#   trigger.info = "Trigger Execution ..."
#   trigger.run = { path:"subscription-manager register --username <username> --password <password> --auto-attach"}
# end
# config.ssh.private_key_path = "~/.ssh/id_rsa"
  config.ssh.forward_agent = true
  config.vm.define "RRH8" do |rrh8|
#   rrh7.vm.box = "clouddood/RH7.5_baserepo"
# config.ssh.private_key_path = "~/.vagrant.d/insecure_private_key"
#  config.ssh.username = "vagrant"
#  config.ssh.password = "vagrant"
  config.ssh.forward_agent = true
  config.ssh.extra_args = ["-o", "PubkeyAcceptedKeyTypes=+ssh-rsa", "-o", "HostKeyAlgorithms=+ssh-rsa"]
# config.ssh.password = "vagrant"

  config.vm.define "RRH8" do |rrh8|
#   rrh7.vm.box = "clouddood/RH7.5_baserepo"
#   rrh8.vm.box = "clouddood/RH8.6_infra"
    rrh8.vm.box = "clouddood/RHEL8.8_base"
    rrh8.vm.hostname = "RRH8"
    rrh8.vm.network "private_network", ip: "192.168.60.148"
    rrh8.vm.provision "shell", :inline => "sudo echo '192.168.60.148 RRH8.local RRH8' >> /etc/hosts"
    rrh8.vm.provision "ansible" do |ansible|
#     ansible.playbook = "deploy_R_Test.yml"
      ansible.playbook = "deploy_RRH8.yml"
      ansible.inventory_path = "vagrant_hosts"
      #ansible.tags = ansible_tags
      #ansible.verbose = ansible_verbosity
      #ansible.extra_vars = ansible_extra_vars
      #ansible.limit = ansible_limit
    end
  end
# config.trigger.before :destroy do |trigger|
#   run "rm -Rf /tmp/abc/*"
    # subscription-manager remove --all
    # subscription-manager unregister
    # subscription-manager clean
#   trigger.name = "Destroy Trigger ..."
#   trigger.info = "Destroy Trigger Execution ..."
#   trigger.run = { path: "subscription-manager remove --all"}
#   trigger.run = { path: "subscription-manager unregister"}
#   trigger.run = { path: "subscription-manager clean"}
# end
end
