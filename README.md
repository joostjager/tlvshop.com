# tlvshop.com

This repository contains:

* `/`: Client side html/javascript to generate a `lncli` order command. This page can be displayed offline if desired. It is currently hosted at https://tlvshop.com.

* `/acceptor`: A tool that interfaces with your `lnd` node and makes sure that only payments above a set value are accepted.

## Set up

* In order to use the acceptor, you need to build the `lnd` master branch with `tags="invoicesrpc"`. [Interactive keysend acceptance](https://github.com/lightningnetwork/lnd/pull/4167/commits) isn't included in a stable release yet, but will likely be part of the upcoming 0.11 version. Don't forget that running master on mainnet comes with additional risks and isn't recommended.

* Start `lnd` with `--accept-keysend --keysend-hold-time=10s`. The keysend hold time specifies how long `lnd` should hold on to the payment before automatically cancelling. During this time frame, the acceptor has the time to decide what to do with the payment (cancel immediately or settle).

* Build and run `acceptor`. A command line flag `--minamt` can be used to specifiy the minimum amount to accept. The `acceptor` can easily be extended to not only verify the amount, but also check for example the inventory before accepting.
