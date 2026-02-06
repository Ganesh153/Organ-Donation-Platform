# Blockchain-Enabled Organ Donation Platform

A decentralized web-based platform built on Ethereum blockchain that facilitates organ donation by creating a transparent, secure, and trustworthy ecosystem connecting organ donors, patients in need of organs, and medical professionals.

## 📋 Project Overview

This is my **Final Year B.Tech Project** that leverages blockchain technology to enhance transparency and trust in organ donation systems. The platform addresses critical challenges including:

- **Lack of transparency** in donor-recipient matching
- **Trust issues** between patients and medical professionals
- **Difficulty in verifying** donor and recipient information
- **Centralized control** and potential data manipulation
- **Inefficient organ allocation** processes

### Key Features

✅ Decentralized donor-patient matching system  
✅ Immutable medical records on blockchain  
✅ Transparent and trustworthy platform  
✅ User-friendly web interface  
✅ Automated smart contract execution  
✅ Real-time data availability  
✅ Secure and tamper-proof storage  

## 🛠️ Technology Stack

### Blockchain Layer
- **Ethereum Blockchain** - Smart contract deployment
- **Solidity** (v0.8.10) - Smart contract language
- **Truffle Framework** - Development and testing
- **Ganache** - Local blockchain network

### Frontend Layer
- **HTML5** - Structure and markup
- **CSS3** - Styling and responsive design
- **JavaScript (Vanilla)** - Client-side logic
- **Web3.js** - Ethereum interaction library
- **Bootstrap** - Responsive UI framework
- **Font Awesome** - Icon library

### Build Tools
- **Webpack** - Module bundler
- **Node.js** - Runtime environment
- **npm** - Package manager

## 📦 Prerequisites

Before running this project, ensure you have installed:

- **Node.js** (v14 or higher) - [Download](https://nodejs.org/)
- **npm** (comes with Node.js)
- **Truffle** - Install globally: `npm install -g truffle`
- **Ganache CLI** - Install globally: `npm install -g ganache-cli`

Verify installations:
```bash
node --version
npm --version
truffle --version
ganache-cli --version
```

## 🚀 Quick Start

This application requires **three separate terminal windows** to run simultaneously.

### Terminal 1: Start Local Blockchain (Ganache)

```bash
ls
npx ganache-cli --port 7545 -i 5777
```

**Expected Output:**
```
Ganache CLI v6.x.x (ganache-core: 2.x.x)

Available Accounts
==================
(0) 0x627306090abaB3A6e1400e9345bC60c78a8BEf57
(1) 0xf17f52151EbEF6C7334FAD080c5704DAAB192C5a
...

Listening on 127.0.0.1:7545
```

**Note:** Keep this terminal running. It provides the local Ethereum network on port 7545 with network ID 5777.

---

### Terminal 2: Deploy Smart Contracts

In a **new terminal window**, run:

```bash
ls
npx truffle migrate
```

**Expected Output:**
```
Compiling your contracts...
===========================
> Compiling ./contracts/DonorContract.sol
> Compiling ./contracts/Migrations.sol

Artifacts written to /path/to/build/contracts
Compiled successfully using:
   - solc: 0.8.10+commit.fc810830.Eminem.Linux.g++

Starting migrations...
======================
> Network name:    'development'
> Network id:      5777
> Block limit:     6721975

1_initial_migration.js
======================
   Deploying 'Migrations'
   ----------------------
   > transaction hash:    0x...
   > Blocks: 0        Seconds: 0
   > contract address:    0x...
   > block number:        1
   > block gas used:      ...
   > gas price:           2 gwei
   > value sent:          0 ETH
   > total cost:          ... ETH

   > Saving migration to chain.
   > Saving artifacts
   ---------------------
   > Total cost:          ... ETH

2_deploy_contracts.js
======================
   Deploying 'DonorContract'
   -------------------------
   > transaction hash:    0x...
   > Blocks: 0        Seconds: 0
   > contract address:    0x...
   > block number:        2
   > block gas used:      ...
   > gas price:           2 gwei
   > value sent:          0 ETH
   > total cost:          ... ETH

   > Saving migration to chain.
   > Saving artifacts
   ---------------------
   > Total cost:          ... ETH

Summary
=======
> Total deployments:   2
> Final cost:          ... ETH
```

**Note:** The contract address will be displayed. This is automatically configured in the application.

---

### Terminal 3: Start Development Server

In a **third terminal window**, run:

```bash
ls
cd app
npm run dev
```

**Expected Output:**
```
> organ-donation-platform@1.0.0 dev
> webpack-dev-server

ℹ ｢wds｣: Project is running at http://localhost:8080/
ℹ ｢wds｣: webpack output is served from /
ℹ ｢wds｣: Content not from webpack is served from /path/to/app/src
ℹ ｢wdm｣: Hash: abc123def456...
ℹ ｢wdm｣: Version: webpack 4.41.2
ℹ ｢wdm｣: Time: 1234ms
ℹ ｢wdm｣: built with 0 warnings
```

**Note:** The application will be available at `http://localhost:8080`

---

## 📂 Project Structure

```
Organ-Donation-Platform/
├── contracts/
│   ├── DonorContract.sol          # Main smart contract
│   └── Migrations.sol             # Truffle migration contract
├── migrations/
│   └── 1_initial_migration.js     # Deployment scripts
├── app/
│   ├── src/
│   │   ├── index.html             # Main dashboard
│   │   ├── main.js                # Frontend logic & Web3 integration
│   │   ├── html/
│   │   │   ├── donor-registration.html
│   │   │   ├── donor-pledge.html
│   │   │   ├── patient-registration.html
│   │   │   ├── view-donors.html
│   │   │   ├── view-patients.html
│   │   │   ├── view-pledges.html
│   │   │   ├── verify-pledges.html
│   │   │   ├── transplant-matching.html
│   │   │   ├── awareness.html
│   │   │   └── homepage.html
│   │   ├── css/
│   │   │   ├── styles.css
│   │   │   ├── bootstrap.css
│   │   │   └── fontawesome-all.css
│   │   └── images/                # Logos and graphics
│   ├── package.json               # Dependencies
│   ├── webpack.config.js          # Build configuration
│   └── node_modules/              # Installed packages
├── build/
│   └── contracts/                 # Compiled contract artifacts
├── truffle-config.js              # Truffle configuration
└── README.md                       # This file
```

## 🔧 Configuration

### Ganache Configuration
- **Port:** 7545
- **Network ID:** 5777
- **Host:** 127.0.0.1

### Web3 Configuration (app/src/main.js)
```javascript
const web3 = new Web3("HTTP://127.0.0.1:7545");
```

### Contract Deployment
The contract is automatically deployed to the local network. The contract address is read from:
```javascript
const deployedContract = artifact.networks[5777];
const contractAddress = deployedContract.address;
```

## 📖 Usage Guide

### 1. Register as Donor
- Navigate to **"Register Donor"** on the dashboard
- Fill in personal and medical information
- System validates input (age ≥ 18, realistic weight/height)
- Submit to register on blockchain

### 2. Register as Patient
- Navigate to **"Register Patient"** on the dashboard
- Fill in personal and medical information
- Specify organs needed for transplant
- Submit to register on blockchain

### 3. Pledge Organs
- Navigate to **"Donor Pledge"** to pledge organs
- Pledge can be converted to verified donor status by medical professionals

### 4. Verify Pledges
- Medical professionals can navigate to **"Verify Pledges"**
- Review pledge information
- Convert verified pledges to donor status

### 5. Search Donors/Patients
- Use search functionality on dashboard
- Enter medical ID to find donor or patient information
- View complete medical profile

### 6. Transplant Matching
- Navigate to **"Transplant Match"**
- System automatically matches compatible donors with patients
- Matching considers:
  - Blood type compatibility
  - Organ availability
  - Physical compatibility
  - Medical urgency

### 7. View Records
- **View Donors** - See all registered donors
- **View Patients** - See all registered patients
- **View Pledges** - See all organ pledges

## 🔐 Input Validation

The platform validates all inputs:

- **Full Name:** Must not be empty
- **Age:** Must be provided; minimum 18 years for donors
- **Gender:** Must be selected
- **Medical ID:** Must be unique (blockchain enforced)
- **Organs:** At least one organ must be selected
- **Weight:** Must be between 20-200 kg
- **Height:** Must be between 54-272 cm
- **Blood Type:** Must be selected from valid options

## 🛡️ Security Features

- ✅ Decentralized storage prevents single point of failure
- ✅ Cryptographic hashing ensures data integrity
- ✅ Transaction signatures authenticate all operations
- ✅ Smart contract prevents duplicate registrations
- ✅ Immutable records prevent tampering
- ✅ Gas limits prevent infinite loops or attacks

## 🧪 Testing

### Run Smart Contract Tests
```bash
truffle test
```

### Manual Testing
1. Open browser to `http://localhost:8080`
2. Use Ganache accounts for transactions
3. Test registration, search, and matching features
4. Verify data appears on blockchain

## 🚨 Troubleshooting

### Issue: "Cannot connect to blockchain"
**Solution:** Ensure Ganache is running on port 7545
```bash
npx ganache-cli --port 7545 -i 5777
```

### Issue: "Contract not found at address"
**Solution:** Run migrations in Terminal 2
```bash
npx truffle migrate
```

### Issue: "Port 8080 already in use"
**Solution:** Kill the process using port 8080 or use a different port
```bash
# On Windows
netstat -ano | findstr :8080
taskkill /PID <PID> /F

# On macOS/Linux
lsof -i :8080
kill -9 <PID>
```

### Issue: "npm dependencies not installed"
**Solution:** Install dependencies in app directory
```bash
cd app
npm install
```

### Issue: "Webpack compilation errors"
**Solution:** Clear node_modules and reinstall
```bash
cd app
rm -rf node_modules package-lock.json
npm install
```

## 📝 Smart Contract Functions

### Registration Functions
- `setPledge()` - Register organ pledge
- `setDonors()` - Register verified donor
- `setPatients()` - Register patient

### Retrieval Functions
- `getPledge(medical_id)` - Get pledge information
- `getDonor(medical_id)` - Get donor information
- `getPatient(medical_id)` - Get patient information

### Verification Functions
- `validatePledge(medical_id)` - Check if pledge exists
- `validateDonor(medical_id)` - Check if donor exists
- `validatePatient(medical_id)` - Check if patient exists

### Listing Functions
- `getAllPledgeIDs()` - Get all pledge IDs
- `getAllDonorIDs()` - Get all donor IDs
- `getAllPatientIDs()` - Get all patient IDs

### Statistics Functions
- `getCountOfPledges()` - Total pledges
- `getCountOfDonors()` - Total donors
- `getCountOfPatients()` - Total patients

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.
**Last Updated:** February 2026  
**Status:** Active Development  
**Version:** 1.0.0
