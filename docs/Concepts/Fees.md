# Fees on Terra

There are two types of Terra transaction fees: [gas fees](#gas) and [stability fees](#stability-fees).

## Gas fees

[Gas](./glossary.md#fees) is a computational fee that covers the cost of processing a transaction. Gas is estimated and added to each transaction in Terra Station. Any transaction that does not contain enough gas will not process.
Gas on Terra works differently than it works on other blockchains:

- Validators can set their own minimum gas fees.
- Most transactions will estimate more than the minimum amount of gas, ensuring the transaction gets completed.
- Unused gas is not refunded.
- Transactions are not queued based on gas amounts, but in the order received.

For an in-depth explanation of how gas fees are calculated, visit the [terrad reference](/Reference/terrad/#fees) page.

To view current gas prices in your browser, visit the [gas prices](https://fcd.terra.dev/v1/txs/gas_prices) FCD page.

## Stability fees

Stability fees are often referred to as taxes and come in two types: the Tobin tax and spread fees.

**Tobin tax**: A percentage fee added to any swap between Terra stablecoins. The rate varies, depending on each Terra stablecoin denomination. For example, while the rate for most denominations is .35%, the rate for MNT is 2%. To see the rates, [query the oracle](/Reference/terrad/subcommands.html#query-oracle-tobin-taxes). Taxes for all denominations are capped at 1 STD.

The Tobin tax was created to discourage front-running the oracle and foreign exchange trading at the expense of users. For more information on the implementation of the Tobin tax, read ["On swap fees: the greedy and the wise"](https://medium.com/terra-money/on-swap-fees-the-greedy-and-the-wise-b967f0c8914e).

**Spread fees**: A percentage fee added to any swap between Terra and Luna. The minimum spread fee is .5%. During times of extreme volatility, the market module adjusts the spread fee to maintain a [constant product](/Reference/Terra-core/Module-specifications/spec-market.html#market-making-algorithm) between the size of the Terra pool and the fiat value of the Luna pool, ensuring stability in the protocol. As the pools reach constant product equilibrium, The spread rate returns to a normal value.

For more information on spread fees, visit the [market module](/Reference/Terra-core/Module-specifications/spec-market.md).
