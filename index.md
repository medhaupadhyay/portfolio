
# Introduction 
Although traditional blockchain transactions offer many advantages, the overall process often comes with many burdens when used in the context of small, frequent payments. Repeated payments can become costly and inefficient due to the associated transaction fees as well as the slow processing times. Micropayment channels have become a feasible and efficient way to remedy these drawbacks. Through a micropayment channel, individuals can carry out multiple transactions without having to make multiple commits on a blockchain, minimizing the cost for the entire process while making it faster. With the current limitations of existing micropayment channels, we propose to create a user-friendly system for individuals to send small repeated payments to trusted parties.
 <br>


<img src="https://github.com/medhaupadhyay/Micropayment-Channel-Public-Website/assets/81603081/ab241105-ac5c-411b-8478-d4e785649a58" style="height:600px;">



<br>

# How it Works 
<details>
<summary> Creating a New Channel </summary>
• Launch index.html and styles.css locally on your computer <br>
• Login with MetaMask and connect your account <br>
• Under ”Create New Channel”, enter your MetaMask address as the ”Sender Wallet Address” <br>
• Enter the ”Receiver Wallet Address”; this is the account you will be sending Ethereum to <br>
• Enter the "Deployment Amount"; this is the initial amount that will be stored in the payment channel as soon as it is opened <br>
• Enter the "Expiration Time"; if the amount of time specified passes and the receiver does not cash out their payments, the Ethereum will be returned to the sender <br>
• Click "Save Address"; a popup should appear so that user can confirm the input is correct <br>
• Click "Deploy Contract" <br>
• Check your MetaMask account and click on the transaction that just occurred <br>
• Click "View on Etherscan" and copy the contract address; keep this for your records <br> <br>
</details>


<details>
<summary>Logging a New Channel</summary>
• Enter the contract address of the newly created contract under ”Log a New Channel” <br>
• Click ”Submit” <br><br>
</details>


<details>
<summary>Logging Payments on an Existing Channel</summary>
• Under ”Log Payments on an Existing Channel”, enter the contract address <br>
• Input the amount of Ethereum you would like to send to the receiver <br>
• Click ”Log Payment” <br>
• Save the unique signature that is generated <br><br>
</details>


<details>
<summary>Closing a Channel</summary>
• Note: this action is irreversible <br>
• Enter the contract address under ”Close Channel” <br>
• Enter the most recently generated signature <br>
• Click ”Close Channel” <br>
• The receiver should receive the Ethereum once the transaction goes through <br>
• The channel will officially close and can no longer be interacted with from this point <br>
</details>
<br>


# Methods
<details>
<summary>Connecting to MetaMask</summary>
Users will be provided a field where they can input their address as well as the receiver's address to connect to MetaMask and begin the transaction process. This was implemented through the integration of Solidity smart contracts (converted to bytecode) and JavaScript, which were used to build the functionalities of the front-end interface. The smart contract acts as the MetaMask connection, while the program written in JavaScript executes the entire process from start to finish. <br><br>
</details> 

<details>
<summary>Opening a New Payment Channel Through Interface</summary>
Like the Connecting to MetaMask feature, opening a new payment channel involves the integration of Solidity and JavaScript. The smart contract will initiate the transaction history between the sender and receiver, and open a payment channel between the two parties. (Note: The user will not have to worry about the "contract address", as it will be stored and implemented in the back-end.) Once the addresses are verified as existing addresses, the sender will be permitted to enter an amount that they wish to send to the recipient. A unique signature will be generated and the sender will be expected to store and save this signature for future reference or when the parties wish to close the current channel. Once the payment channel is open, the sender can send more transactions -- which will be logged off-chain -- as long as needed or until the channel has been closed. <br><br>
</details> 

<details>
<summary>Logging Payments Off-Chain</summary>
This feature was implemented using key-value pairs in local storage. Each contract address serves as a key and the amount that the sender owes the receiver is the value. When a new channel is logged, the contract address is registered in local storage with a value of zero. When a new payment is logged, the existing value is increased by the given amount. The new total amount owed is set as the value for that contract key. This value is then displayed to the user in a pop up message, so they are aware of how much they owe the receiver and that the payment was logged. <br>
Along with every logged transaction, a unique signature is generated using web3.js. This signature must be inputted when the channel is closed in order to validate the transaction. <br>
Since the total amount due is updated as the information comes in, closing the channel simply involves transferring the recorded dues from the sender to the receiver. <br><br>
</details> 

<details>
<summary>Closing a Payment Channel Through Interface</summary>
Closing the payment channel integrates the smart contract and includes a function that allows the user to close the current payment channel. The user must input the unique signature that was generated when the latest payment was logged. It is crucial that the user uses the most recently generated signature in order to ensure that the receiver receives the full payment. After following the prompts, the user will be able to close the channel. The user will also be shown a warning that this action cannot be reversed. Once the payment channel closes, all transactions made from start to end will tally and be sent to the receiver in whole. <br> <br>
</details> <br>

# Results 
<details>
<summary>MetaMask Integration</summary>
The integration with MetaMask ensures that transactions, including contract deployment and interactions, are authenticated and confirmed by the user.
<br><br>
</details> 

<details>
<summary>Successful Deployment</summary>
The smart contract can be deployed traditionally or through our interface. Once deployed, the contract will be recorded on the Ethereum blockchain using the MetaMask account specified during the process.
<br><br>
</details> 

<details>
<summary>Logging Payments Off-Chain</summary>
Once the contract is deployed, users can log payments off-chain using our interface. The payment logs will be stored locally on their computer, and the running total will be displayed to the user.
<br><br>
</details> 

<details>
<summary>Closing the Channel</summary>
Once the sender and receiver decide that it is time to close the channel, they can do so through our interface. This involves sending the amount owed from the sender to the receiver and closing the contract. By only making one lump sum transaction, there will be significantly less fees than having to record each transaction on the blockchain individually.
<br><br>
</details> 

<details>
<summary>Transaction Confirmation</summary>
Users confirm transactions through MetaMask, providing an additional layer of security and control over their Ethereum wallet.
<br><br>
</details> 
<br>

# Conclusion
Our channel emphasizes transparency by encouraging users to verify and publish the contract code on Etherscan. MetaMask integration ensures secure transaction confirmation. Users can interact with the micropayment channel on the Ethereum testnet and use it to sent testnet Ethereum to trusted users. <br>
In essence, this method is a user-friendly guide for experimenting with micropayment channels on the Ethereum test network. With further testing, this framework can be expanded to be deployed on the Ethereum blockchain and be used for real transactions among trusted parties.
