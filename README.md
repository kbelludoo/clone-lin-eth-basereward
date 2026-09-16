# clone-lin-eth-basereward

Experimental LIN clone of Ethereum consensus-spec **integer square root** and Altair **base reward** (uint64 Gwei). This repository is the LIN copy.

Results and the machine-written proof harness live in [kbelludoo/lin-open](https://github.com/kbelludoo/lin-open) (`examples/eth_base_reward/`, `test/prove_eth_base_reward_external.py`).

## Upstream

- Repo: [ethereum/consensus-specs](https://github.com/ethereum/consensus-specs)
- Tag: `v1.5.0` commit `b5c3b619887c7850a8c1d3540b471092be73ad84`
- License: **CC0-1.0**
- `specs/phase0/beacon-chain.md` integer_squareroot  
  sha256 `95519084a4689b0bbbbaa9db9fb1d6e48d6c7be83a8dd21bc82a83cf96a6254a`  
  blob `5658ed2c236568f7be1cf26e8d2c496ed5179564`
- `specs/altair/beacon-chain.md` get_base_reward_per_increment / get_base_reward  
  sha256 `2ea769c3a23139225997efc75efed8914f8fd949ec02991fa62d026017a278d9`  
  blob `4edfbeb763146fe33750de82e118b6bf1bde890e`

## Canonical vector

1 validator, 32 ETH effective, 32 ETH total (Altair) → **11448672 Gwei**.

Class: **EXPERIMENTAL**. Not a beacon node. Not Electra 2048 ETH max EB.

## Reproduce (C11 oracle, no Zig)

```
gcc -O2 -std=c11 -o eth_base_reward_c11 test/oracles/eth_base_reward_c11.c
./eth_base_reward_c11 selftest
./eth_base_reward_c11 altair 32000000000 32000000000
```
