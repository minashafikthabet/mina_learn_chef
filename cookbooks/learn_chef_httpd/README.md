# learn_chef_httpd
This basic cookbook configures Apache on Red Hat Enterprise Linux.

## How to use server and node

Follow direct steps in https://learn.chef.io/tutorials/local-development/rhel/virtualbox/apply-a-cookbook/ 
 
#### Navigate to root folder 
`cd {path-to-project}`

#### bring machine up 
`vagrant up`

#### Add hosts to hosts file 
`Add-Content C:\Windows\System32\drivers\etc\hosts "10.1.1.33 chef-server.test"`

#### fetch and verify the SSL certificate from your Chef server
`knife ssl fetch`

`knife ssl check`

#### Upload a cookbook to Chef server
`knife cookbook upload learn_chef_httpd`

#### bootstrap node 
##### Get your node's connection details
`vagrant ssh-config node1-centos`

##### bootstrap command
`knife bootstrap {machine-ip} --ssh-port 22 --ssh-user vagrant --sudo --identity-file {pem-file path}/private_key --node-name node1-centos --run-list 'recipe[learn_chef_httpd]'`

Node node1-centos exists, overwrite it? (Y/N) y
Client node1-centos exists, overwrite it? (Y/N) y

#### Login to machines 
`knife ssh {machine-ip} --ssh-port 22 'sudo chef-client' --manual-list --ssh-user vagrant --identity-file {pem-file path}/private_key --node-name node1-centos`

### How to develop 
#### Navigate to current folder 
`cd {path-to-project}\cookbooks\learn_chef_httpd`
N.B. 
`when using windows` make sure you named the folder sith shot names and try to add the project in the root disk vagrant have problems with long file pathes in windows 

#### Step 1 Create the Test Kitchen instance
`kitchen create`

#### Step 2 Apply the learn_chef_httpd cookbook to your Test Kitchen instance

`kitchen list`

`berks install`

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


### Faced Problems 
If you faced any issue while installation specially connection errror login to server 
`sudo chef-server-ctl cleanse`

## Prepare Enviroment 
###Windows 
Check reference 1

##REFERENCES
1. `https://learn.chef.io/tutorials/learn-the-basics/rhel/virtualbox/set-up-a-machine-to-manage/`
