# VRF Balance Subscription Monitor | Chainlink Automation | Chainlink VRF

## I. About

Automatically top-up your VRF subscription balances using Chainlink Automation to ensure there is sufficient funding for requests.

## II. Pre-requisites

Install the chainlink contracts npm package using your preferred package manager

```
# via pnpm
$ pnpm add @chainlink/contracts
# via npm
$ npm install @chainlink/contracts --save
```

## III. How to utilize the Example

1. Deploy the VRFBalanceSubscriptionMonitor.sol - while deploying this, the constructor will expect the address of the VRFCoordinator on the given chain (Polygon Mumbai example: 0x7a1BaC17Ccc5b313516C5E16fb24f7659aA5ebed), the LINK token address for your chain (example: 0x326C977E6efc84E512bB9C30f76E30c160eD06FB ), Automation registry address (example: 0xE16Df59B887e3Caa439E0b29B42bA2e7976FD8b2) and minWaitPeriodSeconds as an integer which determines how long to wait until a subscription is funded.
2. Once deployed, call the setWatchList function and input your subscription IDs, specify the minBalance in Juels, and then the amount you would like to top up per refill in Juels.
3. Go to https://automation.chain.link and select custom logic. For the target contract address, enter the address of the contract you deployed in step 1
4. Fill in the rest of the fields and ensure that you send the appropriate amount of LINK in order to ensure the VRF subscription balance can be funded (checkData field can be left blank).
5. Deploy your upkeep once all fields are filled out

Now the Chainlink Automation network will watch your contract for the trigger parameters. If the VRF balance for your subscriptions falls below the minimum balance you specified, and upkeep will be triggered to fund the subscription!

> :warning: **Disclaimer**: This tutorial represents an educational example to use a Chainlink system, product, or service and is provided to demonstrate how to interact with Chainlink’s systems, products, and services to integrate them into your own. This template is provided “AS IS” and “AS AVAILABLE” without warranties of any kind, it has not been audited, and it may be missing key checks or error handling to make the usage of the system, product or service more clear. Do not use the code in this example in a production environment without completing your own audits and application of best practices. Neither Chainlink Labs, the Chainlink Foundation, nor Chainlink node operators are responsible for unintended outputs that are generated due to errors in code.
