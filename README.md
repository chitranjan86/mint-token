# mint-token
 a smart contract to create your own ERC20 token and deploy it using HardHat or Remix. Once deployed, you should be able to interact with it for your walk-through video. From your chosen tool, the contract owner should be able to mint tokens to a provided address and any user should be able to burn and transfer tokens.

# SimpleToken Smart Contract

This project demonstrates a simple Ethereum smart contract for creating and destroying tokens, along with mappings to track token balances for each address.

## Contract Overview

The `SimpleToken` contract allows for minting and burning tokens while maintaining a balance for each address. It also includes fallback and receive functions to prevent the contract from receiving Ether.

## Contract Details

- **Name**: SimpleToken
- **Symbol**: STK
- **Total Supply**: Initially 0

### Functions

1. **mint(address addr, uint val)**: Mints `val` tokens to the address `addr`.
2. **burn(address addr, uint val)**: Burns `val` tokens from the address `addr` if the address has sufficient balance.
3. **fallback() external payable**: Prevents the contract from receiving Ether.
4. **receive() external payable**: Prevents the contract from receiving Ether.

### Mappings

- **d**: A mapping that keeps track of the token balance for each address.

## Prerequisites

- [Node.js](https://nodejs.org/)
- [MetaMask](https://metamask.io/) browser extension

## Steps to Run the Project

### Step 1: Smart Contract

1. Open [Remix IDE](https://remix.ethereum.org/).
2. Create a new file named `SimpleToken.sol`.
3. Copy and paste the following Solidity code into the file:

    ```solidity
    // SPDX-License-Identifier: MIT
    pragma solidity 0.8.18;

    contract SimpleToken {

        string public a = "SimpleToken";
        string public b = "STK";
        uint public c = 0;

        mapping(address => uint) public d;  // mapping 

        function mint(address addr, uint val) public {   // function for creating tokens
            c += val;
            d[addr] += val;
        }

        function burn(address addr, uint val) public {     // destroying tokens
            require(d[addr] >= val, "Insufficient balance to burn");
            c -= val;
            d[addr] -= val;
        }

        fallback() external payable {            // fallback function to prevent contract from receiving Ether
            revert("Contract does not accept Ether");
        }

        receive() external payable {                // receive function to prevent contract from receiving Ether
            revert("Contract does not accept Ether");
        }
    }
    ```

4. Compile the contract using the Solidity compiler.
5. Deploy the contract using the "Deploy & Run Transactions" tab.

### Step 2: Interacting with the Contract

1. After deploying the contract, use the deployed contract's interface in Remix to interact with the contract functions.
2. To mint tokens, use the `mint` function and provide the address and the amount of tokens to mint.
3. To burn tokens, use the `burn` function and provide the address and the amount of tokens to burn.
4. Ensure you are using a valid address and sufficient token balance when calling these functions.

## Summary

This project demonstrates how to create a simple token smart contract using Solidity, with functionalities for minting and burning tokens, and mappings to track token balances. The contract includes safeguards to prevent receiving Ether.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
