# Consensus USD (XUSD)

### Asset backed token

An asset backed token  1-to-1 backed and trustlessly redeemable for some other asset.

### How does this happen

In order to mint certain amount of an asset backed token one must deposit the same amount of the backing asset, and upon withdrawal of said asset the previously minted tokens are burnt.

### What is Consensus USD ? 

Consensus USD (XUSD) is similar to an asset backed token, but not exactly the same.

XUSD can be minted with more than one asset, specifically these and only these:
* DAI  (Multi Collateral Dai)
* BUSD (Binance USD)
* USDT (Tether USD)
* tUSD (True USD)
* USDC (USD Coin)

Anyone is able to mint XUSD by locking the same amount with any of these tokens.

These are all stablecoins supposed to be worth 1 USD, now this is not always the case and is where XUSD might be helpful.

### Market value

To each user who locks their stablecoin, XUSD is going to have the value that he/she deposited, since said user can redeem their stablecoin tokens with XUSD.

This means XUSD will tend to have an average value between these coins, thus providing more assurance to the user that the tokens he/she expected to be worth 1 USD do so.

If adopted XUSD could serve as a stabilizing force between stablecoins.

### Implications

Adoption of XUSD effects are interesting to think of, and potentially benefitial regarding assurance of value of a stablecoin. Some cases discussed ahead:

##### Case - Centralized coin (eg USDC) turns to be unbacked and looses value

Anyone who deposited other asset has their value secured since they can retrieve their assets with XUSD. This will alleviate the loss of a user who instead of holding USDC (just for the example) locked them to mint XUSD, since XUSD is going to have a higher market value because of the point mentioned before.

XUSD is benefitial for every user, mitigating losses for users whose deposited asset unexpectedly decreased in value, and allowing other users (who locked other coins) to profit by being able to retrieve their assets at a lower cost (because they can mint XUSD at a lower cost or buy it at lower market value).

##### Case - Unrestricted unbacked minting

What if someone gets a hold of a whitelisted valid centralized stablecoin control and mints tokens indefinetly, then he/she can also mint XUSD indefinetly, this is the above case taken to an extreme.

Market value of the corrupt token is going to plumet, so will XUSD, but again XUSD will be either benefitial or innocuous for everyone of its users, since users that locked an asset different from the corrupt token will be able to retrieve their assets at a lower cost (or the same if they holded XUSD), and users who deposited the corrupt token will at most loose the value which they trusted to the corrupt stablecoin, but probably less.

##### Case - DAI looses its peg and is worth 1.02 USD

In this case someone who previously minted and spent DAI would need to pay a premium in order to get back DAI to repay his/her loan and retrieve their collateral. Instead if the user had locked DAI and spent XUSD he/she can retrieve DAI at XUSD price.

##### Conclusion

XUSD helps providing further warranty to a user who expects tokens to be worth 1 USD.

### Code

XUSD is very simple, its just an ERC20 token with some added functionality

Valid stablecoins which can be used as collateral are hardcoded in the constructor (called once at contract creation)

```
    constructor() public {
        decimals = 18;
        totalSupply = 0;
        name = "Consensus USD";
        symbol = "XUSD";

        validStablecoins[0x6b175474e89094c44da98b954eedeac495271d0f] = 1; // DAI  (MC DAI       )
        validStablecoins[0xdAC17F958D2ee523a2206206994597C13D831ec7] = 1; // USDT (ERC20 Tether )
        validStablecoins[0x4Fabb145d64652a948d72533023f6E7A623C7C53] = 1; // BUSD (Binance USD  )
        validStablecoins[0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48] = 1; // USDC (USD Coin     )
        validStablecoins[0x0000000000085d4780B73119b644AE5ecd22b376] = 1; // tUSD (TrueUSD      )

    }
```

See mint and retrieve function [implementations](./ConsensusUSD.sol), with which one can mint XUSD and retrieve previously deposited
backing assets (burning XUSD)


### Contract

Deployed and verified on mainnet, see on etherscan[ TODO]()

### Purpose

I find it to be an interesting and potentially benefitial idea, though I don't think its going to be adopted at least as is, it might spark interesting debates or projects. Feel free to contribute or do with it whatever you want.

I don't have any special ownership over the contract nor benefit directly from this in anyway.

Also I'm looking for a job, if interested in knowing more about me please contact at mapozzi@itba.edu.ar