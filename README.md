# tlvshop.com

This repository contains:

* `/`: Client side html/javascript to generate a `lncli` order command. This page can be displayed offline if desired. It was hosted at tlvshop.com but now there is a domain placeholder.

* `/acceptor`: A tool that interfaces with your `lnd` node and makes sure that only payments above a set value are accepted.

## Set up

* In order to use the acceptor, you need to run `lnd v0.11.0-beta` built with `tags="invoicesrpc"`. This will include [Interactive keysend acceptance](https://github.com/lightningnetwork/lnd/pull/4167).

* Start `lnd` with `--accept-keysend --keysend-hold-time=10s`. The keysend hold time specifies how long `lnd` should hold on to the payment before automatically cancelling. During this time frame, the acceptor has the time to decide what to do with the payment (cancel immediately or settle).

* Build and run `acceptor`. A command line flag `--minamt` can be used to specifiy the minimum amount to accept. The `acceptor` can easily be extended to not only verify the amount, but also check for example the inventory before accepting.
