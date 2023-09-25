# Example Subgraph

An example to help you get started with The Graph. For more information see the docs on https://thegraph.com/docs/.
This repository will help in understanding implementation of a subgraph on Neon Devnet.

## Graph node credentials for Neon Devnet

- Graph endpoint: https://ch2-graph.neontest.xyz/
- Graph endpoint for deploying subgraph: https://ch2-graph.neontest.xyz/deploy/
- Endpoint for graphql: https://ch2-graph.neontest.xyz/index-node/graphql
- IPFS Address: https://ch-ipfs.neontest.xyz/

## Steps to follow:

1. Clone this repository https://github.com/sukanyaparashar/graph-neon-test

2. Create a .env file and add the private keys like this -

```
PRIVATE_KEY_1=0x...
PRIVATE_KEY_2=0x...
PRIVATE_KEY_3=0x...
```

3. Run the following commands to install the required packages, compile the Gravatar smart contract and deploy the contract on Neon Devnet.

```
$ npm install
$ truffle compile
$ truffle migrate --network neonlabs
```

4. After getting the contract address and block number from the migration step above, replace the “address” and “startBlock” properties in the “subgraph.yaml” file with the corresponding values.

5. For deploying a subgraph on Neon Devnet, run the following commands -

```
$ graph create neonlabs/test-subgraph-neon --node https://ch2-graph.neontest.xyz/deploy/
$ graph codegen
$ graph build
$ graph deploy neonlabs/test-subgraph-neon --ipfs https://ch-ipfs.neontest.xyz --node https://ch2-graph.neontest.xyz/deploy/ --version-label="v0.0.1"
```

6. Open the HTTP link from the above result - https://ch2-graph.neontest.xyz/subgraphs/name/neonlabs/test-subgraph-neon

7. To query the subgraph, enter a query like this on the left side -

```
query {
 gravatars {
     displayName
     id
     imageUrl
     owner
  }
}
```
