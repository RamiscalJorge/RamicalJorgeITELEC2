The module is given to us to teach us the fundamentals of creating a block chain

 Description

This program aims to help us understand the basics and also to give us a knowledge about 
block chain

 Getting Started
 To be able to execute this application, you may use Remix, an online Solidity IDE, which can be found at https://remix.ethereum.org/.

 Create a new file on the Remix website by clicking the "+" symbol in the left-hand sidebar. Save the file as Phoenixtoken.sol . Insert the following code into the file:

 // SPDX-License-Identifier: MIT
pragma solidity >=0.6.12 <0.9.0;

contract Payment {
    uint public balance;
    uint public constant MAX_UINT = 2 ** 256 - 1;

    function deposit(uint _amount) public {
        // Use require to ensure that the deposit doesn't cause overflow
        uint oldBalance = balance;
        uint newBalance = balance + _amount;
        require(newBalance >= oldBalance, "Overflow");

        balance = newBalance;

        // Use assert to ensure that the balance is correctly updated
        assert(balance >= oldBalance);
    }

    function withdraw(uint _amount) public {
        // Ensure that the withdrawal doesn't cause underflow
        require(balance >= _amount, "Insufficient balance");
        
        // Safe subtraction to prevent underflow
        balance -= _amount;

        // Assert to ensure that the balance is correctly updated
        assert(balance <= MAX_UINT);

        // Add a revert statement if the withdrawal amount exceeds the contract's balance
        if (balance < _amount) {
            revert("The amount withdrawal exceeds to the balance");
        }
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
