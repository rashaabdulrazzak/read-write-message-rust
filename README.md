# Read-write-message-rust
this is an example of how to read and write to the blockchain in NEAR using Rust.

# Usage
### Prerequisites
* [Rust toolchain](https://doc.rust-lang.org/1.30.0/book/2018-edition/ch01-01-installation.html)

* [A NEAR account](https://docs.near.org/docs/develop/basics/create-account)
* NEAR command-line interface (near-cli) to install run: 

``` 
npm install -g near-cli
``` 
### Getting start 
1. Clone the repository 
2. Build the contract by running the following command:
 ```
 cargo build --target wasm32-unknown-unknown --release
 ```
3. Login to your NEAR account from the terminal to ba able to deploy the contract
```
near login 
``` 
4. Deploy the contract by running the following command :

```
near deploy --wasmFile target/wasm32-unknown-unknown/release/set_message.wasm --accountId message.rustnear.testnet :  message.rustnear.testnet is the account I used to login in step 3 
``` 
if the deployment went correctly you will get amessage in the terminal like this with different url related to your contract

```
Starting deployment. Account id: message.rustnear.testnet, node: https://rpc.testnet.near.org, helper: https://helper.testnet.near.org, file: target/wasm32-unknown-unknown/release/set_message.wasm
Transaction Id 2Pyq4KqrcT6uHvvZ1X6mkcdU783pypU7gESnTRDcSLC2
To see the transaction in the transaction explorer, please open this url in your browser
https://explorer.testnet.near.org/transactions/2Pyq4KqrcT6uHvvZ1X6mkcdU783pypU7gESnTRDcSLC2
<b> Done deploying to message.rustnear.testnet </b>

``` 
at this point you have a contract deployed on the blockchain 

### Intract with the contract:

1. Write message to the contract:
To write a message to the contract you can run the following code: 
```
near call message.rustnear.testnet set_status '{"message" : "hello"}' --accountId rashaabdulrazzak.testnet
``` 
where: 
message.rustnear.testnet : is the account you deployed the contract on (same account from step 3 in Getting start part) 
rashaabdulrazzak.testnet : is the account you want to call the corntact (it can be the same from step 3 or any other existing account you can login to) 

2. Read from the contract: 
To read the message we wrote in the previous step we run the following command: 
```
near call message.rustnear.testnet get_status '{"account_id" : "rashaabdulrazzak.testnet"}' --accountId rashaabdulrazzak.testnet
``` 
where the account_id should be the account we signed the message in the previous step. 

