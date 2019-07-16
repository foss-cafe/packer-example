# Packer Example for php-7.1


```
$ packer build -var 'aws_access_key=xyx' \
    -var 'aws_secret_key=abc' \
    7.1.x/config.json
amazon-ebs output will be in this color.

==> amazon-ebs: Prevalidating AMI Name: php-7.1.30-1563261477
    amazon-ebs: Found Image ID: ami-0b37e9efc396e4c38
==> amazon-ebs: Creating temporary keypair: packer_5d2d7a25-cc9b-8e0d-5960-3e3ba3497660
==> amazon-ebs: Creating temporary security group for this instance: packer_5d2d7a2d-69b3-1197-335c-0ae95d7bc228
==> amazon-ebs: Authorizing access to port 22 from [0.0.0.0/0] in the temporary security groups...
==> amazon-ebs: Launching a source AWS instance...
==> amazon-ebs: Adding tags to source instance
    amazon-ebs: Adding tag: "Name": "Packer Builder"
    amazon-ebs: Instance ID: i-00cc462600b73ebc7
==> amazon-ebs: Waiting for instance (i-00cc462600b73ebc7) to become ready...
==> amazon-ebs: Using ssh communicator to connect: 34.214.203.248
==> amazon-ebs: Waiting for SSH to become available...
==> amazon-ebs: Connected to SSH!
==> amazon-ebs: Provisioning with Ansible...
==> amazon-ebs: Executing Ansible: ansible-playbook --extra-vars packer_build_name=amazon-ebs packer_builder_type=amazon-ebs -o IdentitiesOnly=yes -i /var/folders/l0/sczhv02x1fg67mrt1rcgzwm00000gn/T/packer-provisioner-ansible888717506 /Users/rajeev/org/oncorps/infra/packer/php-base-image/ansible/site.yml -e ansible_ssh_private_key_file=/var/folders/l0/sczhv02x1fg67mrt1rcgzwm00000gn/T/ansible-key691518767
    amazon-ebs:
    amazon-ebs: PLAY [apply common configuration to all nodes] *********************************
    amazon-ebs:
    amazon-ebs: TASK [Gathering Facts] *********************************************************
    amazon-ebs: ok: [default]
    amazon-ebs:
    amazon-ebs: TASK [common : install aptititude] *********************************************
    amazon-ebs:  [WARNING]: Could not find aptitude. Using apt-get instead
    amazon-ebs: changed: [default]
    amazon-ebs:
    amazon-ebs: TASK [common : Install a list of packages] *************************************
    amazon-ebs: changed: [default]
    amazon-ebs:
    amazon-ebs: TASK [common : debian | ensure the apt repository key is present] **************
    amazon-ebs: changed: [default]
    amazon-ebs:
    amazon-ebs: TASK [common : debian | ensure the apt repository is present] ******************
    amazon-ebs: changed: [default]
    amazon-ebs:
    amazon-ebs: TASK [common : debian | set license as accepted] *******************************
    amazon-ebs: changed: [default]
    amazon-ebs:
    amazon-ebs: TASK [common : debian | set license as accepted] *******************************
    amazon-ebs: ok: [default]
    amazon-ebs:
    amazon-ebs: TASK [common : debian | ensure Java is installed] ******************************
    amazon-ebs: changed: [default]
    amazon-ebs:
    amazon-ebs: TASK [php : apt_repository] ****************************************************
    amazon-ebs: changed: [default]
    amazon-ebs:
    amazon-ebs: TASK [php : Run the equivalent of "apt-get update" as a separate step] *********
    amazon-ebs: changed: [default]
    amazon-ebs:
    amazon-ebs: TASK [php : Install a list of packages for php] ********************************
    amazon-ebs: changed: [default]
    amazon-ebs:
    amazon-ebs: TASK [php : ensure php7.1-fpm is running] **************************************
    amazon-ebs: ok: [default]
    amazon-ebs:
    amazon-ebs: TASK [php : Copy the www conf file] ********************************************
    amazon-ebs: changed: [default]
    amazon-ebs:
    amazon-ebs: TASK [php : Enable service php-fpm, and not touch the state] *******************
    amazon-ebs: ok: [default]
    amazon-ebs:
    amazon-ebs: TASK [php : adding ssh-figer-print] ********************************************
    amazon-ebs: # github.com:22 SSH-2.0-babeld-598309c9
    amazon-ebs: # github.com:22 SSH-2.0-babeld-598309c9
    amazon-ebs: # github.com:22 SSH-2.0-babeld-598309c9
    amazon-ebs: changed: [default] => (item=github.com)
    amazon-ebs:
    amazon-ebs: TASK [php : Download composer] *************************************************
    amazon-ebs: changed: [default]
    amazon-ebs:
    amazon-ebs: TASK [php : Install composer] **************************************************
    amazon-ebs: changed: [default] => (item=php /tmp/installer.php)
    amazon-ebs: changed: [default] => (item=mv composer.phar /usr/local/bin/composer)
    amazon-ebs:
    amazon-ebs: TASK [nginx : Install a list of packages for nginx] ****************************
    amazon-ebs: changed: [default]
    amazon-ebs:
    amazon-ebs: TASK [nginx : Ansible delete file example] *************************************
    amazon-ebs: changed: [default]
    amazon-ebs:
    amazon-ebs: TASK [nginx : Copy the nginx conf file] ****************************************
    amazon-ebs: changed: [default]
    amazon-ebs:
    amazon-ebs: TASK [nginx : Enable service nginx, and not touch the state] *******************
    amazon-ebs: ok: [default]
    amazon-ebs:
    amazon-ebs: RUNNING HANDLER [php : restart phpfpm] *****************************************
    amazon-ebs: changed: [default]
    amazon-ebs:
    amazon-ebs: RUNNING HANDLER [nginx : restart nginx] ****************************************
    amazon-ebs: changed: [default]
    amazon-ebs:
    amazon-ebs: PLAY RECAP *********************************************************************
    amazon-ebs: default                    : ok=23   changed=18   unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
    amazon-ebs:
==> amazon-ebs: Stopping the source instance...
    amazon-ebs: Stopping instance
==> amazon-ebs: Waiting for the instance to stop...
==> amazon-ebs: Creating AMI php-7.1.30-1563261477 from instance i-00cc462600b73ebc7
    amazon-ebs: AMI: ami-03eb7183d07f30fb2
==> amazon-ebs: Waiting for AMI to become ready...
==> amazon-ebs: Terminating the source AWS instance...
==> amazon-ebs: Cleaning up any extra volumes...
==> amazon-ebs: No volumes to clean up, skipping
==> amazon-ebs: Deleting temporary security group...
==> amazon-ebs: Deleting temporary keypair...
Build 'amazon-ebs' finished.

==> Builds finished. The artifacts of successful builds are:
--> amazon-ebs: AMIs were created:
us-west-2: ami-03eb7183d07f30fb2
```

