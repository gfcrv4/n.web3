# n8n.web3

### Usage
```
docker-compose up --build

```

Go to localhost:5678 and check

Script to check:


```
const { Web3 } = require('web3');

const web3 = new Web3("https://mainnet.infura.io/v3/fc4e8aa2367a4bd1a684391753d53986");

async function getTransactionCount(address) {
  try {
    const count = await web3.eth.getTransactionCount(address);
    return count;
  } catch (error) {
    console.error(error);
    return null;
  }
}

const results = [];

for (const item of $input.all()) {
  const transactionCount = await getTransactionCount(item.json.wallet_address);
  item.json.wallet_transactions = transactionCount;
  results.push(item);
}

return results;
```

Or you can import test workflow from workflows folder.


Open browser console and see results


___ 

docker-compose.yml old 

```
version: "3.7"

services:
  n8n:
    build:
      context: ./n8n
      dockerfile: Dockerfile
      args:
        N8N_VERSION: "1.84.3"
    container_name: n8n
    restart: always
    ports:
      - "0.0.0.0:5678:5678"
    environment:
      - N8N_HOST=x.pogorelyi.com
      - N8N_PORT=5678
      - WEBHOOK_URL=https://x.pogorelyi.com/
      - N8N_PROTOCOL=https
      - NODE_ENV=production
      - GENERIC_TIMEZONE=Europe/Berlin
      - NODE_FUNCTION_ALLOW_BUILTIN=https,crypto
      - NODE_FUNCTION_ALLOW_EXTERNAL=moment,lodash,web3,ccxt,ethers,axios,@clickhouse/client
    volumes:
      - n8n_data:/home/node/.n8n

volumes:
  n8n_data:
    external: true
```
