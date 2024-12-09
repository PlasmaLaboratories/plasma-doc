---
description: >-
  This guide walks through the process of setting up and funding a Plasma wallet
  using the command line interface.
---

# Interacting with a Node

## Quick Start: Create and Fund a Wallet

First, let's define a helper function for better visual separation of steps:

{% code overflow="wrap" %}
```bash
function print_step() {
  local text=$1
  local seperator_length=${2:-80}
  local terminal_width=$(tput cols)
  local total_width=$((seperator_length > terminal_width ? terminal_width : seperator_length))
  local text_length=${#text}
  local padding=$(( (total_width - text_length) / 2 ))

  printf "\n"
  printf "%s\n" "$(printf '=%.0s' $(seq 1 $total_width))"
  printf "%*s%s\n" $padding "" "$text"
  printf "%s\n" "$(printf '=%.0s' $(seq 1 $total_width))"
}
```
{% endcode %}



## Plasma CLI Vars

Set up the required environment variables:

```bash
export PLASMA_CLI_VERSION=0.1.3
```

## Plasma Wallet Vars

{% code overflow="wrap" %}
```bash
export PLASMA_WALLET_DB=plasma-wallet.db export PLASMA_WALLET_JSON=plasma-wallet.json export PLASMA_WALLET_MNEMONIC=plasma-mnemonic.txt 
export PLASMA_WALLET_PASSWORD=password
export PLASMA_WALLET_TX=lvlsTransferTx.pbuf 
export PLASMA_WALLET_PROVED_TX=lvlsTransferTxProved.pbuf
```
{% endcode %}

## General vars

{% code overflow="wrap" %}
```bash
export PLASMA_NODE_HOST=devnet.plasmalabs.tech export PLASMA_NODE_PORT=443
export PLASMA_SECURE_CONNECTION=true export _JAVA_OPTIONS='-DisProd=true'
```
{% endcode %}

## &#x20;Clean up previous runs

Remove any existing wallet files before starting:

{% code overflow="wrap" %}
```bash
print_step "Cleaning up previous runs"
rm $PLASMA_WALLET_DB $PLASMA_WALLET_JSON $PLASMA_WALLET_MNEMONIC $PLASMA_WALLET_TX $PLASMA_WALLET_PROVED_TX
```
{% endcode %}

## 1. Set up the plasma-cli

{% code overflow="wrap" %}
```bash
alias plasma-cli="cs launch -r https://s01.oss.sonatype.org/content/repositories/releases org.plasmalabs:plasma-cli_2.13:$PLASMA_CLI_VERSION -- " shopt -s expand_aliases
```
{% endcode %}

## 2. Create a wallet

{% code overflow="wrap" %}
```bash
print_step "Creating the wallet"
plasma-cli wallet init \
    --network private \
    --password $PLASMA_WALLET_PASSWORD \
    --newwalletdb $PLASMA_WALLET_DB \
    --mnemonicfile $PLASMA_WALLET_MNEMONIC \
    --output $PLASMA_WALLET_JSON
```
{% endcode %}

## 3. Get the wallet address

{% code overflow="wrap" %}
```bash
export ADDRESS=$(plasma-cli wallet current-address --walletdb $PLASMA_WALLET_DB) print_step "Wallet address: $ADDRESS"
```
{% endcode %}

## 4. Create a transaction to transfer tokens to wallet

{% code overflow="wrap" %}
```bash
print_step "Creating a transaction to transfer tokens to wallet"
plasma-cli simple-transaction create \
    --from-fellowship nofellowship \
    --from-template genesis \
    --from-interaction 1 \
    --change-fellowship nofellowship \
    --change-template genesis \
    --change-interaction 1 \
    -t $ADDRESS \
    -w $PLASMA_WALLET_PASSWORD \
    -o $PLASMA_WALLET_TX \
    -n private \
    -a 1000 \
    -h $PLASMA_NODE_HOST \
    --port $PLASMA_NODE_PORT \
    --keyfile $PLASMA_WALLET_JSON \
    --walletdb $PLASMA_WALLET_DB \
    --fee 10 \
    --transfer-token lvl \
    --secure $PLASMA_SECURE_CONNECTION
```
{% endcode %}



## 5. Prove the transaction is semantically and syntactically correct

{% code overflow="wrap" %}
```bash
print_step "Proving the transaction is semantically and syntactically correct"
plasma-cli tx prove \
    -i $PLASMA_WALLET_TX \
    --walletdb $PLASMA_WALLET_DB \
    --keyfile $PLASMA_WALLET_JSON \
    -w $PLASMA_WALLET_PASSWORD \
    -o $PLASMA_WALLET_PROVED_TX
```
{% endcode %}

## 6. Broadcast the transaction

{% code overflow="wrap" %}
```bash
print_step "Broadcasting the transaction"
plasma-cli tx broadcast \
    -i $PLASMA_WALLET_PROVED_TX \
    -h $PLASMA_NODE_HOST \
    --port $PLASMA_NODE_PORT \
    --secure $PLASMA_SECURE_CONNECTION
```
{% endcode %}

## 7. Wait for the transaction to be included in a block

{% code overflow="wrap" %}
```bash
print_step "Waiting for the transaction to be included in a block"
until plasma-cli indexer-query utxo-by-address \
    --host $PLASMA_NODE_HOST \
    --port $PLASMA_NODE_PORT \
    --secure $PLASMA_SECURE_CONNECTION \
    --walletdb $PLASMA_WALLET_DB; do
    sleep 5
done
print_step "Transaction included in a block"
```
{% endcode %}

## 8. Check the balance of the wallet

{% code overflow="wrap" %}
```bash
print_step "Checking the balance of the wallet"
plasma-cli wallet balance \
    --from-fellowship self \
    --from-template default \
    --walletdb $PLASMA_WALLET_DB \
    --host $PLASMA_NODE_HOST \
    --port $PLASMA_NODE_PORT \
    --secure $PLASMA_SECURE_CONNECTION
```
{% endcode %}

