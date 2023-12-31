# Linux VM install GUI Desktop XFCE

## 1. (Option1) Create in Azure a Linux Ubuntu server VM (Spot instance)


## 1. (Option2) Create in AWS a Linux Ubuntu server VM (Spot instance)

![image](https://github.com/luiscoco/Linux_install_XFCE_GUI_Desktop/assets/32194879/80872937-4e03-463a-83ae-a271343ac1ce)

![image](https://github.com/luiscoco/Linux_install_XFCE_GUI_Desktop/assets/32194879/9173ff09-b40b-45db-806c-da7044c51cec)

![image](https://github.com/luiscoco/Linux_install_XFCE_GUI_Desktop/assets/32194879/b94cd032-a596-4160-9efd-65924670666d)

Move the private key *.pem file from Download folder to .ssh folder 

![image](https://github.com/luiscoco/Linux_install_XFCE_GUI_Desktop/assets/32194879/e4327c04-dff3-498e-b417-cbd488406387)

After creating the ssh key pair we select it

![image](https://github.com/luiscoco/Linux_install_XFCE_GUI_Desktop/assets/32194879/c86479ba-8bc7-4e44-9687-9060c95c70da)

Now we set the networking options. We only have to include a new inbound rule for RDP 3389 port

![image](https://github.com/luiscoco/Linux_install_XFCE_GUI_Desktop/assets/32194879/ecb0a621-fdd9-42ce-a774-a1cea9ad2a56)

![image](https://github.com/luiscoco/Linux_install_XFCE_GUI_Desktop/assets/32194879/8097586b-0f9c-4a07-b197-2e7fb20beb46)

Now we set the VM hard disk capacity to 30 Gb because is free

![image](https://github.com/luiscoco/Linux_install_XFCE_GUI_Desktop/assets/32194879/21591d34-5ad9-4391-acf3-8f580dea4c07)

Finally we request a Spot instance for reducing the VM cost

![image](https://github.com/luiscoco/Linux_install_XFCE_GUI_Desktop/assets/32194879/c5df0234-26d7-4c98-b004-da07d1834059)

Then we create the Linux VM pressing the "Launch Instance" button

![image](https://github.com/luiscoco/Linux_install_XFCE_GUI_Desktop/assets/32194879/e2bec630-8251-429e-8c39-6fb0a46ed468)

We check the VM was created, we press in the VM id link

![image](https://github.com/luiscoco/Linux_install_XFCE_GUI_Desktop/assets/32194879/4935341d-ce34-4f2a-a831-4e0472d818c9)

See the new VM in the instances list

![image](https://github.com/luiscoco/Linux_install_XFCE_GUI_Desktop/assets/32194879/04049b83-5f7a-47ea-8fc1-464d596c9ce7)

Select the instance and press the "Connect" button

![image](https://github.com/luiscoco/Linux_install_XFCE_GUI_Desktop/assets/32194879/235890bd-9643-459f-86b2-667272d10e58)

For connecting to the Linux VM via SSH type press the "ssh client" tab and copy the command

![image](https://github.com/luiscoco/Linux_install_XFCE_GUI_Desktop/assets/32194879/99da5e9b-fb4a-469d-9de3-f5faed8b97a4)

In our case we placed the private key file *.pem in the .ssh path, then for connecting to the Linux VM we have to type the command:

```
ssh -i C:/Users/LEnriquez/.ssh/mynewxfceawskeypair.pem ubuntu@ec2-35-180-41-178.eu-west-3.compute.amazonaws.com
```

![image](https://github.com/luiscoco/Linux_install_XFCE_GUI_Desktop/assets/32194879/10c8685a-67b4-41d5-8e98-54e6ab2e743b)

You can see we enter in our Linux VM with the user "ubuntu"

Edit the VM Security Group to add two new outbound for the protocols "HTTP" and "HTTPS" in order to access to Internet from the Linux VM

![image](https://github.com/luiscoco/Linux_install_XFCE_GUI_Desktop/assets/32194879/39b74110-2c30-47a2-9ebc-6ee504269d93)

![image](https://github.com/luiscoco/Linux_install_XFCE_GUI_Desktop/assets/32194879/bacc76eb-1bc2-4e45-853c-d12d6a889fb2)

Do not forget to reboot the EC2 instance to take efect the new outbound rules for "HTTP" and "HTTPS"

![image](https://github.com/luiscoco/Linux_install_XFCE_GUI_Desktop/assets/32194879/889cb1e2-af40-4a1d-8173-45d0fff5a695)

## 2. Install XFCE (GUI Desktop for Ubuntu Linux VM)

https://www.xfce.org/

**IMPORTANT NOTE**: top 10 best Linux desktop environments

https://tecadmin.net/best-linux-desktop-environments/

Run this commands to install xfce in the Linux VM

```
sudo apt-get update

sudo DEBIAN_FRONTEND=noninteractive apt-get -y install xfce4

sudo apt install xfce4-session
```

## 3. Install and configure XRDP to use Remote Desktop with Ubuntu

https://learn.microsoft.com/en-us/azure/virtual-machines/linux/use-remote-desktop?tabs=azure-cli

Run this commands to install and configure xrdp in your Linux VM:

```
sudo apt-get -y install xrdp

sudo systemctl enable xrdp

sudo adduser xrdp ssl-cert

echo xfce4-session >~/.xsession

sudo service xrdp restart

sudo passwd azureuser
```

## 4. Be user you open the RDP port 3389

For Azure Linux VM run the command:

```
az vm open-port --resource-group myResourceGroup --name myVM --port 3389
```

For AWS Linux VM open the 3389 port for RDP when configuring/creating the new Linux VM instance


## 5. Connect to the Linux VM with Remote Desktop Connection

Set the Linux VM **Public IP address**

Set the Linux VM **username**

For Azure see this picture

For AWS see this picture

![image](https://github.com/luiscoco/Linux_install_XFCE_GUI_Desktop/assets/32194879/0888a20e-0898-4f60-b70f-f5b58150ae8e)

![image](https://github.com/luiscoco/Linux_install_XFCE_GUI_Desktop/assets/32194879/a2a8c409-48cb-44dd-84af-88ef8acd5689)

![image](https://github.com/luiscoco/Linux_install_XFCE_GUI_Desktop/assets/32194879/42853bb2-6808-4da0-8e5e-908d76fcf7d7)

![image](https://github.com/luiscoco/Linux_install_XFCE_GUI_Desktop/assets/32194879/a0fdf824-1cf7-4fe5-840d-c660221c6c89)

## 6. How to install VSCode

Open a Terminal Emulator window and run the following commands to install the VSCode application

![image](https://github.com/luiscoco/Azure_VM_Ubuntu_with_GUI_Desktop/assets/32194879/98e76ee1-5832-4536-9692-babdce81e9ad)

```bash
sudo apt install software-properties-common apt-transport-https wget
wget -q https://packages.microsoft.com/keys/microsoft.asc -O- | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main"
sudo apt update
sudo apt install code
```

For accessing VSCode type the command:

```
code
```

## 7. How to install Google Chrome

```bash
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb
```

## 8. How to install .NET 8

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb

sudo apt update

sudo snap install dotnet-sdk --classic

dotnet --version
```

## 9. Install Docker

To install Docker Desktop on a Linux virtual machine, you can follow these general steps. 

Keep in mind that the commands might vary slightly depending on your Linux distribution.

Update Package Index:

```
sudo apt update
```

If you're using a distribution other than Ubuntu, replace apt with your package manager, such as yum for CentOS or dnf for Fedora.

### 9.1. Install dependencies:

```
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```

### 9.2. Add Docker's official GPG key:

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

### 9.3. Replace linux/ubuntu with your distribution if it's different.

Set up the stable repository:

```
echo "deb [signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

### 9.4. Adjust the distribution in the URL if needed.

Update the package index again:

```
sudo apt update
```

### 9.5. Install Docker Engine:

```
sudo apt install docker-ce docker-ce-cli containerd.io
```

### 9.6. Verify Docker installation:

```
sudo docker run hello-world
```

This command downloads a test image and runs a container. If everything is set up correctly, you'll see a "Hello from Docker!" message.


## 10. Install Portainer

Portainer is a great choice for managing Docker containers with a user-friendly interface. Here are the commands to install Portainer on your Linux virtual machine:

## 10.1 Create a Docker volume for Portainer data:

```
sudo docker volume create portainer_data
```

## 10.2. Run Portainer as a Docker container:

```
sudo docker run -d -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer
```

This command pulls the Portainer image from Docker Hub and starts a container named "portainer" with access to the Docker socket for managing containers. 

Portainer will be available on port 9000.

## 10.3. Access Portainer in your web browser:

Open your web browser and go to **http://localhost:9000** or replace localhost with the IP address of your virtual machine if you are accessing it remotely. 

You'll be prompted to set up an admin user and password.

![image](https://github.com/luiscoco/Linux_install_XFCE_GUI_Desktop/assets/32194879/5c9beb0f-99f3-4ce9-a617-049fd0715ba6)

## 11. Download and run a MongoDB docker container

Docker makes it pretty straightforward to run MongoDB in a container. Here's a basic guide to get you started:

### 11.1. Install Docker as explained in section 9. and then login:

Make sure you have Docker installed on your machine. You can download it from the official Docker website.

Let's try adding the group directly using the newgrp command:

```
newgrp docker
```

After running this command, try running docker login again:

```
docker login
```

### 11.2. Pull MongoDB Docker Image:

Open a terminal and run the following command to pull the official MongoDB image from Docker Hub:

```
docker pull mongo
```

![image](https://github.com/luiscoco/Linux_install_XFCE_GUI_Desktop/assets/32194879/e4af5621-4048-463f-9841-22763c194045)

### 11.3. Run MongoDB Container:

Once the image is downloaded, you can run a MongoDB container using the following command:

```
docker run -d -p 27017:27017 --name my-mongodb mongo
```

This command runs a detached (-d) MongoDB container, maps the host port 27017 to the container port 27017, and gives it a name (--name my-mongodb). You can change the name if you prefer.

![image](https://github.com/luiscoco/Linux_install_XFCE_GUI_Desktop/assets/32194879/557c0b97-ee09-441e-a606-6300d6f06869)

### 11.4. Access MongoDB Shell:

To access the MongoDB shell in the running container, use the following command:

```
sudo docker exec -it my-mongodb bash
```

Replace my-mongodb with the name you gave to your container.

![image](https://github.com/luiscoco/Linux_install_XFCE_GUI_Desktop/assets/32194879/c6cc324c-498f-44f3-bf4a-b667683607b0)

### 11.5. To stop and remove the MongoDB docker container

```
sudo docker stop my-mongodb
sudo docker rm my-mongodb
```

### 11.6. How to create a MongoDB database sample, with a collection and some documents

Once you have connected to your MongoDB container using the docker exec -it my-mongodb mongo command, you can create a new database, a collection, and insert some sample documents. Here's an example:

**Create a new database**:

```
use mydatabase
```

Replace mydatabase with the name you want for your new database.

**Create a new collection**:

```
db.createCollection("mycollection")
```

Replace mycollection with the name you want for your new collection.

**Insert some sample documents**:

```
db.mycollection.insertMany([
  { name: "John Doe", age: 30, city: "New York" },
  { name: "Jane Doe", age: 25, city: "San Francisco" },
  { name: "Bob Smith", age: 35, city: "Los Angeles" }
])
```

![image](https://github.com/luiscoco/Linux_install_XFCE_GUI_Desktop/assets/32194879/27f11579-999f-4b8d-975a-b8b263e3a30b)

## 12. Install Studio 3T for MongoDB








## 13. Install IntelliJ Community






## 14. Install Node.js






## 15. Install Angular CLI






## 16. 




