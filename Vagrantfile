require 'json'

Vagrant.configure("2") do |config|
 config.vm.box = "ubuntu12"
 config.vm.network :forwarded_port, guest: 80, host: 8080
 config.vm.hostname = "www.vagrant.com"
 config.vm.provision "chef_solo" do |chef|
 	chef.cookbooks_path ["site-cookbooks", "cookbooks"]
 	chef.data_bags_path = "data_bags"
 	chef.roles_path = "roles"
 	chef.json = load_node('vagrant.json')
end
end

private

def load_node(node)
	File.open(Pathname(__FILE__).dirname.join('nodes', node), "r") do |f|
		return JSON.load(f)
	end
end