# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.nfs.verify_installed = false
  config.vm.synced_folder '.', '/vagrant', disabled: true
  config.vm.define "noc" do |noc|
    noc.vm.box = "debian/bullseye64"
    noc.vm.hostname = "noc"
  end
  config.vm.provision :ansible do |ansible|
    ansible.playbook = "setup.yml"
    ansible.groups = {
      "nocs" => ["noc"]
    }
    ansible.host_vars = {
      "noc" => {
                 "internal_v4" => "10.24.32.253/19",
                 "internal_v6" => "d07:96ae:572e::fffe/64",
                 "internal_v4_net" => "10.24.32.0/19",
                 "internal_v6_net" => "d07:96ae:572e::/64",
                 "wg_private_key" => "4P8I3G0e9v/7dUJT2uGbGiLnSK28UybBdyWqZizdMWI=",
                 "wg_peer_public_key" => "B88nOCZ8ol9AwD328w8AzSS3xRl/6lCTGO1ks725AlI=",
                 "wg_peer_ip" => "10.24.32.1:51820"
               }
    }
  end
end
