---
id: quickstart
title: Quickstart
tags: [quickstart, dapps, developer]
resources:
  - url: https://github.com/prototyp3-dev/frontend-web-cartesi
    title: React.js + Typescript starter template
  - url: https://github.com/masiedu4/nextjs-web-cartesi
    title: Next.js starter template
  - url: https://github.com/jplgarcia/cartesi-angular-frontend
    title: Angular starter template
  - url: https://github.com/Mugen-Builders/deploy-cartesi-dapp
    title: Deploy a Cartesi dApp on a test network
---

Welcome to Quickstart. Here, you will see a step-by-step guide on building a decentralized application easily.

## Set up your environment

The major requirements for building on Cartesi are Docker Desktop and Sunodo.

:::note
If you are using Windows, you must have [WSL2 installed and configured](https://learn.microsoft.com/en-us/windows/wsl/install) for building.
:::

### Install Docker Desktop and Sunodo

1. [Install Docker Desktop for your operating system](https://www.docker.com/products/docker-desktop/).

2. Sunodo is an easy-to-use CLI tool to build and deploy your dApps. To install Sunodo, run:

   ```shell
    npm i -g @sunodo/cli
   ```

## Create an application

To create the backend application from scratch, run:

```bash
sunodo create <dapp-name> --template <language>
```

This creates a new directory with template code in the language you specify.

```bash
$ sunodo create js-app --template javascript
✔ Application created at /js-app
```

Your application entry point will be the `src/index.js` file.

## Build the application

To build your application, ensure you have Docker Desktop running.

After that, you can run the command provided below:

```bash
sunodo build
```

The `sunodo build` command builds a Cartesi machine and compiles your application to be ready to receive requests and inputs.


## Run the application

Running your application starts a local Anvil chain/node that runs on port 8545.

To run your application:

```
sunodo run
```

## Send inputs to the application

With your application running, you can send inputs by sending transactions with the input payload.

To send inputs to your application, you have a few options available. The `sunodo send` command is one option that you can use.

Another option is [Cast](https://book.getfoundry.sh/cast/), a command-line tool enabling you to make Ethereum RPC calls.

Alternativelly, you can build a custom web interface to input data into your application.

### Using Sunodo

```shell
sunodo send
```

This guides you through sending inputs with Sunodo interactively.

```
? Select the send sub-command (Use arrow keys)
❯ Send DApp address input to the application.
  Send ERC-20 deposit to the application.
  Send ERC-721 deposit to the application.
  Send ether deposit to the application.
  Send generic input to the application.
```

### Using Cast

```shell
cast send <InputBoxAddress> "addInput(address,bytes)" <DAppAddress> <EncodedPayload> -mnemonic <MNEMONIC>
```

This command sends an input payload to your application through the `InputBox` contract.

1. Replace placeholders like `0xInputBoxAddress123`, `0xDAppAddress456`, `0xEncodedPayload789`, and `<MNEMONIC>` with the actual addresses, payload, and mnemonic for your specific use case.

:::note
If you are on the local anvil node, `0xDAppAddress456` is `0x70ac08179605AF2D9e75782b8DEcD3c22aA4D0C` and `0xInputBoxAddress123` is `0x59b22D57D4f067708AB0c00552767405926dc768`.
:::

2. Send `“Hello World”` which is hex-encoded into `0x48656c6c6f20776f726c64` to your application using Cast:

```shell
cast send 0x59b22D57D4f067708AB0c00552767405926dc768 "addInput(address,bytes)" 0x70ac08179605AF2D9e75782b8DEcDD3c22aA4D0C 0x48656c6c6f20776f726c64 --mnemonic 'test test test test test test test test test test test junk'
```

### Using a custom web interface

You can create a custom frontend that interacts with your application.

Here is a [React.js + Typescript starter](https://github.com/prototyp3-dev/frontend-web-cartesi) template with all the major functionalities to build on Cartesi.

## Deploy the application

:::danger
Deployment with Sunodo is under active development
:::


You can use [the guide here to deploy on a test network](https://github.com/Mugen-Builders/deploy-cartesi-dapp) in the interim.