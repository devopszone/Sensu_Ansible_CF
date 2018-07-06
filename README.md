# Sensu_Ansible_CF
This repository contains the cloud formation template to install and configure Sensu server components, Sensu client , plugins and checks for system and  Cloud.
Sensu-Server and it's dependencies on RHEL in AWS
This Cloud Formation template allows you to deploy an instance of Sensu-server and it's components like (sensu-api,sensu-client,uchiwa and Redis)on a Linux RHEL 7 VM. This will Template deploy Ec2 instance in AWS Oregon Region by using default VPC and default security groups. The Sensu-server is configured with system level checks,container checks, redis checks and cloud checks. 

# I. Deploy Sensu-server VM using AWS Cloud Formation
   If you have AWS subscription already Configure AWS-Cli on you local machine then execute the below command on terminal.

 > aws cloudformation deploy --template <path/of/template/file/cf_sensu.json> --stack-name <stackname> --parameter-overrides SSHKey=  <sshkey_pair_name> Sit back and relax. 

In above Command provide the path for template(cf_sensu.json) and provide SSH keypair name which is already available in your region.
  
  If you are not Configure AWS Cli, open AWS console in browser and access Cloud Formation and then click on > create stack 
   then browse your template file , then > provide stack name , then select ssh_keypair. 
Access Uchiwa dashboard at http://<ipaddress>:8080
 
# II. Deploy Sensu-server VM using Ansible.

If You have already Running VM with ansible Configured, then clone this Git Repo and execute command like
> ansible-playbook setup.yml -i <inventory file> for sensu-server and client.
> ansible-playbook setup_client.yml -i <inventory file> for sensu-client only.
Access Uchiwa dashboard at http://<ipaddress>:8080
   
# III. Deploy Sensu-server/client VM using Shell Script.

If You have fresh VM then execute the below command 

curl https://raw.githubusercontent.com/devopszone/sensu_install/master/install_sensu.sh | bash -s

Access Uchiwa dashboard at http://<ipaddress>:8080
