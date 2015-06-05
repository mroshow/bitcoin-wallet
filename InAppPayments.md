## Introduction ##

You might want to send Bitcoins from your app. A common example is a donation button.

Check out the code from the repository. There are two subprojects for in-app payments:

  * **integration-android**:
> > A tiny library for integrating Bitcoin payments into your own Android app
> > (e.g. donations, in-app purchases).
  * **sample-integration-android**:
> > A minimal example app to demonstrate integration of Bitcoin payments into
> > your Android app.

Have a look at the Javadoc for the class `BitcoinIntegration`.

## Sending the request ##

```
    class de.schildbach.wallet.integration.android.BitcoinIntegration

    /*
     * Request specific amount of Bitcoins from user,
     * without feedback from the app.
     */
    static void request(Context context, String address, long amount);

    /*
     * Request specific amount of Bitcoins from user,
     * with feedback from the app.
     */    
    static void requestForResult(Activity activity, int requestCode,
                                 String address, long amount);
```

Methods for requests without amount are also available!

The above methods send an intent to any Bitcoin app which listens to it.

```
    action = android.intent.action.VIEW
    data = bitcoin:1PZmMahjbfsTy6DsaRyfStzoWTPppWwDnZ?amount=0.1
```

The URL is formatted to [BIP21 standard](https://en.bitcoin.it/wiki/BIP_0021).

## Retrieving the result ##

Some apps return a result through onActivityResult() after the user has gone through the sending process. In this case you can read some useful extras:

```
    resultCode = OK|CANCELED
    extras[transaction_hash] = c8a9e036ecbbe75c...
```

You can use this convenience method to fetch the hash:

```
    class de.schildbach.wallet.integration.android.BitcoinIntegration

    /**
     * Get transaction hash from result intent.
     */
    static String transactionHashFromResult(final Intent result);
```

This is an example of code for using the result:

```
    protected void onActivityResult(int requestCode, int resultCode, Intent result)
    {
        if (requestCode == REQUEST_CODE && resultCode == Activity.RESULT_OK)
        {
            String txHash = BitcoinIntegration.transactionHashFromResult(result);
            if (txHash != null)
            {
                // thank you!
                // (but: no guarantees)
            }
        }
        else if (resultCode == Activity.RESULT_CANCELED)
        {
            // cancelled
        }
        else
        {
            // something went wrong
        }
   }
```