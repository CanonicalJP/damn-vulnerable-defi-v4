# Damn Vulnerable DeFi v4 Walkthorugh

## 1. [UNSTOPPABLE](https://www.damnvulnerabledefi.xyz/challenges/unstoppable/)

Condition: Prevent `UnstoppableVault.flashLoan()` from successfully executing.

### [PoC](https://github.com/CanonicalJP/damn-vulnerable-defi-v4/blob/master/test/unstoppable/Unstoppable.t.sol)

The balance of `UnstoppableVault` is not accounted for unexpected changes (e.g. an ERC20 transfer), by just transfering an small amount to the vault, the below condition fail and revert

https://github.com/CanonicalJP/damn-vulnerable-defi-v4/blob/84b762cb27b1c44cbd2f1ba6caeaaa2805d12a69/src/unstoppable/UnstoppableVault.sol#L84-L85

```solidity
function test_unstoppable() public checkSolvedByPlayer {
    token.transfer(address(vault), 1e18);
}
```

