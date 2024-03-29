# Smart_Contracts_With_Solidity

## Background
Your new startup has created its own Ethereum-compatible blockchain to help connect financial institutions, and the team wants to build smart contracts to automate some company finances to make everyone's lives easier, increase transparency, and to make accounting and auditing practically automatic!
Fortunately, you've been learning how to program smart contracts with Solidity! What you will be doing this assignment is creating 3 ProfitSplitter contracts. These contracts will do several things:

- Pay your Associate-level employees quickly and easily.
- Distribute profits to different tiers of employees.
- Distribute company shares for employees in a "deferred equity incentive plan" automatically.

## Files

AssociateProfitSplitter.sol -- Level 1 starter code.

## Instructions

This assignment has three levels of difficulty, with each contract increasing in complexity and capability. Although it is highly recommended you complete all three contracts, you are only required to solve one of the three contracts. Recommended to start with Level 1, then move forward as you complete the challenges. You can build all three with the skills you already have!


Level One is an AssociateProfitSplitter contract. This will accept Ether into the contract and divide the Ether evenly among the associate level employees. This will allow the Human Resources department to pay employees quickly and efficiently.

## Starting your project

Navigate to the Remix IDE and create a new contract called AssociateProfitSplitter.sol using the starter code for level one above.
While developing and testing your contract, use the Ganache development chain, and point MetaMask to localhost:8545, or replace the port with what you have set in your workspace.

Level One: The AssociateProfitSplitter Contract
At the top of your contract, you will need to define the following public variables:


employee_one -- The address of the first employee. Make sure to set this to payable.


employee_two -- Another address payable that represents the second employee.


employee_three -- The third address payable that represents the third employee.


Create a constructor function that accepts:


address payable _one


address payable _two


address payable _three


Within the constructor, set the employee addresses to equal the parameter values. This will allow you to avoid hardcoding the employee addresses.
Next, create the following functions:


balance -- This function should be set to public view returns(uint), and must return the contract's current balance. Since we should always be sending Ether to the beneficiaries, this function should always return 0. If it does not, the deposit function is not handling the remainders properly and should be fixed. This will serve as a test function of sorts.


deposit -- This function should set to public payable check, ensuring that only the owner can call the function.


In this function, perform the following steps:

- Set a uint amount to equal msg.value / 3; in order to calculate the split value of the Ether.
- Transfer the amount to employee_one.
- Repeat the steps for employee_two and employee_three.


Since uint only contains positive whole numbers, and Solidity does not fully support float/decimals, we must deal with a potential remainder at the end of this function since amount will discard the remainder during division.


We may either have 1 or 2 wei leftover, so transfer the msg.value - amount * 3 back to msg.sender. This will re-multiply the amount by 3, then subtract it from the msg.value to account for any leftover wei, and send it back to Human Resources.


Create a fallback function using function() external payable, and call the deposit function from within it. This will ensure that the logic in deposit executes if Ether is sent directly to the contract. This is important to prevent Ether from being locked in the contract since we don't have a withdraw function in this use-case.

![compile](https://user-images.githubusercontent.com/77086043/125851871-e4c9d125-5b64-4806-b44d-848c82ddaa51.PNG)


## Test the contract
In the Deploy tab in Remix, deploy the contract to your local Ganache chain by connecting to Injected Web3 and ensuring MetaMask is pointed to localhost:8545.
You will need to fill in the constructor parameters with your designated employee addresses.
Test the deposit function by sending various values. Keep an eye on the employee balances as you send different amounts of Ether to the contract and ensure the logic is executing properly.

![deploy_contract](https://user-images.githubusercontent.com/77086043/125851882-c20ab1bd-7edd-4fd2-b3e3-8f286d9a397c.PNG)

## Deploy the contracts to a live Testnet
Once you feel comfortable with your contracts, point MetaMask to the Kovan or Ropsten network. Ensure you have test Ether on this network!
After switching MetaMask to Kovan, deploy the contracts as before and copy/keep a note of their deployed addresses. The transactions will also be in your MetaMask history, and on the blockchain permanently to explore later.


![contract](https://user-images.githubusercontent.com/77086043/125852142-108ac650-2136-45f7-8174-145222ea3b02.PNG)

![contract_confirm](https://user-images.githubusercontent.com/77086043/125852169-8b56a920-1ea1-4bc1-8f10-05800060d389.PNG)

![contract_complete](https://user-images.githubusercontent.com/77086043/125852179-ac642555-baca-4510-b8ba-5c9522e9c860.PNG)

![confirm_deposit](https://user-images.githubusercontent.com/77086043/125852194-7545614f-1911-4585-a334-e92f4b1efb53.PNG)

![deposit_confirm](https://user-images.githubusercontent.com/77086043/125852217-31f8af5e-3fd2-4183-89be-12641669c460.PNG)

![acct1](https://user-images.githubusercontent.com/77086043/125853066-36ae54ae-e1f6-475a-b47a-e7f4e4988742.PNG)

