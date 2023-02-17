# Install on the AWS myEC2 instance
- Reference:
Terraform installation Tutorial URL: https://www.devopsroles.com/how-to-install-terraform-on-linux/
- Create myEC2 instance using terraform template:
 https://linoxide.com/linux-how-to/how-to-install-terraform-on-centos-ubuntu/

# Installation of Terraform on AWS
- Install and run Terraform
```
$ sudo yum install wget unzip
$ wget https://releases.hashicorp.com/terraform/0.12.16/terraform_0.12.16_linux_amd64.zip
$ sudo unzip ./terraform_0.12.16_linux_amd64.zip -d /usr/local/bin/
$ terraform -v

mkdir terraform    # create folder
cd terraform

nano main.tf       # create terraform script


terraform init     # Initialize and run Terraform
terraform plan     # Dry run before you apply
terraform apply    # Start create and Enter Value: yes   to confirm
terraform destroy  # Destroy and Enter Value: yes        to confirm
```
- Status: Testing complete

## Usage
terraform -> main.tf -> owners   # you need to change the account id to yours
```
> aws sts get-caller-identity
```
- Run terraform
``` cd ../terraform `
 > terraform init; terraform plan; terraform apply -auto-approve    #it will run without typing 'yes' 
 > terraform destroy -auto-approve      # Destory
```        
- Go to AMIs in aws -> deregister   To remove the AMI
```
> aws ec2 deregister-image --image-id <image-id. (which is given by packer)
Go to Snapshots and remove the related one that Terraform created  #This should be done by manually.
aws ec2 delete-snapshot --snapshot-id <snapshot-id> (take from aws console)
```
## Demo URL: https://github.com/aleti-pavan/packer-ansible-terraform-demo/tree/master/packer
