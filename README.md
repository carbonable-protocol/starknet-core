<div align="center">
  <h1 align="center">Carbonable Starknet Protocol</h1>
  <p align="center">
    <a href="https://discord.gg/zUy9UvB7cd">
        <img src="https://img.shields.io/badge/Discord-6666FF?style=for-the-badge&logo=discord&logoColor=white">
    </a>
    <a href="https://twitter.com/intent/follow?screen_name=Carbonable_io">
        <img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white">
    </a>       
  </p>
  <h3 align="center">Carbonable contracts written in Cairo for StarkNet.</h3>
</div>

## About

Carbonable protocol aims to fund carbon removal projects by using [crowdfunding platform](https://app.carbonable.io/). The protocol allows individuals and organizations to invest in carbon removal projects such as reforestation, mangrove restoration and agroforestry.

The Carbonable protocol digitals carbon removal projects as collection of NFTs, and allows to farm this NFTs to generate carbon credits, that represent a certain amount of carbon dioxide removed from the atmosphere due to this projects. These carbon credits can be sold on a carbon market to generate yield, or allowing individuals and organizations to offset their carbon emissions to becoming carbon neutral.

Carbonable is a decentralized protocol, this allows for transparency in the funding and tracking of carbon offsetting projects. The protocol also automate the process of funding, reporting, tracking and farming of the carbon offsetting projects.

## Documentation

You can find the docuemntation [her](https://carbonable.gitbook.io/starknet-smart-contracts/)

## Repo

The repository is in the process of migrating. You can [find it here](https://github.com/Carbonable/carbonable-starknet) for the moment


## Feature : Yiealder v2
issue : https://github.com/carbonable-protocol/carb-starknet-core/issues/1
Responsible : [Bal7hazar ](https://github.com/orgs/carbonable-labs/people/Bal7hazar)
Description of the issue : 

Carbon Credit Vesting is a library designed to facilitate dynamic reward distribution based on a distribution curve. For ex, this library is ideal for projects that aim to reward users for their contributions to carbon neutrality and positive impact on the fight against climate change.

The library allows for the tracking of total project value and how much value has been deposited on the yielder and offset at specific time intervals. This information is then used to calculate how much value has not been deposited between the two snapshots, thus providing a more accurate distribution of rewards.

The library also allows for the implementation of different distribution curves, making it adaptable to different projects and their specific requirements.

In terms of technical requirements, the library is built on Starknet and is used within the Carbonable protocol to manage carbon credit farming.


## Usage

> ## ⚠️ WARNING! ⚠️
>
> This is repo contains highly experimental code.
> Expect rapid iteration.
> **Use at your own risk.**

### Set up the project

#### 📦 Install the requirements

- [protostar](https://github.com/software-mansion/protostar)

### 🎉 Install

```bash
protostar install
```

### ⛏️ Compile

```bash
protostar build
```

### 🌡️ Test

```bash
# Run all tests
protostar test

# Run only unit tests
protostar test tests/units

# Run only integration tests
protostar test tests/integrations
```

### 🌐 Test account

If you want a fresh account for tests, you can deploy an account with the following command:

```bash
starknet deploy_account --network=<network>
```

It will generate the account information into the `~/.starknet_accounts/starknet_open_zeppelin_accounts.json` file.  
See also starknet [documentation](https://www.cairo-lang.org/docs/hello_starknet/account_setup.html#creating-an-account) for more details.

### 💋 Format code

```bash
cairo-format -i src/**/*.cairo tests/**/**/*.cairo
```

### 📝 Generate Documentation

#### Requirements

- python environment (python >=3.9)
- [`mdutils`](https://pypi.org/project/mdutils/) dependency installed
- [`kaaper-cli`](https://github.com/onlydustxyz/kaaper) installed
- [`thoth`](https://github.com/FuzzingLabs/thoth) installed

#### Generation

```bash
cd docs
kaaper generate ../src ./data
python build.py
callgraphs.sh
```

## 🚀 Deployment

```bash
# On testnet
./scripts/deploy.sh -p testnet -a carbonable
```

With:
- `testnet` profile defined in protostar config file (testnet for alpha-goerli)
- `carbonable` alias to the admin account (optional if it is your `__default__`  acount, see also starknet account [documentation](https://starknet.io/docs/hello_starknet/account_setup.html))

Contract addresses will be logged into the prompt.

### Inputs

To manage inputs sent to constructor during the deployment, you can customize the [config files](./scripts/configs/).

### Prepare the contracts before tests

After deployment, the **admin** account (according to parameters) is the owner of all contracts.
So far, you have to do the following actions manually:

- Change the NFT contract owner from **admin** to **Minter contract**
  * How: _Voyager > Write contract > `transferOwnership`_
  * Verifiy: _Voyager > Read contract > `owner`_
- Approve the **Minter contract** to spend the **admin payment tokens**
  * How: Voyager > _Write contract > `approve`_
  * Verifiy: Voyager > _Read contract > `allowance`_
- Buy NFT through the **Minter contract**
  * How: _Voyager > Write contract > `buy`_
  * Verifiy: _Voyager > Read contract > `balanceOf` (of the NFT contract)_

## 📄 License

**carbonable-starknet-protocol** is released under the [MIT](LICENSE).
