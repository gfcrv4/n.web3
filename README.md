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
