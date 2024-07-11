# Hacking blockchain from the command line: Ethereum Mainnet

Using WETH9 (Wrapped Ether) contract for educational purposes:
```
$ export ADDRESS="0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2"
```

## Convert Ether to wei in hex:
```
$ cast --to-hex $(cast --to-wei 0.25)
```
## eth_call (Does not consume gas):
```
$ cast call $ADDRESS "number()"
$ seth call $COL1 'balanceOf(address)' $ETH_FROM
```
## Calling a setter:
```
$ cast send $ADDRESS "setNumber(uint256)" "34" --private-key $PRIVKEY
```

## Different ways to send Ether eth_send:
```
$ seth --to-dec $(seth call $COL1 'balanceOf(address)' $ETH_FROM)
$ seth send --value 0.1 $ADDRESS
```

## Run anvil for Metamask localhost debugging:
```
$ anvil --chain-id 1337
```

## Get chain-id:
```
$ cast chain-id
```

## Get balance of an address (in Ether):
```
$ cast --from-wei $(cast balance $ADDRESS)
```

## Fork Ethereum mainnet locally:
```
$ anvil --fork-url https://mainnet.infura.io/v3/$INFURA_KEY
```
