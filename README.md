﻿# BlockSizeDebate

Adding to this document.
=========

This document is a work in progress. 
If you are interested in adding to or editing this document please fork it, make your changes and create a pull request.


Argument 1 Pro: Increased Transaction Throughput
=========

The chief argument for the increase in the maximum blocksize is to help the protocol address scalability issues, specifically by raising the total throughput of the Bitcoin network from its current ~3 tps (transactions per second) to something higher. This is most often attributed to an expected spike in adoption.

### Counter Argument 1.1: Other Scaling Solutions

**1.1a Off-Chain Third Parties**<a name="Offchain"></a>

Of the listed solutions, this is the only one that is implemented today. The use of such Third Parties could significanly reduce both the rate of blocksize increase and the average blocksize itself by reducing the number of on-blockchain transactions, and by condensing the number of inputs/outputs used.

*1.1a.1 Security Concerns of Off-Chain Third Parties*

However, opening up to third parties allows them to potentially  steal from you, and have your funds more easily hacked.<sup>[1](#footnote1)</sup> 

*1.1a.2 Privacy Concerns with Off-CHain Third Parties*

This allows for third parties to more easily collect information on you, and leak<sup>[2](#footnote2)</sup> it. Not only does this open up Bitcoin to regulatory bodies, but also hackers.

* Counter Argument 1.1a.1/2: Alternative distrubuted trust systems that checkpoint to the blockchain

Side chains, and side-graphs and other distributed trust networks that may not have the same level of security but are sufficient for large numbers of small transactions should mitigate any security and privacy concerns.   There are many good examples of alt coins that have solved "speed" issues at the expense of security.   Done right, a burn-and-code merger with an alt coin could grow the user base, allow for side-chain scaling and resolve security and privacy issues.  See below for more side-chain discussion.

**1.1b OpenTransactions**

Content pending research...

**1.1c Sidechains**

Content pending research...

**1.1d Lightning Networks/StrawPay**

Each of these are decentralized versions of the above, designed to reduce the amount of trust needed. Using payment channels allows it to use much less room on the blockchain, however, leading to a higher overall transaction rate.

*1.1d.1 Security Concerns*

Like with [Off-Chain Third Parties](#Offchain), there are often security concerns sited, such as the ability to steal other parties' funds from Strawpay channels.<sup>[3](#footnote3)</sup>

* Counter Argument 1.1d.1.1: This is impossible with Lightning network.  Hubs cannot spend funds.

*1.1d.2 No Current Implementation*

Because there is no current implementation of it, there is no way to be certain this system is a workable solution.

* Counter Argument 1.1d.1.1: Lightning has been implemented and has been tested.

Argument 2 Con: Miners/Full Nodes Cannot Handle Expansion
=========

Pools and Miners in some places of the world have difficulty connecting to some portions of the Internet.<sup>[4](#footnote4)</sup> These barriers of entry would grow larger if the maximum bandwidth of the network increases. In some places larger maximum blocksizes may make it so that they never catch up to the network, further pressuring the centralization of nodes and hashrate. Though not a Bitcoin protocol issue, it is unclear how the increase in maximum blocksize might effect existing hardware based on older maximum blocksize assumption. 

### Counter Argument 2.1: Resource Impact not Immediate

Because the change is only made to the *maximum* blocksize, it would not introduce an immediate resource impact. This time gap would also give time to implement several bandwidth saving solutions that have been created/theorized specifically to reduce these problems.

* Counter-counter argument 2.1.1: Miners mining large blocks will be able to sweep in more low-fee transactions, collecting fees that currently expire out of the mempool.   This can increase the number of transactions per block immediately.

### Counter Argument 2.2: Decreased node-count is not necessarily increased Centralization

Because we would have to trade this off (currently) with [Off-Chain Third Parties](#Offchain), that is also an increase in centralization. So the question is more "Which increases *overall* decentralization?" instead of "Will this decrease decentralization?".

* Counter-counter argument 2.2.1: Lightning network and side chains can, should and most likely will be equally decentralized.

### Counter Argument 2.3: Several Large Miners Have Agreed To Adopt A Change

*2.3.1: Several have also spoken against large changes*<sup>[5](#footnote5)</sup>

### Counter Argument 2.4: Moore's Law (and its companion laws) will support this in the future

*2.4.1: Trusting future hardware innovation is a risky move*

Especially as Bitcoin is supposed to serve *all*, some of which has not yet experienced the growth in bandwidth predicted by Nielsen's Law. This argument may work for storage (and thus far has seemed to), but propogation time of blocks, as well as total download time, will likely outstrip Nielsen's law with any major increase.

### Counter Argument 2.5: Satoshi Predicted Node Centralization<sup>[6](#footnote6)</sup>

*2.5.1: Should we really trust the opinion of one person from 5 years ago?*


Argument 3 Pro: The Limit Was Intended As A Temporary Measure
=========

### Counter Argument 3.1: The Limit Will Provide Fee Pressure

### Counter Argument 3.2: Nothing has been done to fix the original problem since<sup>[7](#footnote7)</sup>


Argument 4 Con: Hardforks Are Difficult
=========

The less notice there is before a hard fork, the more likely it is to fracture the network into competing chains.

### Counter Argument 4.1: The last hardfork increasing the block size to 1 MB was performed with merely 2 months notice.<sup>[7](#footnote7)</sup>

* Counter-counter argument 4.1.1: The last hard fork was not contentious.

### Counter Argument 4.2: The Hardfork Can Be Used To Make Other Useful Changes


Argument 5 Pro: Increases Cost Of Transaction Flooding Block Monopolization Attack
=========

The attack considered here is one in which the attacker generates a large number of transaction fees with high enough transaction fees so that the attack transactions will use all avaliabl;e block space preventing non-attacker transactions from being confirmed. The bitcoin wiki refers to this attack as a transaction flooding<sup>[8](#footnote8)</sup>.

This can be shown with the following scenario:<sup>[9](#footnote9)</sup>

Assume blocks are currently 90% full, and fees are 1 unit per kB. At the current blocksize it would take 1,200 units/hour to block 10% of transactions, and 10,000 units/hour to block *all* transactions.

Under a new blocksize (let's assume 20MB), it would take 115,200 units/hour to block 10% of transactions, and 120,000 to block all transactions.

This is a simplified model that does not take fee markets into account, but it would make transacting much more difficult whether fee markets were used or not.

### Counter Argument 5.1: Reduces the cost of a UTXO-based DoS Attack

Increasing the blocksize would allow faster bloating of the UTXO database.<sup>[9](#footnote10)</sup> Because the ability to change this scales roughly linearly to block size, increasing the blocksize increases the potential bloat rate from a bad actor. This reduces the ability to run a full node significantly, as RAM is an expensive resource to use compared to disk space.

*5.1.1 The effect of this can be dramatically reduced by storing the UTXO database on disk,<sup>[11](#footnote11)</sup> and by storing it more efficiently.*

Argument 6 Con: When Would A Hardfork Occur?
=========

Nearly any automated solution will have problems with it, so how can we solve those problems?

### Counter Argument 6.1: Predefined block number

After a certain block number, raise the maximum blocksize to X. This allows for a step function as well, but that is not what is being discussed here.

*6.1.1 This has no way to measure if it would fracture the network*

### Counter Argument 6.2: Adoption threshold

If X% of the previous 1000 blocks have a "v.new" flag, raise the limit.

*6.2.1 This puts a lot of power into the hands of miners*

### Counter Argument 6.3: A Combination Approach

If the block number is greater than X, and Y% of the previous 1000 blocks have the "v.new" flag, raise the blocksize limit<sup>[10](#footnote10)</sup>.


Argument 7 Meta: Dynamic Block size limits
=========

Allow the ability for Bitcoin to dynamically determine block size limits in a method similar to how Bitcoin dynamically regulates hash rate<sup>[12](#footnote12)</sup>. 

### Counter Argument 7.1: Formula Manipulation

Any set formula can be manipulated by attackers and miners, making the network more fragile.

### Counter Argument 7.2: Fine Tuning

Any formula will by definition create political decisions. Most proposed formulas are using the median block size, making a simple majority decide to raise or lower the block size. Problem with this is that because most blocks are found in less than ten minutes<sup>[13](#footnote13)</sup>, the median block size will by necessity be smaller than the mean block size (blocks after more time are more likely to have a transaction backlog).

If you use the proposed multiplier (Max_size = 2 * median (last 144 blocks)), then you have more pressure to smaller blocks (rather than the 50% + 1 it was proposed as).

### Counter Argument 7.3: Possible Disagreements Caused By Short-Term Forks

There is a ***small*** possibility of the following scenario:

A node accepts a block which pushes the new Max_size down to 749kB. This node then recieves a longer chain (2 blocks) where the first has a size of 750kB. The node would then reject the longer chain because of the Max_size from the first node, making the possibility of automatic, accidental hard forks.

*7.3.1: Calculate based on previous blocks*

Simple solution to the above would be to calculate the hashrate based on [x-6,x-150), where x is the current height.


Argument 8 Con: A Block Size Increases Would Lead to a Maximum Cap Increase
=========

Source: [1](https://twitter.com/jonmatonis/status/611844197331693568), [2](https://medium.com/@twobitidiot/the-21mm-btc-soft-cap-71e14cd09946), [3](https://medium.com/@anarchoass/economic-concerns-over-the-bitcoin-xt-hard-fork-203dbb4f67c6)

Increasing the block size with the goal of scaling the blockchain is the same reasoning someone would argue for an increase in the maximum 21 million block limit.

### Counter Argument 8.1: No Is Sugesting That

No one advocating for a rise in the block size is advocating for a raising the block limit.

### Counter Argument 8.2: Sure, on an Altcoin Alterative

Any change on the total block limit would amount to an altcoin.

### Counter Argument 8.3: The Block Limit is Sacrosanct.

The block limit is regarded as too important or valuable to be interfered with.

### Counter Argument 8.4: Slippery Slope argument

Pointing this out is sufficient to logically counter the argument.


Evidence 
=========

1. [Bitcoin Network Capacity Analysis – Part 1: Macro Block Trends](https://tradeblock.com/blog/bitcoin-network-capacity-analysis-part-1-macro-block-trends)

Argument 9: The majority of users support increasing block size
=========

Currently there are Segregated Witness, which raises the block size to 4MB, Bitcoin Unlimited which has an unknown size increase based on handing power to miners to make the decision, and Bitcoin Classic, which raises it to 2MB.  None of these has garnered even a simple majority of support, let alone the 95% or 75% needed to activate.   However, combined, the clear majority of miners support a block size increase: https://coin.dance/blocks

References
=========

<a name="footnote1">1</a>: CoinDesk, [http://www.coindesk.com/coinbase-security-concerns-amid-theft-reports/](http://www.coindesk.com/coinbase-security-concerns-amid-theft-reports/)

<a name="footnote2">2</a>: CoinDesk, [http://www.coindesk.com/coinbase-denies-reports-data-breach-addresses-security-concerns/](http://www.coindesk.com/coinbase-denies-reports-data-breach-addresses-security-concerns/)

<a name="footnote3">3</a>: Mike Hearn, [https://medium.com/@octskyward/the-capacity-cliff-586d1bf7715e#3555](https://medium.com/@octskyward/the-capacity-cliff-586d1bf7715e#3555)

<a name="footnote4">4</a>: Wikipedia, [http://en.wikipedia.org/wiki/Internet_in_China#Structure](http://en.wikipedia.org/wiki/Internet_in_China#Structure)

<a name="footnote5">5</a>: Chun Wang, [http://sourceforge.net/p/bitcoin/mailman/message/34157036/](http://sourceforge.net/p/bitcoin/mailman/message/34157036/)

<a name="footnote6">6</a>: Satoshi Nakamoto, [https://bitcointalk.org/index.php?topic=532.msg6269#msg6269](https://bitcointalk.org/index.php?topic=532.msg6269#msg6269)

<a name="footnote7">7</a>: Luke-Jr, [http://www.reddit.com/r/Bitcoin/comments/38wpjn/i_know_transactions_per_second_is_a_sore_spot_but/cryzi6v?context=3](http://www.reddit.com/r/Bitcoin/comments/38wpjn/i_know_transactions_per_second_is_a_sore_spot_but/cryzi6v?context=3)

<a name="footnote8">8</a>: Bitcoin Wiki,
[https://en.bitcoin.it/wiki/Flood_attack](https://en.bitcoin.it/wiki/Flood_attack)

<a name="footnote9">9</a>: /u/IntroShine, [http://www.reddit.com/r/Bitcoin/comments/37790q/some_say_raising_the_blocksize_from_1mb_to_20mb/](http://www.reddit.com/r/Bitcoin/comments/37790q/some_say_raising_the_blocksize_from_1mb_to_20mb/)

<a name="footnote10">10</a>: /u/sheepiroth, [http://www.reddit.com/r/Bitcoin/comments/37790q/some_say_raising_the_blocksize_from_1mb_to_20mb/crkcu6j](http://www.reddit.com/r/Bitcoin/comments/37790q/some_say_raising_the_blocksize_from_1mb_to_20mb/crkcu6j)

<a name="footnote11">11</a>: Gavin Andresen, [http://gavinandresen.ninja/utxo-uhoh](http://gavinandresen.ninja/utxo-uhoh)

<a name="footnote12">12</a>: Washington Sanchez, [https://twitter.com/drwasho/status/607687507627548672](https://twitter.com/drwasho/status/607687507627548672)

<a name="footnote13">13</a>: Matt Springer, [http://scienceblogs.com/builtonfacts/files/2014/01/bitcoin2.png](http://scienceblogs.com/builtonfacts/files/2014/01/bitcoin2.png)

