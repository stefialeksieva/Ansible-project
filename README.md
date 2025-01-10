# Ansible-project

Hello, this is simple/example code for AWS and Ansible. 

There are tree Ansible yml playbooks: 
- ubuntu-creation.yml
- terminate-ec2.yml
- ec2-creation-project.yml

I found a bug in Ubuntu & AWS AMI, which lead me to implement the same code using Red Hat AMI, so that I can submit code for the task, in case I wasn't able to fix it.

With the `ubuntu-creation.yml` - the Ansible playbook is reading the variables, configuring the security group and creating 3 brand new ec2 instances in AWS account; After that, there are tasks to configure the instances as per the task.

With the `terminate-ec2.yml` - the Ansible playbook is reading the variables, terminating the instances and removing the security group which were created with creation-ec2.yml.

With the `ec2-creation-project.yml` - is the same as `ubuntu-creation.yml` but with Amazon Linux 2023 (Red Hat destribution).

 _**Note:** Changes can be applied, to improve security, for example: if you have private network -> the security group could be configured better. In addition, I had an idea to imporve the functions and add ssl configuration but I didn't have time due to the issues with the ssh connection between Ansible and new instances with Ununtu 24.04._

I am using my AWS test account, which is only for personal tests and examples. 
Ansible and git are installed on the ec2 instance and you can clone the repository there in order to have the files and execute them with ansible-playbook.


## Clone repo

```bash
gh repo clone stefialeksieva/Ansible-project
```

## Ways of working

Navigate in the folder Ansible-project once you cloned the repository

```bash
cd Ansible-project
```

Executing the playbook `ubuntu-creation.yml`

```bash
ansible-playbook ubuntu-creation.yml -e "ansible_user=ubuntu" --private-key=/home/ubuntu/ansible-key-rsa
```


Checking in AWS Console the instance was created successfully:

![image](https://github.com/user-attachments/assets/b9470e14-f31c-4354-a977-613e4032f5f3)

Executing the playbook `terminate-ec2.yml`

```bash
ansible-playbook terminate-ec2.yml -e "ansible_user=ubuntu" --private-key=/home/ubuntu/ansible-key-rsa
```

