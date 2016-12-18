# learn_chef_httpd
This basic cookbook configures Apache on Red Hat Enterprise Linux.

## How to use 

Follow direct steps in https://learn.chef.io/tutorials/local-development/rhel/virtualbox/apply-a-cookbook/ 


### Setup 
#### Step 1 Create the Test Kitchen instance
`kitchen create`

#### Step 2 Apply the learn_chef_httpd cookbook to your Test Kitchen instance

`kitchen list`
`kitchen converge`

### Verify that your Test Kitchen instance is configured as expected (Step 5)
`kitchen exec -c 'curl localhost'`

### Delete the Test Kitchen instance (Step 6)
`kitchen destroy`


## How to Develop Simillar project  
Followed the Tutorial in https://learn.chef.io/tutorials/manage-a-node/
Choose `Red Hat Enterprise Linux >>`
Then `Vagrant and VirtualBox >>`

Followed the Tutorial in https://learn.chef.io/tutorials/local-development/
Choose `Red Hat Enterprise Linux >>`
Then `Vagrant and VirtualBox >>`


### Needed commands 
#### Login to machines 
`knife ssh {machine-ip} --ssh-port 22 'sudo chef-client' --manual-list --ssh-user vagrant --identity-file {pem-file path}/private_key --node-name node1-centos`

### bootstrap node 
`knife bootstrap {machine-ip} --ssh-port 22 --ssh-user vagrant --sudo --identity-file {pem-file path}/private_key --node-name node1-centos --run-list 'recipe[learn_chef_httpd]'`

Node node1-centos exists, overwrite it? (Y/N) y
Client node1-centos exists, overwrite it? (Y/N) y

### Faced Problems 
If you faced any issue while installation specially connection errror login to server 
`sudo chef-server-ctl cleanse`

## Prepare Enviroment 
###Windows 
Check reference 1

##REFERENCES
1. `https://learn.chef.io/tutorials/learn-the-basics/rhel/virtualbox/set-up-a-machine-to-manage/`
