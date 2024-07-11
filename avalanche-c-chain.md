# Hacking blockchain from the command line: Avalanche C-Chain
```
cast send --rpc-url=https://api.avax-test.network/ext/bc/C/rpc
```

## Pangolin contract calls
https://snowtrace.io/address/0x88afdae1a9f58da3e68584421937e5f564a0135b#code
```
$ cast call --rpc-url=https://api.avax.network/ext/bc/C/rpc 0x88afdaE1a9F58Da3E68584421937E5F564A0135b "rewardPerToken()"
0x00000000000000000000000000000000000000000000000003ebb1b9e92f1629

$ cast call --rpc-url=https://api.avax.network/ext/bc/C/rpc 0x88afdaE1a9F58Da3E68584421937E5F564A0135b "totalSupply()"
0x00000000000000000000000000000000000000000036c3e52851d33982a66c47

$ seth --to-dec $(cast call - rpc-url=https://api.avax.network/ext/bc/C/rpc 0x88afdaE1a9F58Da3E68584421937E5F564A0135b "earned(address)" "0xe02752824b6b11e027080e75f692bd22b3dc7091")
```

## POC StakingRewards.sol - withdraw() method
```
$ cast call --rpc-url=https://api.avax.network/ext/bc/C/rpc 0x88afdaE1a9F58Da3E68584421937E5F564A0135b "balanceOf(address)" "0x8C26fb2DaF4790311DF4e9AAA87b356a8a9bd214"
```

### Calling a setter will consume gas, so we have to specify our private key:
```
$ cast send --rpc-url=https://api.avax.network/ext/bc/C/rpc 0x88afdaE1a9F58Da3E68584421937E5F564A0135b "withdraw(uint256)" "10" --private-key $PRIVKEY

$ cast call --rpc-url=https://api.avax.network/ext/bc/C/rpc 0x88afdaE1a9F58Da3E68584421937E5F564A0135b "balanceOf(address)" "0x8C26fb2DaF4790311DF4e9AAA87b356a8a9bd214"
```
