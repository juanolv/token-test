# Create Token Process

The goal is to create a token on solana and mint it

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





