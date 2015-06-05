# Problem #

Transactions with no or low fees will not get relayed by most peers. As a consequence, they will never be confirmed without further action.

On the other hand, coins spent in stuck transaction cannot be spent elsewhere. Those coins are stuck.


# Solution #

You've got two options to resolve your problem:
  * Reset your blockchain and wait until it's up to date again (keep your device on power and connected to a reliable WLAN). After the rescan, stuck transactions should be gone and your BTC free to spend again.
  * Relay stuck transactions to a miner that accepts non-standard fees. You can use the "trusted peer" option for this, just remember to clear that option after your problem is resolved. Also see https://en.bitcoin.it/wiki/Free_transaction_relay_policy.