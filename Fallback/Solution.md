
# FallBack

In the FallBack challenge, we have two challenges to beat the level:

1. Claim ownership of the contract
2. Reduce its balance to 0

![alt text](image1.png)

![alt text](image2.png)

## Claim Ownership

The owner of the contract is mentioned at three places - the constructor, the contribution() function and receive() function.
We cannot use the constructor to change the contract address as it is executed only once and holds the assdress of the deployer of the contract. 

Hence, let us take a look at the contributor() and receive() function which can be helpful in chnaging the owner of the contract. 

The owner of the contract has contributed 1000 ether as viewed in the contructor. Also, we may need to contributed more than 1000 ether to change the ownership of the contract using the contribute() function.

The receive() function has minimal requirements - msg.value>0 and contributions[msg.sender]>0. Hence, we call the contribute() function fulfilling the requirement - msg.value < 0.001 ether and contribute 1 wei. Hence, the contributions[msg.sender]>0 requirement is fulfilled.

Next, we call the contract and send 1 wei such that msg.value >0 condition is fulfilled. 

Now, we have the ownership of the contract

## Reduce balance to 0

Since we have the ownership, we call the withdraw() function which can be called only by the owner due to the modifier onlyOwner() and transfer all the funds.

## Steps for the above challenge 
1. Call the contribute function and send 1 wei
2. Send 1 wei to the contract.
3. Ownership of the contract is claimed.
4. Use the withdraw() functiont to transfer funds.