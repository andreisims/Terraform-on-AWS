# Terraform on AWS
A simple project on how to use Terraform to create infrastructure on AWS. This will be an EC2 instance that has Jenkins pre-installed. 
## Requirements
<li>an AWS account</li>
<li>an AWS admin user</li>
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
