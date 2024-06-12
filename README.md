# Project Title
MyToken Smart Contract

# Simple Overview
A simple Solidity smart contract for a token with public details, address-to-balance mapping, mint and burn functions, and balance checks during burning.

# Description

## Public Variables
 - `tokenName`: A string that stores the full name of the token. In this contract, it is set to "Yashi gupta".
  - `tokenAbbrv`:A string that stores the abbreviation or ticker symbol of the token. In this contract, it is set to "YAS".
  - `totalSupply`:An unsigned integer (uint256) that stores the total number of tokens that have been minted minus the tokens that have been burned. It starts at 0 and is updated by the mint and burn functions.

## Mappings
- `balances`:It tracks that how many tokens each person have.
## Functions
- `mint`: It creates new tokens and Increases the total supply and the balance of a specified address.
- `burn`: It destroy the tokens and Decreases the total supply and the balance of a specified address, ensuring that the balance is sufficient for the burn operation.

## Copy code solidity Contract Code
       
- Copy the following code and paste it into `eth_beg`:
     ```solidity
     // SPDX-License-Identifier: MIT
     pragma solidity 0.8.18;

     /*
            REQUIREMENTS
         1. Your contract will have public variables that store the details about your coin (Token Name, Token Abbrv., Total Supply)
         2. Your contract will have a mapping of addresses to balances (address => uint)
         3. You will have a mint function that takes two parameters: an address and a value. 
            The function then increases the total supply by that number and increases the balance 
            of the “sender” address by that amount
         4. Your contract will have a burn function, which works the opposite of the mint function, as it will destroy tokens. 
            It will take an address and value just like the mint functions. It will then deduct the value from the total supply 
            and from the balance of the “sender”.
         5. Lastly, your burn function should have conditionals to make sure the balance of "sender" is greater than or equal 
            to the amount that is supposed to be burned.
     */

     contract MyToken {
         // public variables here
         string public tokenName = "Yashi gupta";
         string public tokenAbbrv = "YAS";
         uint256 public totalSupply = 0;

         // mapping variable here
         mapping(address => uint256) public balances;

         // mint function
         function mint(address _address, uint _val) public {
             totalSupply += _val;
             balances[_address] += _val;
         }

         // burn function
         function burn(address _address, uint _val) public {
             if (balances[_address] >= _val) {
                 totalSupply -= _val;
                 balances[_address] -= _val;
             }
         }
     }
     ```
### Executing Program

#### How to Run the Program in Remix
1. **Compile the Smart Contract**
   - Select the `Solidity Compiler` tab.
   - Ensure the compiler version is set to `0.8.18`.
   - Click `Compile MyToken`.

2. **Deploy the Contract**
   - Go to the `Deploy & Run Transactions` tab.
   - Select the appropriate environment (e.g., JavaScript VM).
   - Click `Deploy`.

3. **Interact with the Contract**
     - After deploying, the contract will appear under `Deployed Contracts`.
   - To mint tokens:
     - Input the address and the amount of tokens to mint.
     - Click the `mint` button.
   - To burn tokens:
     - Input the address and the amount of tokens to burn.
     - Click the `burn` button.
