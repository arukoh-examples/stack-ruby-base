# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.hostname = "stack-ruby-base"
  config.vm.box      = "dummy"

  config.ssh.username         = "ec2-user"
  config.ssh.private_key_path = ENV["SSH_PRIVATE_KEY_PATH"]
  config.ssh.max_tries        = 40
  config.ssh.timeout          = 120

  config.vm.provider :aws do |aws, override|
    aws.access_key_id     = ENV["AWS_ACCESS_KEY_ID"]
    aws.secret_access_key = ENV["AWS_SECRET_ACCESS_KEY"]
    aws.region            = "ap-northeast-1"
    aws.instance_type     = "t1.micro"
    aws.ami               = "ami-39b23d38" # https://aws.amazon.com/marketplace/pp/B00635Y2IW/ref=srh_res_product_title?ie=UTF8&sr=0-2&qid=1372213880882
    aws.keypair_name      = ENV["AWS_KEYPAIR_NAME"]
    aws.security_groups   = ["default"]
    aws.tags              = { Name: 'stack-ruby-base' }
    aws.user_data = <<-USER_DATA
#!/bin/bash
echo 'Defaults:root !requiretty\nDefaults:ec2-user !requiretty' > /etc/sudoers.d/999-vagrant-cloud-init-requiretty
chmod 440 /etc/sudoers.d/999-vagrant-cloud-init-requiretty
    USER_DATA
  end

  config.omnibus.chef_version = :latest

  config.berkshelf.berksfile_path = "./Berksfile"
  config.berkshelf.enabled        = true

  config.vm.provision :chef_solo do |chef|
    chef.add_recipe "rvm::system"

    chef.json = {
      rvm: {
        default_ruby: "ruby-1.9.3-p448",
#        rubies: ["1.9.3"],
        global_gems: [
          { name: 'bundler' }
        ]
      }
    }
  end
end
