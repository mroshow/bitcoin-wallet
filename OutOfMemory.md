Some of you experience out of memory problems. This surfaces in seemingly random crashes of the app. In extreme cases it crashes always on launch.

One part of the problem is a small heap size. Even if your device got more RAM in total, Android limits the heap that can be used by an individual app. The limit can be as low as 32 MB for old devices or as high as 192 MB.

The more important part is your usage pattern. Bitcoin Wallet (and to some extent Bitcoin in general) works best with amounts of 0.01 BTC or larger and a little bit of balance between receiving and spending. If you never spend you will accumulate unspent transactions (more precisely: unspent outputs) that will clog up your RAM. If you spend, Bitcoin Wallet can garbage collect spent transactions after a while.

Note that you can spend to yourself. Just make sure to choose an amount that aggregates a number of transactions, without letting that number get too large. If it gets too large, you'll bump into another limit: the transaction size limit.

General rules:

  * Try have about one spend every 30-50 transactions.
  * Refrain from receiving [dust transactions](DustTransactions.md).
  * Refrain from receiving transactions that pay lots of recipients at once.
  * The above is especially true on cheap or aging phones.