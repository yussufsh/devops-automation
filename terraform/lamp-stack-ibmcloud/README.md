# Deploy a LAMP stack using Terraform on IBM Cloud VPC 

Deploy a Linux Apache MariaDB PHP (LAMP) stack on Ubuntu 18.04 ppc64le running in IBM Cloud VPC

## Prerequisites 

1. Terraform = 0.11.14 
2. IBM Cloud Terraform Provider = 0.20.0 
3. IBM Cloud API Key with authorization to provision in IBM Cloud VPC and IBM Cloud Block Storage for VPC 

## Overview

This deployment provisions:
  1. a Linux Ubuntu ppc64le VM server on IBM Cloud VPC 
  3. Creates a 200GB Block Storage for VPC  
  4. Creates a new ssh key to login 
  5. Opens Ports 80, 443 in VPC Security Group port to access web page 
  6. Opens Ports 22 to access SSH console
  7. Sets up LAMP packages and starts services
  8. MariaDB db is mounted to /mnt/block-storage/mysql 
  9. WebPage HTML files are mounted to /mnt/block-storage/html 

After install you can access the default web page of Ubuntu VM by IP:

    https://<IP>/  

To validate MariaDB successful connection:  

    https://<IP>/todo_list.php 

For information on system run:  
  
    https://<IP>/info.php 

To run the example, you will need to:

1. Clone this Git repository
2. [Download and configure](https://github.com/IBM-Cloud/terraform-provider-ibm) the IBM Cloud Terraform provider (minimally v0.20.0 or later)
3. Obtain your [IBM Cloud API key](https://cloud.ibm.com) (needed for step #4)
4. Update the variables.tf file to suit your needs

### Add your own web page
  1. Modify ./scripts/add\_web\__pages.sh and copy your own /var/www/html project directory 
  2. Modify ./scripts/setup\_db.sh to point to your own db directory 

## Provision Environment in IBM Cloud with terraform
Next, you can run the example by invoking...

The planning phase (validates the Terraform configuration)

```shell
terraform init
terraform plan
```

The apply phase (provisions the infrastructure)

```shell
terraform apply
```

The destroy phase (deletes the infrastructure)

```shell
terraform destroy
```



