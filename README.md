# Experiment 3: Supply Chain Transparency for Luxury Goods

# Aim:
To develop a smart contract that tracks the supply chain of luxury goods, ensuring authenticity.

### Name : Mohammed ibrahim MN 
### Reg No : 212223100034

# Algorithm:
1.Identify stakeholders involved in the luxury goods supply chain.

2.Set up a blockchain network to record and share supply chain data.

3.Develop smart contracts to automate tracking and verification processes.

4.Assign unique digital IDs (e.g., QR/RFID) to each luxury product.

5.Record product data at every supply chain stage into the blockchain.

6.Enable consumer access to product history via a web or mobile app.

7.Monitor and improve the system through audits and feedback.


# Program:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract LuxurySupplyChain {
    struct Product {
        string name;
        address currentOwner;
        bool verified;
    }

    mapping(uint256 => Product) public products;

    event ProductRegistered(uint256 productId, string name);
    event OwnershipTransferred(uint256 productId, address newOwner);

    function registerProduct(uint256 productId, string memory name) public {
        require(products[productId].currentOwner == address(0), "Product already registered");
        products[productId] = Product(name, msg.sender, true);
        emit ProductRegistered(productId, name);
    }

    function transferOwnership(uint256 productId, address newOwner) public {
        require(products[productId].currentOwner == msg.sender, "Not the owner");
        products[productId].currentOwner = newOwner;
        emit OwnershipTransferred(productId, newOwner);
    }

    function verifyProduct(uint256 productId) public view returns (string memory, address, bool) {
        Product memory p = products[productId];
        return (p.name, p.currentOwner, p.verified);
    }
}
```
# Expected Output:
A luxury good (e.g., a Rolex watch) is registered on-chain.
![image](https://github.com/user-attachments/assets/ff8fcedc-3508-4f0a-9152-93a4ebafeb7a)



Ownership is transferred at every checkpoint.
![image](https://github.com/user-attachments/assets/1855beac-4794-446b-b0f2-2b575a0b3748)


Buyers can check the authenticity before purchasing.


# High-Level Overview:
Helps prevent counterfeit luxury goods.


Teaches real-world supply chain use cases.

# RESULT : 
Hence we implemented code for a smart contract that tracks the supply chain of luxury goods, ensuring authenticity.

