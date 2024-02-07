# Taiko - Alpha-6 Katla

[Official documentation](https://taiko.xyz/docs/guides/run-a-node) </br>

#### System requirements: </br>

#### Minimum: </br>
CPU: 4 Core </br>
RAM: 8 Gb </br>
SSD: 50 Gb SSD (For testing) </br>
OS: Ubuntu 20.04 LTS </br>

#### Recommended: </br>
CPU: 8/16 Core </br>
RAM: 32 Gb </br>
SSD: 50 Gb SSD (For testing) </br>
OS: Ubuntu 20.04 LTS </br>


# Installation of the Taiko node with Docker.
#### 1. Required packages installation:
```
sudo apt update && apt upgrade -y
```
```
sudo apt install git-all -y
```
#### 2. Installing docker and docker compose:
```
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
curl -SL https://github.com/docker/compose/releases/download/v2.16.0/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```
#### 3. Clone simple-taiko-node:
```
git clone https://github.com/taikoxyz/simple-taiko-node.git
cd simple-taiko-node
```
#### 4. Copy the .env.sample to a new file .env:
```
cp .env.sample .env
```
#### 5. Next, open the .env file in your preferred text editor:
```
nano .env
```
At the current stage, you need to make changes to the .env file </br>
L1_ENDPOINT_HTTP </br>
L1_ENDPOINT_WS </br>

#### 6. To receive HTTPS and WS, you need to register at [Blockpi](https://blockpi.io/)
#### 7. We create an application:
In the upper right corner, click +create app button. </br>
In the window that opens, enter the name, CHAIN - Ethereum, NetWork - Holesky. </br>
Save the entered data, click create app button. </br>
#### 8. On the right side of the newly created project, click on the VIEW KEY button. </br>
We copy HTTPS and WSS, and paste it into the file, from step 5 of the instruction.
#### 9. Enable your node as a prover (optional): </br>
In the ".env" file, we make additional adjustments: </br>
ENABLE_PROVER -  change the value to "true" </br>
Set L1_PROVER_PRIVATE_KEY - Metamask wallet secret key </br>
SGX_RAIKO_HOST= -We write SGX_RAIKO_HOST our own </br>
ENABLE_PROPOSER - change the value to "true" </br>
Set L1_PROPOSER_PRIVATE_KEY - Metamask wallet secret key </br>

#### 10. Save the file ".env" Ctrl+X, Ctrl+Y, Enter.
#### 11. For Prover to work correctly, you need to have a certain amount of Eth coins in the Sepolia network on your wallet. </br>
You can use the [faucet](https://stakely.io/en/faucet/ethereum-holesky-testnet-eth)</br>
#### 12. Start a node:
```
docker compose up -d
```

At the moment, only the router is working normally, in order to start the PROVER, you need tokens and an old processor with SGX.

# Useful commands:
#### Since the node is raised using docker compose, all commands are executed from the folder in which it is located, by default /root/simple-taiko-node/
```
cd /root/simple-taiko-node/
```
#### Stop a node:
```
docker compose down
```
#### Remove a node:
```
docker compose down -v
rm -f .env
```
#### Update a node:
```
docker compose pull
```
#### View the node's logs:
```
docker compose logs -f
```
#### View the node's status dashboard:
```
http://localhost:3000/d/L2ExecutionEngine/l2-execution-engine-overview?orgId=1&refresh=10s
```

This is the last phase of the testnet, I do not advise you to skip it.
