Vagrant::Config.run do |config|

    # Ubuntu 12.04 LTS
    config.vm.box = "precise32"
    config.vm.box_url = "http://files.vagrantup.com/precise32.box"

    # Forward HTTP and MySQL of the guest system
    config.vm.forward_port 80,   8080  # http
    config.vm.forward_port 3306, 3306  # mysql

    # Share WordPress themes and plugins folder
    config.vm.share_folder "themes", "/var/www/wordpress/wp-content/themes", "./themes"
    config.vm.share_folder "plugins", "/var/www/wordpress/wp-content/plugins", "./plugins"

    # Provisioning!
    config.vm.provision :chef_solo do |chef|
        chef.cookbooks_path = "cookbooks"
        chef.add_recipe "apt"
        chef.add_recipe "git"
        chef.add_recipe "subversion"
        chef.add_recipe "wordpress"

        chef.json = {
            "mysql" => {
                "server_root_password"   => "vagrant",
                "server_repl_password"   => "vagrant",
                "server_debian_password" => "vagrant"
            },
            "wordpress" => {
                "version"   => "latest",
                "checksum"  => "",
                "dir"       => "/var/www",
                "db" => {
                    "database"  => "wordpress",
                    "user"      => "wordpress",
                    "password"  => "wordpress"
                }
            }
        }
    end
end