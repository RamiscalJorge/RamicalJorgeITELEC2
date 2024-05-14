The module is given to us to teach us the fundamentals of creating a block chain

 Description

This program aims to help us understand the basics and also to give us a knowledge about 
block chain

 Getting Started
 To be able to execute this application, you may use Remix, an online Solidity IDE, which can be found at https://remix.ethereum.org/.

 Create a new file on the Remix website by clicking the "+" symbol in the left-hand sidebar. Save the file as Phoenixtoken.sol . Insert the following code into the file:

// SPDX-License-Identifier: MIT
pragma solidity >=0.6.12 <0.9.0;

import "@openzeppelin/contracts/utils/math/SafeMath.sol";

contract Payment {
    using SafeMath for uint256;

    uint256 public balance;
    uint256 public constant MAX_UINT = type(uint256).max;

    event Deposit(address indexed from, uint256 amount);
    event Withdrawal(address indexed to, uint256 amount);

    // Deposit function allowing users to deposit ETH into the contract
    function deposit(uint256 _amount) public payable {
        // Ensure that the sent amount matches the specified amount
        require(msg.value == _amount, "Sent value does not match specified amount");

        // Add the deposit amount to the balance using SafeMath to prevent overflow
        balance = balance.add(_amount);

        // Emit a deposit event for logging
        emit Deposit(msg.sender, _amount);
    }

    // Withdraw function allowing users to withdraw ETH from the contract
    function withdraw(uint256 _amount) public {
        // Ensure that the contract has enough balance for the withdrawal
        require(balance >= _amount, "Insufficient balance");

        // Subtract the withdrawal amount from the balance using SafeMath to prevent underflow
        balance = balance.sub(_amount);

        // Transfer the specified amount to the caller
        payable(msg.sender).transfer(_amount);

        // Emit a withdrawal event for logging
        emit Withdrawal(msg.sender, _amount);
    }
    
    // Fallback function to handle direct ETH transfers to the contract
    receive() external payable {
        // Treat any direct transfer as a deposit
        deposit(msg.value);
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
