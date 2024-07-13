# n8n.web3

### Installation
### Install docker-compose

```
docker-compose up --build -d

# to get name of container get the last column of n8n cointaner
docker ps
docker exec -it -u root NAME_OF_YOUR_CONTAINER /bin/sh -c  "npm install -g web3"
```

Go to localhost:5678 and check

Script to check:


```
const { Web3 } = require('web3');

const web3 = new Web3("https://mainnet.infura.io/v3/fc4e8aa2367a4bd1a684391753d53986");
console.log("BLA")
web3.eth.getTransactionCount("0x6422Df9B4a20862a3b360439eE0feb7c8B974036")
.then(console.log);
```

Open browser console and see results
