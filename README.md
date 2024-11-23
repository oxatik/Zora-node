# Zora node
The NFT marketplace protocol

![image](https://github.com/user-attachments/assets/0bb5c817-e89a-4365-9ea7-2d9a88e8addb)

# Zora: An Overview
ZORA is the NFT marketplace protocol working towards a new paradigm for creators. It enables the creation, curation, and collection of NFTs, and makes it possible for people to build their own markets around their work.
 In addition, ZORA also launched ZORA NETWORK, a Layer 2 network based on OP Stack. The network provides a faster and more efficient extension of Ethereum for artists, creators and the community, and will directly integrate all existing zora tools.
  Zora positions itself as a pillar of the NFT economy, providing a space where creativity and ownership are celebrated and preserved through the power of blockchain. Supported by major investors such as Coinbase Ventures and Haun Ventures, Zora has recently raised over $50 million, affirming its ambition to become the foundation for the future of digital media.
  
  ![image](https://github.com/user-attachments/assets/60094467-4d43-43b0-9251-41db6ddee4b9)

  
  # Prerequisites for Deploying a Zora Node
  Recommended Configuration

* Linux Ubuntu 22.04 / Docker
* Available storage space: 200 GB
* RAM: 16 GB

To host a Zora node, opt for a VPS 2 server. I have chosen Contabo for its reliability and performance, ideal for meeting the technical requirements of Zora.
To order your Contabo VPS server, you can click on https://contabo.com/en/
# Ethereum Mainnet API Key for the Zora Node
To prepare your environment for the installation of a Zora node, creating an Alchemy account and obtaining an API key for the Ethereum Mainnet are necessary.
Sign up on https://www.alchemy.com/ and verify your account via email.

![image](https://github.com/user-attachments/assets/384cc02b-1b73-4df1-8f6f-7fb069296c09)

Create a new application, name it, add a description, and select Ethereum Mainnet as the network.

![image](https://github.com/user-attachments/assets/fc9bb76d-1957-4f21-a4bf-1a421b1b9e8e)

Access your API keys in “View Key”; and copy your https key into a file. It will be requested during the execution of the Ansible script during the installation of your node.

![image](https://github.com/user-attachments/assets/44611f51-ceeb-4176-a349-f2cbd9f095cf)

# Installation of Essential Components
* Before delving into the installation of your node, it is crucial to update your VPS. To do so, simply execute the following command in your VPS terminal:
```bash
sudo apt-get update && sudo apt-get upgrade -y  
```
* Install the essential libraries to run your node:
```bash
sudo apt install curl build-essential git screen jq pkg-config libssl-dev libclang-dev ca-certificates gnupg lsb-release -y  
```
* Next, you will install Docker Compose on your machine
```bash
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo chmod a+r /etc/apt/keyrings/docker.gpg
  
```
*  Then proceed with the installation of Docker and its dependencies:
```bash
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose
  
```
# Downloading the Zora Folder
*  Clone the Conduit Github repository, the infrastructure that deployed the Zora node:
```bash
git clone https://github.com/conduitxyz/node.git  
```
# Node Installation
*  Now that your folder has been created, you can proceed with launching your node.
*  Navigate to the folder you just created:
```bash
cd node  
```
#  Initiate the download of the Zora mainnet folder:
```bash
./download-config.py zora-mainnet-0  
```
* Set a value for the CONDUIT_NETWORK variable to inform the node that you want to launch on the Zora network:
```bash
export CONDUIT_NETWORK=zora-mainnet-0  
```
* Enter your API key into your environment file so that your node can use it to operate. First, create your text file:
```bash
cp .env.example .env  
```
* Open your text file:
```bash
nano .env  
```
*  In your .env file, replace <HTTP://…> with your Alchemy account's API key.

* You can find your API key on your Alchemy account.
*  Close your text file by holding down CTRL+X, then press Y, and hit ENTER
# Node Launch
* Your folder is ready; you can now initiate the launch of your node.
* Create a new instance on your VPS so that your node can operate in the background:
```bash
screen -S zora  
```
This creates a background instance named ‘zora’
# Now, launch your node:
```bash
docker compose up --build  
```
To exit your instance, press CTRL+A+D.
Done, your node has been successfully launched!

![image](https://github.com/user-attachments/assets/74abd0af-4585-432d-8d2f-c40dcab184e8)

You can see that your node is active on the Alchemy site:

![image](https://github.com/user-attachments/assets/b1510fb1-11ba-43cf-bc0d-820e95e8ccb2)


To exit your instance, press CTRL+A+D.
* You can go back to your node’s instance to check its log:
```bash
screen -r zora  
```
# Learn more about The NFT marketplace protocol

https://zora.co/

https://x.com/zora

https://docs.zora.co/







