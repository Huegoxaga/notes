# Solidity

## Introduction

- Solidity is an object-oriented programming language for writing smart contracts, mostly for Ethereum.
- Solidity code has `.sol` extension.
- It is a strongly typed language.
- Solidity compiler can compile the code into contract bytecode, the bytecode can be deployed and run on any blockchain networks. The compiler can also compile the code into `ABI` that can be parsed as JavaScript objects

## IDE

### Remix

- [Remix](https://remix.ethereum.org) is an online code editor, created for writing and testing Solidity codes
- To select a preferred compiler version, Click the drop down menu named `Select new compiler version` and scroll down to select a version
- It will show a red box whenever there is an error in the code
- Click `Run` button can quickly test the contract.
  - It can create a mini network with the broswer's JavaScript engine with a new account for testing.
- By adding input variable for the constructor and click `Create` button a contract instance will be created at the button
  - Click the `X` on the top right corner of the contract instance dialog, and run the constructor again to recompile the contract.
- Click the colored boxes to run the function inside the contract instance dialog.
  - red boxes required user input
  - blue boxes will output values, multiple output values will have indices starting at 0.
- It can interact with deployed contracts by selecting the `Injected Web3` option, then input the contract address in the `AtAddress` box
  - `Injected Web3` can be used to get access to account through `metamask`
- It includes a debugger on the top right corner of the console panel

## Network Provider

### Ganache

- Previously known as `TestRPC`
- It host a local test network
- It is good for local testing
- It provides 10 unlocked Ethereum accounts that doesn't required token to access

### Truffle Wallet Provider

- It provide the provider required to initialize `web3` connection

#### Usage

- run `npm install --save truffle-hdwallet-provider`
- `const HDWalletProvider = require('truffle-hdwallet-provider');` import module
- `const provider = new HDWalletProvider('12 words mnemonics', 'Network API URL')` initialize the provider
- `const web3 = new Web3(provider)` use the provider to connect

## Network APIs

- There are companys that host nodes for various blockchain network, and they provide API access to these nodes.

### Infura

- It provides API accesses to Ethereum Main and Test networks

#### Usage

- Sign up at [here](https://infura.io)
- Create a new project in the console and get the API token
- Select the network and get the endpoint URL

## Deployment

### Truffle

- A comprehensive contract development CLI tool
- It is undergoing rapid development

### Custom Node Project

1. In a new project folder, run `npm init` to generate a new `package.json` file
2. Run `npm install --save solc mocha ganache-cli web3` to install the solidity compiler, the mocha testing framework, Ganache or TestRPC for creating local Ethereum network and the `web3.js` library
3. put solidity code in a sub folder called `contracts`
4. In the project folder create a `compiler.js` file with the following code:
   ```js
   const path = require("path");
   const fs = require("fs");
   const solc = require("solc");
   const inboxPath = path.resolve(__dirname, "contracts", "Inbox.sol");
   const source = fs.readFileSync(inboxPath, "utf8");
   // 1 stands for the number of contract for compilation
   module.exports = solc.compile(source, 1).contracts[":Inbox"];
   ```
   - The compiler outputs a `bytecode` object for deployment and an `interface` object as `ABI` in a list of contracts it compiled under the `contracts` property
5. create a test folder and test file `projectName.test.js` using `mocha`, then run test cases locally
6. create a deploy file, and run `node deployFilename.js` to deploy to an actual network

## Basic Syntax

- Semicolon is required at the end of each line.
- Single line comments: Start the line with `//`
- Multi-line comment: Start with `/*` and end with `*/`.
- In the first line of the code, the version of the solidity code in use should be specified as `pragma solidity ^X.X.XX;`
- Each code file will define a contract. A contract is essentially a class using keyword contract.

## Basic Types

- `string`: sequence of characters
- `bool`: `true` or `false`
- `int`(`int256`): positive and negative integer numbers
  - `int8` - `int256`: the number indicate the number of bits this type can store
  - `int8` stores numbers from `-128` - `127`
  - solidity does not provide built-in method to generate random numbers
- `uint`(`uint256`): unsigned integer, positive numbers only
  - `uint8` stores numbers from `0` - `256`
- `fixed`: decimal numbers
  - for coin units `0.01 ether` will be auto converted to the equivalent amount of `wei`
- `ufixed`: unsigned decimal numbers
- `address`: store account address, has methods for sending money
  - `addressX.transfer(amount)` transfer money from the current contract to the address in `wei`

### Type Conversion

- `int(value)` convert a value to `int`

## Reference Types

- fixed array: array with fixed length, all elements must be the same type
  - `int[3]`
- dynamic array: array with fixed leng, all elements must be the same type
  - `int[] public arrayX;`
  - `arrayX = new int[](5);` create dynamic array with initial size 5, default value will be `0`
  - `arrayX.push(1);` add a new element `1`
  - `arrayX.length;` return the length of the array
  - `arrayX[0]` access the first element
  - when solidity works with `ABI` the nested dynamic arrays are not available
    - string is an array of character. In this case, an array of string is also not available
    - It will raise an `UnimplementedFeatureError`
  - the default getter method for array takes an index as argument and return the value of the element
- mapping: collection of key value pairs, keys must be of the same type, and values must be of the same type. Keys and values doesn't have to be of the same type
  - `mapping(string => int) public mappingX`
- struct: represent an object type
  - `struct Person { uint age; string name; }`

## Global Variable

- The variable that available for all functions

### `msg`

- `msg.data` the data in the transcation
- `msg.gas` the amount of gas available
- `msg.sender` the address of the account that called the function
- `msg.value` the amount of ether in wei that was sent along with the function call

### `block`

- `block.difficulty` the current block difficulty

### `now`

- `now` returns the current time

### `this`

- `this` is a reference to the current contract
- `this.balance` the current balance of the current contract

## Contract

- A contract can be defined using `contract ContractName{}`

### Instance Variables

- A variable can be defined inside a contract using `string public variableName`syntax
- For all public variables, the compiler will automatically create a public get method that has the same name as the variable name for easy access.
- Instance variables can be `private` and it will not be shown to the users.

### Function

- It can be defined inside each contract definition as follow
  ```java
  function functionName(string variableName) public view returns(string){
      return newVariable;
  }
  ```
- A function can be of the following types:
  - `public` - anyone can call it.
  - `private` - can only be called internally by the contract.
- A `public` or `private` can have the following optional modifier.
  - `view` or `constant` - this function returns a data without modifying any data in the contract.
    - only this type of function can return values
  - `pure` - function without accessing or modifying contract's data.
  - `payable` - function involves in transactions.
- A constructor function has the same name as the contract name, and defined as follows:
  ```java
  function ContractName(string initialVariable) public{
      variable = initialVariable
  }
  ```

### Modifier

- it acts like a wrapped for others function to reduce duplicated codes

```java
function innerFunc() public modfierExample {
  // code
}
// the _; indicate the location of the inner function code when it is wrapped in the modifier
modifier modfierExample() {
  // code
  _;
}
```

### Global Functions

- `require(condition);` is used to check if a certain condition is satisfied in a funciton. When the condition returns false the function will stop executing and return an error message says `VM error: revert`, if true the execution will continue
- `sha3(valueA, valueB, valueC);` or `keccak256(valueA, valueB, valueC)` calculate hash bash on the input values
