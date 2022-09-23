# Akbank-Web3-Practicum-Hw1
Hands on Task (Beginner Level): Build and Deploy an Ether-Store Smart Contract with Remix IDE
![Screenshot_4](https://user-images.githubusercontent.com/67005954/192044520-f7b8c3fd-a81a-4b43-89ef-8fcdcab42684.png)

```Solidity
pragma solidity ^0.8.7;
//SPDX-License-Identifier: MIT
contract FeeCollector {
    //Kontrat sahibi yani adresin sahibi
    address public owner;
    uint256 public balance;
    constructor() {
        //msg.sender ile kontrat adresimizi owner a atadık.
        owner = msg.sender;
    }

    receive() payable external {
        balance += msg.value;
    }

    function withdraw (uint amount, address payable destination) public {
    require(msg.sender == owner, "Only owner can withdraw");
    require(amount <= balance, "Balance is not enough");

    destination.transfer(amount);
    balance -= amount;
    }
}
```
