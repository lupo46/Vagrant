

nodes = [
  { :hostname => 'rabbit1', :ip => '192.168.1.41', :box => 'geerlingguy/centos7', :ram => 512 },
  { :hostname => 'rabbit2', :ip => '192.168.1.42', :box => 'geerlingguy/centos7', :ram => 512 },
  { :hostname => 'rabbit3', :ip => '192.168.1.43', :box => 'geerlingguy/centos7', :ram => 512 }
]

Vagrant.configure("2") do |config|
  nodes.each do |node|
    config.vm.define node[:hostname] do |nodeconfig|
      #config.vm.box = :box
	  config.vm.box = "geerlingguy/centos7"
      nodeconfig.vm.hostname = node[:hostname] + ".box"
      nodeconfig.vm.network :private_network, ip: node[:ip]

      memory = node[:ram] ? node[:ram] : 256;
      nodeconfig.vm.provider :virtualbox do |vb|
        vb.customize [
          "modifyvm", :id,
          "--cpuexecutioncap", "50",
          "--memory", memory.to_s,
        ]
      end
    end
  end
end

