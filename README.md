# Blockchain CA x14488478 #

### Deployed ERC20 token 'YURT' on the Ropsten test network ###
Contract Address: ```https://ropsten.etherscan.io/address/0x2688e753dA66C06Be63217Aa93A4b46C3997571d```

### Pre-requisites for running ###

 - Node.js installed
 - Docker installed
 - Github repo cloned locally
    
        git clone https://github.com/ryanbannon/BlockchainProject.git

### Configuring dependencies ###

Make sure you're in the BlockchainProject folder and install the necessary dependencies

    cd BlockchainProject 
    npm install

Before running the code locally, you must create the .env file containing the following variables

    INFURA_KEY=<infura key>
    OWNER_ADDRESS=<owner public key>
    OWNER_PRIVATE_KEY=<owner private key>
    CONTRACT_ADDRESS=0x2688e753dA66C06Be63217Aa93A4b46C3997571d
    account2=0xAb85032566e8bb73C20501C756cA4032592309cb

### Running and testing the Node application ###

Start the web server

    node handlers.js

**As the server is running in a terminal instance, open a separate terminal and use curl to complete the following tasks:**

Get the ERC20 token symbol name

    curl -get 'http://localhost:8090/symbol'

Get the ERC20 token total supply 

    curl -get 'http://localhost:8090/supply'

Transfer 50 YURT tokens to account2 defined in the .env file

    curl -get 'http://localhost:8090/transfer'

Distribute 5% of the remaining tokens in the owners account evenly amongst a list of supplied accounts

    curl -XPOST http://localhost:8090/distribute -H 'content-type: application/json' -d '{"addresses": ["0x9b14eeE99808BaB2a4C6492D37B4D771F75b7631", "0xe8a43eFC2CE385AbA7465101262b03B0d2489c43", "0x9ca3208d90Ce19f42F2e5FC435ADA5922cB34989", "0x1F4aB29bDe4fb3b29d40577c55a7Ae7c1F973351", "0x22aF8cf4dE24Cbb09D5D6DA6c6989E0e5315078a", "0xFcCE91F39E2C001ED59204A9f321Ce741975E7dd", "0x7A768244C32fB024B254acFbE2dFF59919b63898", "0x754c68d82DF83699aD2179927c3F9312FF5590e7", "0x40581B22EA850D3eC905A4D21f860A489b625d20", "0x3f4D34336a1357a19BeBb824166Ac12FAC5676B3"]}'

### Using Docker Containers ###

Pull down the image from dockerhub

    docker pull ryanbannon/blockchain

Run the image in docker

    docker run -p 41960:8090 --name blockchain -d ryanbannon/blockchain
    
**Use curl to complete the following tasks again:**

Get the ERC20 token symbol name

    curl -get 'http://localhost:41960/symbol'

Get the ERC20 token total supply 

    curl -get 'http://localhost:41960/supply'

Transfer 50 YURT tokens to account2 defined in the .env file

    curl -get 'http://localhost:41960/transfer'

Distribute 5% of the remaining tokens in the owners account evenly amongst a list of supplied accounts

    curl -XPOST http://localhost:41960/distribute -H 'content-type: application/json' -d '{"addresses": ["0x9b14eeE99808BaB2a4C6492D37B4D771F75b7631", "0xe8a43eFC2CE385AbA7465101262b03B0d2489c43", "0x9ca3208d90Ce19f42F2e5FC435ADA5922cB34989", "0x1F4aB29bDe4fb3b29d40577c55a7Ae7c1F973351", "0x22aF8cf4dE24Cbb09D5D6DA6c6989E0e5315078a", "0xFcCE91F39E2C001ED59204A9f321Ce741975E7dd", "0x7A768244C32fB024B254acFbE2dFF59919b63898", "0x754c68d82DF83699aD2179927c3F9312FF5590e7", "0x40581B22EA850D3eC905A4D21f860A489b625d20", "0x3f4D34336a1357a19BeBb824166Ac12FAC5676B3"]}'

### Stop the docker container ###

    docker stop blockchain