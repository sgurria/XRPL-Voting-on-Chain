# XRPL-Voting-on-Chain
"XRPL Voting on Chain" is a GitHub repository containing a decentralized application built on the XRP Ledger that allows users to participate in community-driven decision-making through secure and transparent on-chain voting. 

## Voting System
This code implements a voting system using the XRP Ledger. The system uses a JsonRpcClient to communicate with the XRP Ledger and the xrpl library to generate wallets, transactions and submit them to the network.

The system has access to the voters' information in a database called voter_db. Each user has a wallet and an OTP (one-time password) associated with their account. It also stores the last time a user voted and a flag to indicate whether a user has voted or not. The system defines a time window for voting, from a start time to an end time and a user can vote only once during this time window.

The system defines two functions to authenticate users and check if they can vote. The authenticate_user function checks if the username and OTP are valid. The can_vote function checks if the user can vote based on the time window and whether the user has already voted or not.

The cast_vote function allows a user to vote by sending a Payment transaction with a memo that contains the candidate's name. The function also checks if the candidate is valid and signs the transaction with the user's wallet. The transaction is then submitted to the network using send_reliable_submission function. The function also updates the voter_db to indicate that the user has voted.

The system tests the voting system by prompting the user to enter their username and OTP, and then calling the cast_vote function if the user is authenticated and can vote.

## Dependencies
The system depends on the following libraries:
- nest_asyncio
- Xrpl
- time
- banascii

## Installation
To install the dependencies, run the following command:

pip install nest_asyncio, xrpl

## Usage
To use the system, import nest_asyncio and xrpl and call the apply function to enable asynchronous I/O in a synchronous context. Then, import the required libraries: JsonRpcClient and generate_faucet_wallet from the xrpl.clients and xrpl.wallet modules, respectively.

Next, create a network client by instantiating a JsonRpcClient object with the URL of the XRP Ledger server. The system uses the altnet (alternative test network) for testing, but you can use the mainnet or any other test network.

Generate the wallets for each user and store their information in the voter_db dictionary. Create candidates and set up the time window for voting.
Call the cast_vote function to allow a user to vote. The function prompts the user to enter the candidate's name and checks if the candidate is valid. If the candidate is valid, the function creates a Payment transaction with a memo that contains the candidate's name, signs the transaction with the user's wallet, and submits it to the network using the send_reliable_submission function.

To test the voting system, prompt the user to enter their username and OTP, and call the cast_vote function if the user is authenticated and can vote.
