# Blockchain-Based Supply Chain Management Portal

A decentralized application (DApp) for transparent supply chain tracking using Ethereum blockchain technology. Developed as final year B.Tech project at Chaitanya Bharathi Institute of Technology.

## Overview

This project implements a transparent supply chain management system where products can be tracked from manufacturer to end consumer using blockchain technology. Each transaction is immutably recorded on the blockchain, ensuring authenticity and preventing counterfeit products, particularly crucial in pharmaceutical and healthcare sectors.

## Features

- **Multi-Actor System**: Supports manufacturers, distributors, retailers, and consumers
- **Product Tracking**: Complete traceability from origin to end-user
- **Smart Contracts**: Automated execution of supply chain rules and transfers
- **Transparency**: Public verification of product authenticity and journey
- **Immutable Records**: Permanent transaction history on blockchain
- **User-Friendly Interface**: React-based web interface for all stakeholders

## Technology Stack

- **Blockchain**: Ethereum (Local deployment using Ganache)
- **Smart Contracts**: Solidity 0.8.0+
- **Frontend**: React.js, Web3.js
- **Development Framework**: Truffle Suite
- **Testing**: Mocha, Chai
- **Local Blockchain**: Ganache CLI/GUI

## Architecture

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│Manufacturer │────>│ Distributor │────>│   Retailer  │
└─────────────┘     └─────────────┘     └─────────────┘
       │                   │                    │
       └───────────────────┴────────────────────┘
                           │
                    ┌──────────────┐
                    │  Blockchain  │
                    │   (Ganache)  │
                    └──────────────┘
                           │
                    ┌──────────────┐
                    │  React App   │
                    │   (Web3.js)  │
                    └──────────────┘
```

## Prerequisites

- Node.js v14+ and npm
- Truffle Suite
- Ganache CLI or Ganache GUI
- MetaMask browser extension

## Installation

### 1. Clone the repository
```bash
git clone https://github.com/KrishnaRishi2208/Blockchain-based-Supply-Chain-Management.git
cd Blockchain-based-Supply-Chain-Management
```

### 2. Install dependencies
```bash
# Install Truffle globally
npm install -g truffle

# Install project dependencies
npm install
```

### 3. Start Ganache
```bash
# Using Ganache CLI
ganache-cli -p 8545

# Or use Ganache GUI (download from https://trufflesuite.com/ganache/)
```

### 4. Deploy Smart Contracts
```bash
truffle compile
truffle migrate --reset
```

### 5. Configure MetaMask
- Connect MetaMask to `http://localhost:8545`
- Import accounts from Ganache using private keys
- Network ID: 1337 (or as configured in Ganache)

### 6. Start the React application
```bash
cd client
npm install
npm start
```

Application will run at `http://localhost:3000`

## Smart Contract Structure

### SupplyChain.sol
Main contract managing the supply chain logic:

```solidity
- addManufacturer()      // Register manufacturer
- addDistributor()       // Register distributor  
- addRetailer()         // Register retailer
- manufactureProduct()   // Create new product
- shipToDistributor()   // Transfer to distributor
- shipToRetailer()      // Transfer to retailer
- purchaseProduct()     // Consumer purchase
- getProductHistory()   // View complete history
```

### Product Structure
```solidity
struct Product {
    uint256 id;
    string name;
    uint256 price;
    address manufacturer;
    address currentOwner;
    State state;
    uint256 timestamp;
}
```

## Usage Guide

### For Manufacturers
1. Register as manufacturer
2. Add new products to the system
3. Set product details and initial price
4. Transfer products to distributors

### For Distributors/Retailers
1. Register in the system
2. Receive products from previous actor
3. Update product location/status
4. Transfer to next actor in chain

### For Consumers
1. Search for products by ID
2. View complete product history
3. Verify authenticity before purchase
4. Complete purchase transaction

## Testing

Run the test suite:
```bash
truffle test
```

Tests include:
- Contract deployment
- Actor registration
- Product creation
- Ownership transfers
- State transitions
- Access control

## Project Structure

```
Blockchain-based-Supply-Chain-Management/
├── contracts/
│   ├── SupplyChain.sol      # Main smart contract
│   └── Migrations.sol       # Truffle migrations
├── migrations/
│   └── 2_deploy_contracts.js
├── test/
│   └── supplychain.test.js  # Contract tests
├── client/
│   ├── src/
│   │   ├── components/      # React components
│   │   ├── contracts/       # Contract ABIs
│   │   └── App.js          # Main application
│   └── package.json
├── truffle-config.js        # Truffle configuration
└── package.json
```

## Key Features Implementation

### Product Authentication
- Each product gets a unique blockchain ID
- QR codes can be generated for physical products
- Consumers can scan and verify authenticity instantly

### Transparency Benefits
- **Healthcare**: Verify medicine authenticity, check expiry dates
- **Food Industry**: Track farm-to-table journey
- **Luxury Goods**: Prevent counterfeiting
- **Electronics**: Verify genuine components

## Gas Optimization Strategies

- Minimal on-chain storage
- Event logging for historical data
- Efficient struct packing
- Batch operations where possible

## Security Considerations

- Role-based access control
- Ownership verification at each step
- Re-entrancy protection
- Input validation and sanitization


## Learning Outcomes

This project demonstrates understanding of:
- Blockchain fundamentals and Ethereum
- Smart contract development with Solidity
- DApp architecture and Web3 integration
- Supply chain management concepts
- Decentralized system design

## Contributing

This is an academic project. Feel free to fork and enhance for educational purposes.

## License

MIT License

**Note**: This project was developed for educational purposes. For production deployment, additional security audits and optimizations would be required.
