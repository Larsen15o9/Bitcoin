Here, we will explain how mining works, how NiceHash works, how do you get paid and how can you monitor whether your mining system is fully optimized and working with complete reliability. It will also quickly teach you how to evaluate other miners and compare them to NiceHash QuickMiner.


### Cryptocurrency mining on NiceHash (very simple version)
Cryptocurrency mining is nothing else but performing calculations of hash values - it is an one way mathematical function which calculates output `Xa` out of input `Ia`. Each input `Ia` also has a special number appended, which consist of two parts: `Ns` (nonce-server) and `Nm` (nonce-miner). Your miner gets _job_ from NiceHash server which contains `Ia` and `Ns`. Your miner chooses (usually just doing iteration ++1) `Nm` for each calculation and then calculates output according to the following formula: 

`Xa = HASH(Ia + Ns + Nm)`

`Xa` is a very big number. If this number is smaller than `Ta` (also provided in _job_ from NiceHash), then your miner has found a **share** and corresponding `Nm` is sent to NiceHash as _proof-of-work_. This proves that your miner actually performed work to _find_ appropriate **nonce**. Because HASH is an one way function, there is no other possibility for miner but to try many **nonces**. Mining with 60 MH/s means that your miner is trying 60 million of HASH calculations per second.


### Shares
When your miner is lucky to find appropriate **nonce** `Nm`, it packs it together with ID of the _job_ and sends to the NiceHash server as **share**. NiceHash can then:
* accept your share as valid,
* reject your share as invalid - wrong calculation or
* reject your share as stale - it came too late.


### Accepted shares
Your found **nonce** is correct (there was no mistake in calculation) and the share arrived to the server on time (it was not too late). Usually you can notice accepted shares when miner console window informs you, for example:

> net | daggerhashimoto | Share #114 accepted (31 ms)

You get paid some fixed amount of BTC for this share. The amount of BTC the share is worth depends on two factors:
* how **hard** the work was and 
* how much buyers are paying currently.

We will explain only the first one, because second one is part of the NiceHash confidential proprietary algorithm. The **hardness** of work is defined by `Ta` which is calculated out of `(1 * algo_const) / Da`. `Da` is difficulty. The higher the difficulty, the smaller is number `Ta` and it is harder to guess appropriate `Xa` which would be smaller than `Ta`. **In fact, if we increase difficulty by factor 2, the number `Ta` becomes smaller by factor 2 and your miner consequently finds only half as many shares as before.** Each _job_ has certain `Da` attached (defined by the NiceHash server). When your miner finds share for _job_ that has `Da` increased by x2, then this share also has **hardness** factor x2 and is worth twice as much as share found for _job_ with `Da` x1.

NiceHash adjusts `Da` (difficulty) dynamically according to your miner's speed:
* If your miner is faster and is submitting shares more frequently than expected, NiceHash increases difficulty.
* If your miner is slower and is submitting shares rarely, then Nicehash decreases difficulty.

Therefore it does not matter how many shares your miner finds, but rather how many weighted shares your miner finds. This value can be best represented with a two dimensional graph of **accepted speed**.

> We have 6 rigs with following miner speeds: 587 MH/s, 409 MH/s, 261 MH/s, 215 MH/s, 214 MH/s and 121 MH/s. The total speed of all rigs is 1807 MH/s.
>
> When we check average speed over longer period of time (at least several hours for multiple/big rigs and several days for small/single rigs), the speed has to match to our total rig speed as visible on the chart below. The total accepted speed on the chart is lower, because we need to account in 1.14 % reject rate. At the speed of ~1800 MH/s, that is approx. 20 MH/s. When we deduct 20 MH/s from our total rig speed of 1807 MH/s, we get 1787 MH/s. Our chart is showing us 1791 MH/s which is 4 MH/s more - this can be attributed to _better luck_ during that period of time.

![Chart - accepted speed](https://github.com/nicehash/NiceHashQuickMiner/blob/main/images/chart_all.png?raw=true)

**IMPORTANT!** Accepted speed on NiceHash is the most important chart. It tells you how your miner is **actually** performing. If your chart is showing greatly depressed numbers compared to what your miner is displaying in console, then you are being **cheated out**! It is a well known fact that some devfee miners artificially inflate console-speed numbers to attract more customers and in most cases they do not deduct devfee speed. So you may get impression that your miner is performing great with high speed, but on NiceHash, your accepted speed chart shows different story. **It does not matter what speed your miner reports, but what accepted speed chart on NiceHash says - you are paid directly according to that!**


### Rejected shares - _share above target_
When you get this type of rejected share, it means that your miner provided **wrong or invalid** calculation and as a consequence wrong result. Usually, this happens if you overclock VRAM too much - memory is not stable anymore and errors happen. You should not have many of these type of rejects (perhaps only one or two shares here and there). In Rig Manager, you can filter out all other shares and view only **average percentage of rejected shares of type _share above target_**.

> In our example, we had only few shares of that type rejected, so the chart has only two spikes and average percentage is so low that, when rounding it to two decimals, it shows 0%. This shows that our rigs are properly tweaked and tuned not to produce too many rejects of type _share above target_.

![Chart - rejected speed - target](https://github.com/nicehash/NiceHashQuickMiner/blob/main/images/chart_r_target.png?raw=true)


### Rejected shares - _job not found_ (stale)
This type of reject is unavoidable. It depends on many factors, including your network latency to chosen NiceHash server. That's why it is important to choose the one with the lowest latency as [instructed here](https://github.com/nicehash/NiceHashQuickMiner/wiki/Tips-&-tricks#1-choose-your-service-location-to-improve-your-latency-and-reduce-number-of-stale-shares). It can also depend on your chosen miner software. A miner software that is sending old shares for jobs that are not valid anymore, will generate you stale shares.

> Our stale share ratio is 0.97%. This means that we are losing about 1% of possible income. With approx. 1800 MH/s of total rig speed, this means we are _wasting_ (or throwing away) approx. 18 MH/s of it. 

![Chart - accepted speed - stale](https://github.com/nicehash/NiceHashQuickMiner/blob/main/images/chart_r_stale.png?raw=true)

But, why do jobs become stale anyway? Your miner is performing work for a blockchain - there is a new block every few minutes or seconds. When that happens, previous jobs become stale and cannot be used anymore. In Excavator, when job has suffix `(clean)` all previous jobs are stale.

And what is the point of shares? A share with extremely high difficulty which is above **network difficulty of blockchain** is the solution that creates new block on the blockchain.