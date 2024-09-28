All code examples were originally build by CoinChimp in this repo: https://github.com/coinchimp/kaspa-krc20-apps **Thank you CoinChimp!**

# Kaspa KRC20 Token Integration Examples

This repository provides a set of tools and examples for integrating the KRC20 token protocol from the Kaspa network. The examples include generating keys, minting, deploying, and transferring KRC20 tokens. The tools are built using TypeScript and leverage the Kaspa WASM library.

## Prerequisites

- [Bun](https://bun.sh) v1.0.31 or later
- [Kaspa WASM](https://github.com/kaspanet/rusty-kaspa/releases/tag/v0.15.2)

## Installation

1. **Clone the repository:**

    ```bash
    git clone https://github.com/argonmining/krc20-examples.git
    cd krc20-examples
    ```

2. **Install required packages:**

    ```bash
    bun install
    ```

3. **Download and setup Kaspa WASM:**

    Download the latest Kaspa WASM from [here](https://github.com/kaspanet/rusty-kaspa/releases/tag/v0.15.2). Move the `nodejs` folder from the WASM archive to the root of your project and rename it to `wasm`.

## KeyGenerator CLI

The `keygen/keyGeneratorCli.ts` script allows you to generate a 24-word mnemonic phrase, derive private keys, and obtain wallet addresses for the Kaspa network.

### Usage

- **Generate a new mnemonic, private key, and address:**

    ```bash
    bun run keygen/keyGeneratorCli.ts generate
    ```

- **Obtain an address from an existing private key:**

    ```bash
    bun run keygen/keyGeneratorCli.ts address <privateKey>
    ```

    Replace `<privateKey>` with your actual private key.

- **Enable debug mode:**

    ```bash
    bun run keygen/keyGeneratorCli.ts generate --debug
    ```

- **Display help:**

    ```bash
    bun run keygen/keyGeneratorCli.ts --help
    ```

### Example

Generate a new mnemonic, private key, and address with debugging enabled:

```bash
bun run keygen/keyGeneratorCli.ts generate --debug
```

## Balance Checker CLI

The `balance/index.ts` script allows you to check the balance of a given address on the Kaspa network.

### Usage

- **Check the balance of an address:**

    ```bash
    bun run balance/index.ts <address>
    ```

    Replace `<address>` with the actual address you want to check.

### Example

Check the balance of an address:

```bash
bun run balance/index.ts kaspaAddressHere
```

## Kaspa Transfer CLI

The `kaspa/sendKaspa.ts` script allows you to securely transfer KASPA tokens to any wallet using your private key.

### Usage

```bash
bun run kaspa/sendKaspa.ts --privKey <privateKey> --destination <address> --amount <amount> [options]
```

### Options

- `--privKey`: Your private key to sign the transaction. **(Required)**
- `--destination`: The destination address to which funds will be sent. **(Required)**
- `--amount`: The amount of KASPA to transfer. **(Required)**
- `--network`: The network to connect to (default: `testnet-10`).
- `--logLevel`: Log level (`DEBUG`, `INFO`, default: `INFO`).
- `--help`: Display the help message with usage details.

### Example

Transfer 100 KASPA tokens from your wallet to the specified destination address on the `testnet-10` network, with detailed logging output at the `DEBUG` level:

```bash
bun run kaspa/sendKaspa.ts --privKey yourPrivateKeyHere --destination kaspaAddressHere --amount 100 --network testnet-10 --logLevel DEBUG
```

## KRC20 Minting CLI

The `krc20/mint.ts` script allows you to mint KRC20 tokens within the Kaspa blockchain network.

### Usage

```bash
bun run krc20/mint.ts --privKey <priv-key> [options]
```

### Options

- `--privKey <priv-key>`: **Required**. Your private key used to sign transactions.
- `--network <network>`: The network to use (default: `testnet-10`).
- `--ticker <ticker>`: The ticker symbol for the token (default: `TCHIMP`).
- `--priorityFee <fee>`: Priority fee in KAS for the transaction (default: `0`).
- `--timeout <ms>`: Timeout for operations in milliseconds (default: `300000`).
- `--logLevel <level>`: Logging level: `INFO` or `DEBUG` (default: `INFO`).
- `--loops <number>`: Number of loops to perform (default: `1`).
- `--help`: Show this help message and exit.

### Example

Mint KRC20 tokens with the specified options:

```bash
bun run krc20/mint.ts --privKey your_private_key_here --ticker MYTOKEN --priorityFee 0.1 --loops 5
```

## KRC20 Deployment CLI

The `krc20/deploy.ts` script allows you to deploy KRC20 tokens within the Kaspa blockchain network.

### Usage

```bash
bun run krc20/deploy.ts --privKey <priv-key> [options]
```

### Options

- `--privKey <priv-key>`: **Required**. Your private key used to sign transactions.
- `--network <network>`: The network to use (default: `testnet-10`).
- `--ticker <ticker>`: The ticker symbol for the token (default: `TCHIMP`).
- `--priorityFee <fee>`: Priority fee in KAS for the transaction (default: `1.5`).
- `--timeout <ms>`: Timeout for operations in milliseconds (default: `120000`).
- `--max <max-supply>`: Maximum supply for the deployed token (default: `28700000000000000000`).
- `--limit <limit-per-mint>`: Limit per mint for the deployed token (default: `2870000000000`).
- `--help`: Show this help message and exit.

### Example

Deploy a new KRC20 token with the specified options:

```bash
bun run krc20/deploy.ts --privKey your_private_key_here --ticker MYTOKEN --max 1000000 --limit 1000
```

## KRC20 Transfer CLI

The `krc20/transfer.ts` script allows you to transfer KRC20 tokens within the Kaspa blockchain network.

### Usage

```bash
bun run krc20/transfer.ts --privKey <priv-key> --dest <destination> --amount <amount> [options]
```

### Options

- `--privKey <priv-key>`: **Required**. Your private key used to sign transactions.
- `--dest <destination>`: **Required**. The destination wallet address for the transfer.
- `--amount <amount>`: **Required**. The amount of tokens to transfer.
- `--network <network>`: The network to use (default: `testnet-10`).
- `--ticker <ticker>`: The ticker symbol for the token (default: `TCHIMP`).
- `--priorityFee <fee>`: Priority fee in KAS for the transaction (default: `1.5`).
- `--timeout <ms>`: Timeout for operations in milliseconds (default: `120000`).
- `--logLevel <level>`: Logging level: `INFO` or `DEBUG` (default: `INFO`).
- `--help`: Show this help message and exit.

### Example

Transfer KRC20 tokens with the specified options:

```bash
bun run krc20/transfer.ts --privKey your_private_key_here --dest your_wallet_address_here --amount 100 --ticker MYTOKEN
```

## Disclaimer

**1. No Responsibility:**
I, the developer, am not responsible for any direct or indirect consequences, including but not limited to financial loss, damages, or legal repercussions that may arise from the use or misuse of this project. This software is provided "as is," without any guarantees or warranties of any kind.

**2. No Recommendation or Endorsement:**
This project is not an endorsement, recommendation, or promotion of any cryptocurrency, blockchain technology, or financial product. Any references to specific technologies or products are for informational purposes only and do not constitute an endorsement.

**3. Not Financial Advice:**
The content and tools provided in this project are not intended as financial advice. I am not a financial advisor, and you should consult with a qualified professional before making any financial decisions.

**4. Use at Your Own Risk:**
By using this project, you acknowledge that you do so at your own risk. The user is solely responsible for ensuring compliance with all applicable laws and regulations.

**5. No Warranty or Liability:**
This project is provided without warranty of any kind, express or implied. In no event shall I, the developer, be held liable for any damages arising from the use of this project.

**6. Third-Party Content:**
Any third-party content, including but not limited to libraries, APIs, or other code incorporated into this project, is the responsibility of their respective authors. I do not assume any responsibility for the content or functionality of third-party materials.

**7. Legal Compliance:**
Users are responsible for ensuring that their use of this project complies with all applicable local, national, and international laws and regulations.