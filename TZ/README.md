# Create Token Process

The goal is to create a token on solana and mint it and transfer tokens to a second account

## Accounts

```
solana-keygen grind --starts-with w:1 --ignore-case
```

- wD1W4ofjrCWo4XP45chQodLtWqfE1AieU1t1QVaehBt: principal account
- wBi5t6a8uhTtScgmi6YGwafdBkb2GGUGD1Hx4xsYJaW: secondary account

## Create Token
A new token is created

```console
spl-token create-token --program-id TokenzQdBNbLqP5VEhdkAS6EPFLC1PHnBqCXEpPxuEb --enable-metadata
```
Output:
```
Address:  88BfMpEab7UzeLYEQSonk78S5QFaysMGLqJb5vytE8pe
Decimals:  9

Signature: 5DKD3ipjcmZt2przwFdLr8VMiKMe5h1Ku1fGc33rgK81eKw7CVD7W2wj6RsEU6HZVdt5imE9MHMFRxc7U9X12ndY
```
[Transaction](https://explorer.solana.com/tx/5DKD3ipjcmZt2przwFdLr8VMiKMe5h1Ku1fGc33rgK81eKw7CVD7W2wj6RsEU6HZVdt5imE9MHMFRxc7U9X12ndY?cluster=devnet)

[Token](https://explorer.solana.com/address/88BfMpEab7UzeLYEQSonk78S5QFaysMGLqJb5vytE8pe?cluster=devnet)

## Initialize metadata
Token metadata is initialized

```console
spl-token initialize-metadata 88BfMpEab7UzeLYEQSonk78S5QFaysMGLqJb5vytE8pe "TestZero" "TZ" "https://raw.githubusercontent.com/juanolv/token-test/7f6d7343c1a896b929e854aee6f8fa817ad1013c/TZ/metadata.json"
```
```json
{
  "name": "Test Zero",
  "symbol": "TZ",
  "description": "Test Zero Token",
  "image": "https://raw.githubusercontent.com/juanolv/token-test/505a5d07090002f192d3450c4d32b108771db63c/TZ/Zero.jpg",
  "attributes": [
    {
      "trait_type": "Item",
      "value": "Test Zero"
    }
  ]
}
```


Output: 
```
Signature: 54Arcm845hQEuVVQneFUhZGAdBgjqUfYvwzpTFFo4oWtyq5YTsRpcGL6LYU55WYqqkagxyCqmVazV7eJGKw7e7w9
```
[Transaction](https://explorer.solana.com/tx/54Arcm845hQEuVVQneFUhZGAdBgjqUfYvwzpTFFo4oWtyq5YTsRpcGL6LYU55WYqqkagxyCqmVazV7eJGKw7e7w9?cluster=devnet)

## Create a new account
A new account is created for the token

```console
spl-token create-account 88BfMpEab7UzeLYEQSonk78S5QFaysMGLqJb5vytE8pe --program-id TokenzQdBNbLqP5VEhdkAS6EPFLC1PHnBqCXEpPxuEb
```

Output:
```
Creating account FUAe6MEp4tKAXoZZs637utkT3t7eVLc5JVhJ717VeCKW

Signature: 65Yd8zti8kJ7gifWQgPo2GZS62qa74yTgLKDQtS2y2SAhp6TkJwuxmhahjWzbqzYepPDBtwGrqSWNmo8CXWQEWZN
```
[Transaction](https://explorer.solana.com/tx/65Yd8zti8kJ7gifWQgPo2GZS62qa74yTgLKDQtS2y2SAhp6TkJwuxmhahjWzbqzYepPDBtwGrqSWNmo8CXWQEWZN?cluster=devnet)

## Mint the token
The new token is minted

```console
spl-token mint 88BfMpEab7UzeLYEQSonk78S5QFaysMGLqJb5vytE8pe 10000000000
```

Output:
```
Minting 10000000000 tokens
  Token: 88BfMpEab7UzeLYEQSonk78S5QFaysMGLqJb5vytE8pe
  Recipient: FUAe6MEp4tKAXoZZs637utkT3t7eVLc5JVhJ717VeCKW

Signature: 2AoJqKD8EFo1h3TYHb3FDwJQXCqSREH25MaJX3JN3vHzUL2nAQnP5DM5iPSdHwQ22uuuayVRJFQ7eoNHk8HXmQHf
```
[Transaction](https://explorer.solana.com/tx/2AoJqKD8EFo1h3TYHb3FDwJQXCqSREH25MaJX3JN3vHzUL2nAQnP5DM5iPSdHwQ22uuuayVRJFQ7eoNHk8HXmQHf?cluster=devnet)

# Wormhole - NTT

## Generate NTT Program Keypair
```console
solana-keygen grind --starts-with ntt:1 --ignore-case
```

Output
```
Searching with 8 threads for:
        1 pubkey that starts with 'ntt' and ends with ''
Wrote keypair to NTtTAGDe3hSDaWxckAPbVkt9WwxgXrxSmGDPCCFnQm5.json
```

## Derive the 'token-authority' PDA of the newly generated NTT Program id
```console
ntt solana token-authority NTtTAGDe3hSDaWxckAPbVkt9WwxgXrxSmGDPCCFnQm5
```

Output:
```
4yGArNB7T9oR3zjyRVgVufD7bDPWzYMFP5Wf4zXYxVHE
```

## Set SPL token Mint Authority to newly generated 'token authority' PDA
```console
 spl-token authorize 88BfMpEab7UzeLYEQSonk78S5QFaysMGLqJb5vytE8pe mint 4yGArNB7T9oR3zjyRVgVufD7bDPWzYMFP5Wf4zXYxVHE
```

Output:
```
Updating 88BfMpEab7UzeLYEQSonk78S5QFaysMGLqJb5vytE8pe
  Current mint: wD1W4ofjrCWo4XP45chQodLtWqfE1AieU1t1QVaehBt
  New mint: 4yGArNB7T9oR3zjyRVgVufD7bDPWzYMFP5Wf4zXYxVHE

Signature: 2NsXSzKVrDwvihc3P4hUz3CkstFxQMjMA4X7Ji451igxqPtGeNgZhZk5Kn3Y2tisn57uNXoqLDocNkPQUaSPEobU
```

## Deploy NTT
```console
ntt add-chain Solana --latest --mode burning --token 88BfMpEab7UzeLYEQSonk78S5QFaysMGLqJb5vytE8pe --payer ./wD1W4ofjrCWo4XP45chQodLtWqfE1AieU1t1QVaehBt.json --program-key ./NTtTAGDe3hSDaWxckAPbVkt9WwxgXrxSmGDPCCFnQm5.json
```

Output:
```
Preparing worktree (detached HEAD 1193a4a)
HEAD is now at 1193a4a evm/src/interfaces: update topic hashes (#396)
Created worktree at .deployments/Solana-1.0.0 from tag v1.0.0+solana
Anchor CLI version must be 0.29.0 but is 0.30.1
```



