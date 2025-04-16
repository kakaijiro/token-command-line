# SPL-Token Deployment on Devnet

To install solana-cli:

```
sh -c "$(curl -sSfL https://release.anza.xyz/v2.23/install)"
```

## 1. create a mint authority account

To create a keyPair for a mint authority account starting with "bos":

```
solana-keygen grind --starts-with bos:1
solana config set --keypair <mint auth account>.json
solana config set --url devnet
```

> [NOTE]
> the newly-created account nees some SOL balance.

## 2. create a token account

To create a token account starting with "mnt":

```
solana-keygen grind --starts-with mnt:1
```

## 3. create a SPL-Token

To create a SPL-Token:

```
spl-token create-token --program-id TokenzQdBNbLqP5VEhdkAS6EPFLC1PHnBqCXEpPxuEb  --enable-metadata <token account>.json
```

> [NOTE]
> TokenzQdBNbLqP5VEhdkAS6EPFLC1PHnBqCXEpPxuEb is the Token Extensions program's programID.

## 4. create a Token-associated account

To create a Token-associated account:

```
spl-token create-account <token account>
```

## 5. initialize metadata

To initialize metadata:

```
spl-token initialize-metadata <token account> <TOKEN_NAME> <TOKEN_SYMBOL> <TOKEN_URI>
```

TOKEN_URL refers to metadata.json file that contains metadata.

```
{
  "name": "Example Token",
  "Symbol": "EXAMP",
  "description": "Example token for solana bootcamp token-command-line project.",
  "image": "https://raw.githubusercontent.com/kakaijiro/token-command-line/main/pokky.webp"
}
```

![Screenshot of solana explorer showing the custom Token](https://raw.githubusercontent.com/kakaijiro/token-command-line/main/explorer.png)

## 6. generate Token

To generate some Token:

```
spl-token mint <token account> <amount>
```

## 7. transfer Token

To transfer some Token:

```
spl-token transfer <token account> <amount> <ecipient account> --url devnet --fund-recipient
```
