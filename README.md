# Terraform on AWS
A simple project on how to use Terraform to create infrastructure on AWS. This will be an EC2 instance that has Jenkins pre-installed. 
## Requirements
<li>an AWS account</li>
<li>an AWS admin user (the default login credentials)</li>
<li>AWS CLI</li>
<li>Visual Studio Code</li>
<li>Notepad or Excel (for documentation)</li>

### 1. AWS CLI
<li>download and install AWS CLI on your pc</li>

![Image](https://github.com/user-attachments/assets/821ff715-7308-40cc-9ec0-3298725a45be)

![Image](https://github.com/user-attachments/assets/58d04bc0-5fbf-48ca-9ac3-49ceed8f2964)

![Image](https://github.com/user-attachments/assets/d41d10fb-97a6-4db7-9b95-e8bf150383e0)
<li>open command prompt and enter 'aws configure'</li>

![Image](https://github.com/user-attachments/assets/066353d8-73af-4344-a9df-94eb1061b596)
<li>we will aunthenticate to AWS by entering your access key: AWS> Users> create access key</li>

![Image](https://github.com/user-attachments/assets/b0394ae8-4468-4568-a1b7-2a7502bcc433)
<li>the access key is your username and the secret access key is your password</li>
<li>copy Access Key and paste at cmd prompt (press enter) now enter the secret access key.</li>
<li>confirm/select region name. accept default output format.</li>

![Image](https://github.com/user-attachments/assets/71018f5c-8bd8-4f2c-941e-e607ac81acab)
<li>this has authenticated your local windows machine to AWS. so any AWS command performed locally will be executed on your AWS account.</li>
<li>enter aws sts get-caller-identity. sts is the secure token service.</li>

![Image](https://github.com/user-attachments/assets/4a781d6f-4e18-4216-a326-a674d444733f)
<li>info can be confirmed on AWS. select the user/account in the upper-right corner to compare the information.</li>

![Image](https://github.com/user-attachments/assets/6f91fa15-e509-4eab-ba59-46bb802e26ef)
### 2. Clone repo locally using Git Bash
fork <a href="https://github.com/asecurityguru/terraform-ec2-jenkins-aws-k8s-infra-creation.git">repo</a> into your git account. I have already done this.

![Image](https://github.com/user-attachments/assets/68b7b427-2acb-4def-9761-a359f72d837c)
<li>this repo contains all the files that we will be using for this demonstration.</li>
<li>I created a new folder on my local machine and created folder for the repo. open the folder and right-click Git Bash here.</li>

![Image](https://github.com/user-attachments/assets/21c8c277-f285-4a5b-a7f8-8a86ecc96bdc)
<li>now clone into the repo: git clone https://github.com/andreisims/terraform-ec2-jenkins-aws-k8s-infra-creation.git</li>

![Image](https://github.com/user-attachments/assets/8d38bce5-658a-4881-8c37-a998aa6cbd14)
<li>repo files now show locally</li>

![Image](https://github.com/user-attachments/assets/557e50c8-c4ef-4255-bf00-910ad7aad472)
### 3. Visual Studio
<li>open Terraform repo in Visual Studio. file> open folder> and locate the folder where cloned repo is> select folder</li>

![Image](https://github.com/user-attachments/assets/6ff4f1a7-c28b-4846-bfcd-2690f7396975)
<li>Vars folder stores all the variable files. install_jenkins.sh is a shell script file to automate the installation and setup of Jenkins</li>

![Image](https://github.com/user-attachments/assets/62d7c354-71cf-41c7-a791-46a68161e853)
<li>main.tf contains entire script to create EC2 instance. the primary file searched by terraform to create the infrastructure. install_jenkins.sh is referenced in it</li>

![Image](https://github.com/user-attachments/assets/cce2e6c1-2514-4e9d-84f5-dc32d8a15577)
<li>outputs.tf is used to store outputs from infrastructure creation</li>

![Image](https://github.com/user-attachments/assets/88fd1580-eaee-400a-850e-94ca1b569df8)
### 4. Variable file and Key Pair
<li>update the file with your VPC ID. search for vpc on AWS console> VPC dashboard> Your VPCs.
If you have more than one, the default VPC has the 172.31.0.0/16 CIDR block</li>
<li>this file is passed to the terraform script (terraform apply -var-file="vars/dev-west-2.tfvars")
on the AWS console. Be sure that your are in the same region as the script: aws_region = "us-west-2"</li>

![Image](https://github.com/user-attachments/assets/b623284e-a47b-499f-9c67-27a7925b1082)
<li>for key pair, sign into AWS console. go to the EC2 dashboard> launch instance> create new key pair> name it and copy it to notepad</li>
<li>select RSA key pair type and .ppk as file format> select create key pair</li>

![Image](https://github.com/user-attachments/assets/e1e5ae75-076b-45f2-9dda-cb966b3ff566)
<li>key pair is downloaded to your pc. go to file location where is has been downloaded. copy and paste file into the cloned repo</li>

![Image](https://github.com/user-attachments/assets/ab16a33b-2609-4fac-baa6-3ca381c40772)

![Image](https://github.com/user-attachments/assets/560caf37-3d89-459f-9feb-6f601696ee72)
<li>take the file name that you copied to notepad and update the key_name section in the dev-west-2.tfvars file</li>

![Image](https://github.com/user-attachments/assets/7be04cc9-38c2-4f74-814e-942e0025db10)
### 5. Run Terraform script to create AWS infrastructure
<li>the steps are outlined in the README.md file. open new terminal in VS Code</li>

![Image](https://github.com/user-attachments/assets/91d0ff80-11ba-4140-85b7-5ce7be930c26)
<li>now copy and paste the code from the README.md file in the terminal according to the steps</li>

#### Step 1: Initialize Terraform
<li>terraform init</li>

![Image](https://github.com/user-attachments/assets/d3c5982a-ad37-4d0b-9f04-928251dd142a)

![Image](https://github.com/user-attachments/assets/2213dccd-1bb2-4675-967e-10e2bbf70e94)

<li>its initializing the backend, and provider plugins. also created a new .terraform directory</li>

![Image](https://github.com/user-attachments/assets/d1b6882b-ee0d-42f5-a429-a8e0255f1fca)
#### Step 2: Plan Resources
<li>terraform plan -var-file="vars/dev-west-2.tfvars"</li>

#### Step 3: Apply Resources
<li>terraform apply -var-file="vars/dev-west-2.tfvars"</li>

![Image](https://github.com/user-attachments/assets/e0b94327-0a7b-46e5-9703-7f0bb96d8d2b)
<li>after running this script, let's go back to the AWS EC2 dashboard to see the new instance that was created</li>

![Image](https://github.com/user-attachments/assets/170873e1-444d-40b7-a783-9a458e851462)

![Image](https://github.com/user-attachments/assets/603c58fe-ffe8-407d-817f-576dedae0399)
<li>open the Public IPv4 DNS address, remove the 's' from https since there is not a certificate and add port 8081</li>

![Image](https://github.com/user-attachments/assets/1b78b9a0-6b83-44f2-b501-94dc1cca382a)
# SUCCESS!
For the next phase of this project, we will integrate SonarCloud into the pipeline to scan a vulnerable application




