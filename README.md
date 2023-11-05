# zkevm-contracts

Smart contract implementation which will be used by the polygon-hermez zkevm

[![Main CI](https://github.com/0xPolygonHermez/zkevm-contracts/actions/workflows/main.yml/badge.svg)](https://github.com/0xPolygonHermez/zkevm-contracts/actions/workflows/main.yml)

## Note

Private keys and mnemonics contained in this repository are used for internal test exclusively. Do not use them in production environments

## Requirements

- node version: 16.x
- npm version: 7.x

## Repository structure

- `contracts`: zkevm contracts
  - `PolygonZkEVMBridge.sol`: transfer assets between chains
    - `PolygonZkEVMGlobalExitRoot.sol`: manage global exit root in L1
    - `PolygonZkEVMGlobalExitRootL2.sol`: manage global exit root in L2
  - `PolygonZkEVM.sol`: consensus algorithm used by polygon hermez zkevm
- `docs`: specs and useful links
- `test`: contracts tests

## Activate github hook

```
git config --local core.hooksPath .githooks/
```

## Install

```
npm i
```

## Run tests

```
npm run test
```

## Run Linter

See errors:

```
npm run lint
```

Autofix errors:

```
npm run lint:fix
```

## Deploy on hardhat

```
npm run deploy:ZkEVM:hardhat
```

## Build dockers

```
npm run docker:contracts
```

A new docker `hermez-geth1.3:latest` will be created
This docker will contain a geth node with the deployed contracts
The deployment output can be found in: `docker/deploymentOutput/deploy_output.json`
To run the docker you can use: `docker run -p 8545:8545 hermez-geth1.3:latest`

## Note

In order to test, the following private keys are being used. These keys are not meant to be used in any production environment:

- private key: `0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80`
  - address:`0xf39fd6e51aad88f6f4ce6ab8827279cfffb92266`
- private key: `0xdfd01798f92667dbf91df722434e8fbe96af0211d4d1b82bbbbc8f1def7a814f`
  - address:`0xc949254d682d8c9ad5682521675b8f43b102aec4`

## Verify Deployed Smart Contracts

To verify that the smartcontracts of this repository are the same deployed on mainnet, you could follow the instructions described [document](verifyMainnetDeployment/verifyDeployment.md)

The smartcontract used to verify a proof, it's a generated contract from zkEVM Rom and Pil (constraints). To verify the deployment of this smartcontract you could follow the instructions described in this [document](verifyMainnetDeployment/verifyMainnetProofVerifier.md)

## License
All contracts except for `DARouterVerification.sol`, `MockDABridgeRouter.sol`, `MockDABridgeRouter.sol` and `Merkle.sol` are released under AGPL v3 (see [LICENSE](LICENSE.md)). The excepted contracts are released under Apache v2.
