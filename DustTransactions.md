Problem scenarios:
  * Some people use Bitcoin for receiving compensations for incredibly small workloads (e.g. clicking on an ad).
  * Some services misuse transactions as a messaging system (e.g. lost bets).

You should know that each payment under 0.01 BTC requires a fee of at least 0.0005 BTC. That means if you are receiving a payment of 0.0005 BTC or below, you will not be able to economically spend it!

Now, what about aggregating several 0.0005 BTC payments in one transaction? For example, you could spend 0.0005 BTC `*` 4 = 0.002 BTC. Problem here: The fee is 0.0005 _per kilobyte_, and aggregating builds larger (in bytes) transactions. You can roughly aggregate 5 transactions with a 0.0005 BTC fee.

So, as a general rule of thumb:

**You should refrain from receiving payments smaller than 0.0001 BTC.** We call them _dust_.

Note that these numbers will change over time, as Bitcoin value rises and falls and fee rules get adapted. Until then however, dust just uses up precious memory, making everything slower than it should be. Or, in extreme cases, causes [running out of memory](OutOfMemory.md).