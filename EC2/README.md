# Amazon Elastic Compute Cloud - EC2 ☁️

**EC2** é um serviço da **Amazon Web Services** que oferece capacidade de computação escalável na nuvem, 
podendo ser criadas a partir de instâncias (instalar um software, configurar definições) e criar uma AMI a partir dela. <br>
* **AMI - Amazon Machine Image** : Imagem de uma máquina virtual pré configurada.
## Diagrama Virtual Private Cloud - VPC
![ec2-vpc](https://github.com/user-attachments/assets/7a4a070b-e25f-4b1b-a276-5037773a9ab7)
<br>
### 🔹 Parte superior:
* Há uma VPC contendo um Servidor Windows protegido por um Security Group. <br>
* O servidor tem associada uma chave pública (Public Key). <br>
* A porta 22 está aberta, permitindo conexões SSH. <br>
* Um usuário externo (mostrado com um ícone de pessoa) usa a chave privada (Private Key) correspondente para se conectar ao servidor via SSH, autenticando o acesso de forma segura.

### 🔹 Parte inferior:
* Representa outra VPC com um Servidor Windows também protegido por um Security Group.
* Este servidor possui uma chave pública (Public Key) associada.
* A porta 3389 está aberta, permitindo conexões via Remote Desktop (RDP).
* O usuário externo usa novamente uma chave privada (Private Key) para se autenticar e acessar o servidor por RDP.

## [Documentação Amazon Elastic Compute Cloud - EC2 🦋](https://docs.aws.amazon.com/pt_br/AWSEC2/latest/UserGuide/EC2_GetStarted.html)
