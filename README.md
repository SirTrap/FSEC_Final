    In this project, I selected 3 different kinds of common Ethereum Network vulnerabilities. I developed 3 different sets of smart contracts and Javascript deployment code to implement these vulnerabilities in a hardhat local network and established ways to solve these vulnerabilities. The first vulnerability I focused on was reentrancy attacks. These attacks exploit the smart contracts which update their variables after making transactions. For example, for a banking smart contract, if a withdrawal function, first makes a transaction and then updates the balance status, this can allow malicious smart contracts to continuously send withdrawal requests draining the whole bank's funds. I implemented this exact example in the ReentrancyDeploy.js file and accompanying ReentrancyVulnerable.sol and ReentrancyAttacker.sol files. These kinds of attacks can be easily solved by switching the order of operations for variable updates and transactions. The second vulnerability I focused on was Denial of Service attacks. These attacks can vary from freezing the order of operations of a smart contract with transaction blocking code to forcing the smart contracts to spend incredible transaction fees, draining the contracts of gas. In my implementation, I created an auction scenario where the auction contract has a bidding function that requires transferring the money back to the last bidder before confirming the status of the new bidder. This caused a vulnerability that I exploited to freeze the auction process and ensure that the "cheating contract" always stays on top in bidding. Lastly, I implemented an Integer Underflow/Overflow vulnerability. This implementation was pretty straightforward where I used a similar banking smart contract with the reentrancy attack. The only difference was the integer values were limited to uint8 instead of uint256. This allowed small values like a single eth (10^18 wei) to overflow multiple times before getting rounded to zero. 
