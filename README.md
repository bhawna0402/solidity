# TheToken Smart Contract

TheToken is an Ethereum smart contract that implements a basic token with functionalities to mint and burn tokens.
It includes public variables to store the token details, a mapping of addresses to balances, and functions to mint and burn tokens.
## Description
The computer language Solidity, which is used to create smart contracts on the Ethereum network, is used to write this contract. 
The four public state variables in this contract are balances, total supply, token name, and token symbol. 
The mapping of a sender to its balance is called a balance.
following BurnTokens and mintTokens are the two functions. Two parameters are required by mintTokens: address and value. The value will be added to the sender's balance and token supply upon calling mintToken. 
The next step in burnTokens is to provide the address and value to be burned. A conditional statement is then used to determine whether or not the tokens to be burned are truly present in the sender's balance.
If the requirement is met, the amount will be subtracted from the balance of address.
## Executing program
To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/
Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar.
Save the file with a .sol extension (e.g., MyToken.sol). Copy and paste the following code into the file:
## Code
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
contract TheToken {

    // public variables here
    string public tokenName = "ALPHA";
    string public tokenSymbol = "ALP";
    uint public totalSupply = 0;

    // mapping variable here
    mapping(address => uint) public balances;

    // mint function
    function mint(address _to, uint _value) public {
        totalSupply += _value;
        balances[_to] += _value;
    }

    // burn function
    function burn(address _from, uint _value) public {
        require(balances[_from] >= _value, "Insufficiant balance");
        totalSupply -= _value;
        balances[_from] -= _value;
    }
}

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar.
Make sure the "Compiler" option is set to "0.8.18" (or another compatible version), and then click on the "Compile MyToken.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. 
Select the "MyToken" contract from the dropdown menu, and then click on the "Deploy" button.

Once the contract is deployed, you can interact with it.
Click on the "MyToken" contract in the left-hand sidebar, and then check the token Abbrev, tokenName, total supply by clicking them.
By passing address and token value in mintToken and clicking it will call the mintTokens function and same will be with burnTokens.
## License
This MyToken is licensed under the MIT License
