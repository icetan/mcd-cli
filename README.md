## MCD Command-line interface

```
McDai - Multi-collateral Dai

Usage: mcd [<options>] <command> [<args>]
   or: mcd help [<command>]

Commands:

   bite            Trigger liquidation of an unsafe CDP
   bites           Recent bites
   dai             Vat dai balances
   debt            Total dai issuance
   drip            Trigger stability fee collection
   flap            Trigger a flap auction
   flips           View flips and kick-off auctions
   flog            Release queued bad-debt for auction
   flop            Trigger a flop auction
   frob            CDP management
   frobs           Recent frobs
   gem             Collateral balances
   help            Print help about mcd or one of its subcommands
   ilk             Ilk state
   poke            Update the price feed for a given Ilk
   urn             CDP state
   vice            Total bad debt
   vow             Liquidator balances
```

## Install

First install dapp tools:

```
$ curl https://dapp.tools/install | sh
```

Then install the `mcd` package:

```bash
$ dapp pkg install mcd
```

## Open a CDP and withdraw Dai

```bash
$ mcd --ilk=ETH join 100

$ mcd --ilk=ETH gem balance
vat   100 Free collateral
ink   0   Locked collateral
ext   900 ERC20 account balance

$ mcd --ilk=ETH frob 99 7
ilk   ETH                                                              CDP type identifier
urn   43335d187cfab85d415678095495d06e779bd0f5000000000000000000000000 CDP identifier
ink   99.0000000000000000000                                           Locked collateral (ETH)
art   7.00000000000000000000                                           Outstanding debt (DAI)
spot  99.3333333333333333333                                           Price with safety margin (USD)

$ mcd --ilk=ETH gem balance
vat   1   Free collateral
ink   99  Locked collateral
ext   900 ERC20 account balance

$ mcd dai balance
vat   7.00000000000000000000 Vat balance
ext   0.00000000000000000000 ERC20 account balance

$ mcd dai exit 50

$ mcd dai balance
vat   0.00000000000000000000 Vat balance
ext   7.00000000000000000000 ERC20 account balance
```
