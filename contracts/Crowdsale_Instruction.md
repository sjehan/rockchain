Rockchain Crowdsale

- ENS rockchain.eth
- Crowdsale Address 0xb67732ca658b9f7f6c46865865fd990d634c8766

The smart contract has a certain number of advanced features :

- Issue the ROK tokens, fully compliant with the ERC20 standard
- Implements the token distribution as described in the white paper
- Allows funding in Ether
- Allows full traceability of the contributions being in ETH and the corresponding ROK
- Funds are saved in a multisig wallet (3/5)
- Contributors protection in case where the mincap 18,000 ETH is not reached with a refund period of 45 days
- ROK Tokens will be claimed from the contributers at the end of the crowdsale
- Contributors who purchase more than 3 ETH of ROK tokens have to sign up on rockchain.org to provide informations and be listed on the KYClist that allow them to claim their ROK Tokens at the end of the crowdsale
- Contributors who purchase less than 3 ETH of ROK tokens can buy directly using the address rockchain.eth, but we would appreciate if they could let us know their emails using our online form "Buying less than 3 Eth of ROK Tokens: get the contract address"

Crowdsale process

The crowdsale contract is created and initialized with the follwing parameters :
address of the ROK token deployed contract , and a multisig wallet to receive the ETH collected.

The crowdsale starts when the current block is after the startDate and continue until all token are sold,
or the maxFundingGoal is reached, or the deadline (startDate + 30 days) is reached.

During the crowdsale, participants can contribute by sending ETH to the crowdsale contract address
with a minimum purchase of 0,1 ether. All this contributions are recorded in the smart contract,
thus ensuring full traceability and transparency.

At the crowdsale completion, if the ICO is successful, ROK token will be a fully ERC20 compliant token,
which will be issued once, with limited supply. The currency also supports « burning » which will destroy
un-sold tokens at the end of the crowdsale.

Each contributors have to claim the authorization to transfer their ROK tokens to another addresses when the crowdsale is over to prevent the creation of a second market during crowdsale period. However the authorization to transfer ROK tokens is allowed by the smart contract "Crowdsale.sol" to contributors who have been registered their ETH addresses in our web site only if the amount exceeds 3 ETH to be listed on the KYClist.  

The Contributors will be awarded balance based on their contribution if the ICO is successful. Otherwise, if the
minimun funding goal (18 000 ether) is not reached contributors can demand a refund over 45 days and keep their ROK Tokens as a gift for their contribution :
 - Backer call the "refund" function of the Crowdsale contract
 - Backer call the "withdrawPayments" function of the Crowdsale contract to get a refund in ETH

Or demand a partial refund over 45 days :
 - Backer call the "partialRefund" function of the Crowdsale contract with the partial amount of ETH to be refunded (value will be renseigned in WEI)
 - Backer call the "withdrawPayments" function of the Crowdsale contract to get a partial refund in ETH

ICO Contract Function Description:

Variable/Function | Purpose
--- | ---
`rateETH_ROK`|The number of ROK tokens issued per ETH
`minimumPurchase`|Minimum number of ETH accepted in a contribution transaction
`startDate`|The epoch timestamp representing the start date which the ICO officially begins accepting contributions
`deadline`|The epoch timestamp representing the end date of the ICO campaign
`refundeadline`|The epoch timestamp representing the end date of refund period in case of unsuccessful of ICO campaign
`minFundingGoal`|The minimum number of Ether that the ICO must receive in contributions in order to be considered "Successful"
`maxFundingGoal`|The absolute maximum number of Ether that the ICO contract will accept, if this number if reached, the ICO will end immediately and be declared a success.
`secondbonusdate `|The epoch timestamp representing the start of the second period bonus (5%)
`ROKtoken`|The Address of the ERC20 ROK Token Contract
`Escrow`|The Address of our Escrow Provider. This is the hard-coded address that all final Ether will be sent to upon Successful completion of the ICO
`Bounty`|The Address dedicated to bounty services. This is the hard-coded address that all final Ether will be sent to upon Successful completion of the ICO
`Owner`|This is the Address of the Owner Account. This is where the ROK Tokens will be sent when minted.
`balances`|Ether Balance for each contributor, we can look back and determine what the balance was easily.
`balancesRokToken`|Rokt token Balance for each contributor, we can look back and determine what the balance was easily.
`savedBalance`|The final Ether Balance of the Contract. This is saved so that once withdrawls happen, we can look back and determine what the balance was easily.
`contribute()`|send in contribution (send ETH along with execution)
`isStarted`|Boolean (True or False) is the ICO started?
`isComplete`|Boolean (True or False) Is the ICO Complete?
`isSuccessful`|Boolean (True or False) Is the ICO past it's minimum goal?
`checkEthBalance(address)`|Returns the number of Ether Balance held for account
`checkRokBalance (address)`|Returns the number of Token Balance held for account
`checkRokSold`|The total number of Tokens Sold via contributions
`checkRokTeam`|The total number of Tokens being issued to the team
`checkRokBounty`|The total number of Tokens being issued for bounty
`percentOfGoal`|The Percentage of the Minimum Goal we have achieved.
`RefundPeriodStart`|This function check if the refund period is start
`RefundPeriodOver`|This function check if the refund period is over
`KYClist`|List of validated ROK token buyers addresses
`payout`|This function is called to pay out the Creator (if ICO was a success, Ether is sent to escrow, if ICO was not a success, all Tokens sent to creator address).
`getBonus`|This function allow to calculate the related contributor bonus during the ICO campaign. 10% for the first 5 days period and 5% for the second 5 days period.
`payTokens`|This function is called to pay tokens to contributors even if the ICO wasn’t a success. Rockchain will be used ROK okens for our services
`payTeam`|This function is called to pay tokens to the team and related advisors for their contributions.
`Refund`| This function is called by each contributors to refund them in case if the minFundfingGoal is not reached.
`partialRefund`| This function is called by each contributors to demand a partial refund in case if the minFundfingGoal is not reached (value will be renseigned in WEI).
`updateKYClistByAddress`| This function is called to update the KYClist of allowed addresses only by the owner 
`updateKYClist`| This function is called to check if a specific address is allowed to transfer their tokens.
`Claim`| This function is called by each contributors to claim the autorization to transfer their tokens. 

## Contract ABI
```
  "abi": [
    {
      "constant": true,
      "inputs": [],
      "name": "totalPayments",
      "outputs": [
        {
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "startDate",
      "outputs": [
        {
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "savedBalanceToken",
      "outputs": [
        {
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "minFundingGoal",
      "outputs": [
        {
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "checkRokBounty",
      "outputs": [
        {
          "name": "totalbounty",
          "type": "uint256"
        }
      ],
      "payable": false,
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [],
      "name": "refundPeriodStart",
      "outputs": [
        {
          "name": "",
          "type": "bool"
        }
      ],
      "payable": false,
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "deadline",
      "outputs": [
        {
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [],
      "name": "unpause",
      "outputs": [],
      "payable": false,
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "checkRokSold",
      "outputs": [
        {
          "name": "total",
          "type": "uint256"
        }
      ],
      "payable": false,
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "maxFundingGoal",
      "outputs": [
        {
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "isStarted",
      "outputs": [
        {
          "name": "",
          "type": "bool"
        }
      ],
      "payable": false,
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [],
      "name": "refund",
      "outputs": [],
      "payable": false,
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "paused",
      "outputs": [
        {
          "name": "",
          "type": "bool"
        }
      ],
      "payable": false,
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [],
      "name": "withdrawPayments",
      "outputs": [],
      "payable": false,
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [],
      "name": "payout",
      "outputs": [],
      "payable": false,
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "rateETH_ROK",
      "outputs": [
        {
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "savedBalance",
      "outputs": [
        {
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [],
      "name": "pause",
      "outputs": [],
      "payable": false,
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "team",
      "outputs": [
        {
          "name": "",
          "type": "address"
        }
      ],
      "payable": false,
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "owner",
      "outputs": [
        {
          "name": "",
          "type": "address"
        }
      ],
      "payable": false,
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "bounty",
      "outputs": [
        {
          "name": "",
          "type": "address"
        }
      ],
      "payable": false,
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [
        {
          "name": "_contributor",
          "type": "address"
        }
      ],
      "name": "checkEthBalance",
      "outputs": [
        {
          "name": "balance",
          "type": "uint256"
        }
      ],
      "payable": false,
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "tokenBalance",
      "outputs": [
        {
          "name": "balance",
          "type": "uint256"
        }
      ],
      "payable": false,
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "minimumPurchase",
      "outputs": [
        {
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [],
      "name": "refundPeriodOver",
      "outputs": [
        {
          "name": "",
          "type": "bool"
        }
      ],
      "payable": false,
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "isComplete",
      "outputs": [
        {
          "name": "",
          "type": "bool"
        }
      ],
      "payable": false,
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "refundeadline",
      "outputs": [
        {
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "checkRokTeam",
      "outputs": [
        {
          "name": "totalteam",
          "type": "uint256"
        }
      ],
      "payable": false,
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "rok",
      "outputs": [
        {
          "name": "",
          "type": "address"
        }
      ],
      "payable": false,
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [],
      "name": "contribute",
      "outputs": [],
      "payable": true,
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [
        {
          "name": "",
          "type": "address"
        }
      ],
      "name": "payments",
      "outputs": [
        {
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "escrow",
      "outputs": [
        {
          "name": "",
          "type": "address"
        }
      ],
      "payable": false,
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "percentOfGoal",
      "outputs": [
        {
          "name": "goalPercent",
          "type": "uint16"
        }
      ],
      "payable": false,
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "isSuccessful",
      "outputs": [
        {
          "name": "",
          "type": "bool"
        }
      ],
      "payable": false,
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [
        {
          "name": "newOwner",
          "type": "address"
        }
      ],
      "name": "transferOwnership",
      "outputs": [],
      "payable": false,
      "type": "function"
    },
    {
      "inputs": [
        {
          "name": "_roktoken",
          "type": "address"
        },
        {
          "name": "_escrow",
          "type": "address"
        }
      ],
      "payable": false,
      "type": "constructor"
    },
    {
      "payable": true,
      "type": "fallback"
    },
    {
      "anonymous": false,
      "inputs": [
        {
          "indexed": true,
          "name": "_contributor",
          "type": "address"
        },
        {
          "indexed": true,
          "name": "_value",
          "type": "uint256"
        },
        {
          "indexed": true,
          "name": "_tokens",
          "type": "uint256"
        }
      ],
      "name": "Contribution",
      "type": "event"
    },
    {
      "anonymous": false,
      "inputs": [
        {
          "indexed": true,
          "name": "_receiver",
          "type": "address"
        },
        {
          "indexed": true,
          "name": "_value",
          "type": "uint256"
        },
        {
          "indexed": true,
          "name": "_timestamp",
          "type": "uint256"
        }
      ],
      "name": "PayEther",
      "type": "event"
    },
    {
      "anonymous": false,
      "inputs": [
        {
          "indexed": true,
          "name": "_value",
          "type": "uint256"
        },
        {
          "indexed": true,
          "name": "_timestamp",
          "type": "uint256"
        }
      ],
      "name": "BurnTokens",
      "type": "event"
    },
    {
      "anonymous": false,
      "inputs": [],
      "name": "Pause",
      "type": "event"
    },
    {
      "anonymous": false,
      "inputs": [],
      "name": "Unpause",
      "type": "event"
    }
  ]
```
