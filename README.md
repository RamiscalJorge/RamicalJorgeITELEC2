The module is given to us to teach us the fundamentals of creating a block chain

 Description

This program aims to help us understand the basics and also to give us a knowledge about 
block chain

 Getting Started
 To be able to execute this application, you may use Remix, an online Solidity IDE, which can be found at https://remix.ethereum.org/.

 Create a new file on the Remix website by clicking the "+" symbol in the left-hand sidebar. Save the file as Phoenixtoken.sol . Insert the following code into the file:

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract MyContract {
    address public Jorge;  // Setting 'Jorge' as the owner
    mapping(address => uint) public balances;

    constructor() {
        Jorge = msg.sender;  // Initializing 'Jorge' as the contract deployer
    }

    function deposit() public payable {
        require(msg.value > 0, "Value must be greater than 0");  // Ensuring the deposit amount is greater than 0
        balances[msg.sender] += msg.value;  // Updating the balance mapping for the sender
    }

    function withdraw(uint amount) public {
        require(amount > 0, "Withdrawal amount should be greater than 0");  // Ensuring the withdrawal amount is greater than 0
        require(balances[msg.sender] >= amount, "You have insufficient balance");  // Checking if the sender has enough balance

        balances[msg.sender] -= amount;  // Updating the balance mapping for the sender

        bool success = payable(msg.sender).send(amount);  // Sending the amount to the sender
        require(success, "Transfer failed.");  // Ensuring the transfer was successful
    }

    function assertE(uint value) public pure returns (uint) {
        uint result = value * 2;  // Doubling the input value
        assert(result > value);  // Asserting that the result is greater than the input value
        return result;
    }

    function revertE(uint value) public pure returns (uint) {
        require(value != 0, "Value cannot be 0");  // Requiring the input value to be non-zero
        return 100 / value;  // Returning the result of 100 divided by the input value
    }
}


Authors
Jorge ramiscal
@JRamiscal

Contributors names and contact info

Ramiscal Jorge
[@Jay2kkkk](https://twitter.com/Jay2kkkk)


## License

This project is licensed under the Ramiscal Jorge License - see the LICENSE.md file for details
