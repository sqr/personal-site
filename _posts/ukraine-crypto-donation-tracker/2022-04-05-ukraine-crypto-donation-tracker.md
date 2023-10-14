---
layout: post
title: "Ukraine Crypto Donation Tracker"
date: 2022-04-05 09:29:20 +0700
categories: software crypto
usemathjax: true
---

Tracks and plots funds in the official Ukranian BTC and ETH addresses. You can check the project [live](https://ukraine-crypto-tracker.arturobracero.com/){:target="\_blank"}{:rel="noopener noreferrer"} and view the [live](https://github.com/sqr/ukraine-crypto-donation-tracker/){:target="\_blank"}{:rel="noopener noreferrer"}

Soon after the invasion of Ukraine started, the official Twitter account [announced](https://twitter.com/Ukraine/status/1497594592438497282){:target="\_blank"}{:rel="noopener noreferrer"}

that they would accept donations of cryptocurrencies to aid in their defense. After the Minister of Digital Transformation, Mykhailo Fedorov, confirmed that this was legit, I thought it would be interesting to see how many people have donated. Would donators prefer ETH or BTC? What kind of ERC-20 tokens will they donate?

All these questions could be easily answered by checking different blockchain explorers, but not all on one site. After quickly checking that there APIs available for both Bitcoin and Ethereum blockchains, the project started, with the goal of completing it in less than 48 hours. Lets go!

The plan is simple: use two free APIs to gather information about the transactions, store the results in a database, and render the information on a chart.
Backend

The most important aspect to keep in mind as we approach data gathering is that the actual balance on the addresses is not important at all. Ukraine will cash out eventually and bring the balance down. We don’t want that reflected on the graph. All we care about are transactions that have these particular addresses as a receiver.

For bitcoin this is easy, as the [Blockstream API](https://github.com/Blockstream/esplora/blob/master/API.md){:target="\_blank"}{:rel="noopener noreferrer"} exposes this information as funded_txo_sum when querying specific addresses, as well as funded_txo_count.

Things get a little bit more complicated with Ethereum. Etherscan’s API only exposes the current balance or a list of all transactions, limited to 10.000 txs per query. Fortunately, they also store the block height of each transaction.

So the solution for ETH is to store on the database the last block height that has been checked, and next time we poll start on last block checked + 1. Check all transactions in that range and add them to the value last stored on the database.
Frontend
The frontend is an extremely basic react page without any particular styling framework. The most interesting part is the use of Rechart to display the data from MongoDB in a beautiful chart. The table for ERC-20 tokens is powered by React Table, an extremely easy to set up hook-based utility for React.
