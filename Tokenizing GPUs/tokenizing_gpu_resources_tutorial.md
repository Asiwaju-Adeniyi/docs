# Writing a Smart Contract to Monetize Idle GPU Resources in a Blockchain Marketplace

## Step 1: Benchmark the GPU
Write a script to benchmark the GPU:
```python
import torch
def benchmark_gpu():
    start_time = time.time()
    # Example workload: Matrix multiplication on GPU
    a = torch.rand((10000, 10000)).cuda()
    b = torch.rand((10000, 10000)).cuda()
    result = torch.matmul(a, b)
    end_time = time.time()
    return end_time - start_time
benchmark_score = benchmark_gpu()
```
Store the benchmark score on the blockchain using a smart contract.

## Step 2: Mint a GPU Token
Deploy a smart contract to mint tokens:
```solidity
contract GPUResourceToken {
    struct GPU {
        string gpuID;
        uint256 benchmarkScore;
        address owner;
    }
    mapping(uint256 => GPU) public gpuTokens;
    function mintToken(string memory gpuID, uint256 benchmarkScore) public {
        uint256 tokenID = uint256(keccak256(abi.encodePacked(gpuID, block.timestamp)));
        gpuTokens[tokenID] = GPU(gpuID, benchmarkScore, msg.sender);
    }
}
```

## Step 3: Build the Marketplace
Create a listing contract:
```solidity
contract GPUMarketplace {
    struct Listing {
        uint256 tokenID;
        uint256 pricePerHour;
        address renter;
    }
    mapping(uint256 => Listing) public listings;
    function listToken(uint256 tokenID, uint256 pricePerHour) public {
        listings[tokenID] = Listing(tokenID, pricePerHour, address(0));
    }
    function rentToken(uint256 tokenID) public payable {
        require(msg.value == listings[tokenID].pricePerHour, "Incorrect payment");
        listings[tokenID].renter = msg.sender;
    }
}
```

## Step 4: Deploy and Test
Deploy the contracts to a testnet (e.g., Ethereum Goerli or Polygon Mumbai).
Interact with the smart contracts via Remix or a custom front-end using Web3.js.

## Step 5: Build a Front-End
Use React.js to build a UI for users to benchmark GPUs, mint tokens, and interact with the marketplace.