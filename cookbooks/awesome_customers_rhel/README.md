# awesome_customers_rhel

## How to use 
### Bringing machine up 
Navigate to root 
`vagrant up`


### Use Berkshelf to install your dependencies
`berks install`

### Use Berkshelf to upload the cookbooks to the Chef server
Upload your cookbooks to the Chef server.
`berks upload --no-ssl-verify`


### Verify that the upload process succeeded
To prove that the cookbooks uploaded successfully, run 
`knife cookbook list`

Navigate to root 
`knife bootstrap 192.168.64.149 --ssh-port 22 --ssh-user vagrant --sudo --identity-file E:/SourceCode/Assignment/.vagrant/machines/node1-centos/virtualbox/private_key --node-name node1-centos --run-list 'recipe[awesome_customers_rhel]'`

Node node1-centos exists, overwrite it? (Y/N) y
Client node1-centos exists, overwrite it? (Y/N) y


## Develop locally 
### Apply the awesome_customers_rhel cookbook on a Test Kitchen instance
`kitchen list`

`berks install`

every time you do change you should call  
`kitchen converge`

`kitchen login`

## How to Develop Simillar project  
Followed the Tutorial in `https://learn.chef.io/manage-a-web-app/`
Choose `Red Hat Enterprise Linux >>`
then Follow the steps 



## References 
https://learn.chef.io/manage-a-web-app/rhel/configure-php/
