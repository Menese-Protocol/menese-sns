# Menese Protocol SNS

This repository holds the initialisation parameters for the Menese Protocol DAO,
published openly so anyone can read them before the NNS votes.

`sns_init.yaml` is the whole DAO in one file. It says which canisters the DAO takes
control of, how the governance token is distributed, and the terms of the
decentralization swap. It is submitted to the NNS as a single proposal. If that
proposal passes, these are the values the SNS is created with, and after that they
can only change by a vote.

## Menese is the Multichain Operating System

A composable cross chain execution engine; anyone can build financial tools on top of
it, powered by ICP's chain key cryptography, with no bridges, no guardians, and no
corporate custody.

ICP nodes collectively hold signing keys using threshold cryptography. No single node,
server, or company ever holds a full key, and the complete private key is never
reconstructed; not during generation, not during signing, not ever. The canister reads
the world through HTTP outcalls, decides with on chain logic, then signs and submits
real transactions on the destination chain. This is the difference between a
distributed key and a distributed brain.

It executes on 18 chains: Bitcoin, Ethereum, Arbitrum, Optimism, Base, Polygon, Monad,
Solana, Sui, Aptos, NEAR, TON, TRON, Cardano, XRP, Litecoin, CloakCoin, and ICP. On
top of that sit venue integrations including THORChain and Hyperliquid, and access to
around 26 tokenized equities and real world assets covering stocks, index products,
treasuries, silver, oil and rare earths.

## Why decentralize

Three things the community should own and steer with us.

1. Exchange listing, with the treasury funding the listing and the market making
2. Debit card issuance, so people can spend what they hold
3. Growing the protocol, more chains, more business integrations, more SDK partners

## What the DAO gets control of

| Canister | ID |
|---|---|
| backend | `cxa6p-xiaaa-aaaad-aczda-cai` |
| frontend | `cqby3-2qaaa-aaaad-aczdq-cai` |
| icp_sol_swap | `w2vjc-2yaaa-aaaab-ae6zq-cai` |
| sdk_gateway | `urs2a-ziaaa-aaaad-aembq-cai` |

The full source of all four is published at
[Menese-External-Reviewers](https://github.com/Menese-Protocol/Menese-External-Reviewers)
with a pinned Docker builder. Each one rebuilds byte for byte to the module hash
installed on mainnet, and the repository ships a script that checks all four against
the live network in one command.

## Token distribution

100,000,000 MENES. Fixed supply. No inflation.

| Bucket | MENES | Share |
|---|---|---|
| Team, as genesis neurons | 10,000,000 | 10% |
| Decentralization swap | 10,000,000 | 10% |
| DAO treasury | 80,000,000 | 80% |
| **Total** | **100,000,000** | **100%** |

Team and Mercatura Forum hold 28,000,000 MENES between them on the existing ledger,
staked in the sale canister. Those entitlements are unchanged.

The team's 18,000,000 arrives in two parts: 10,000,000 at genesis as neurons, each
person's pro rata share, and 8,000,000 redeemed 1 for 1 against what they already hold.

Mercatura Forum is Menese Protocol's pre-seed investor. Their 10,000,000 is held as a
named treasury earmark and released by the DAO's first treasury proposal. That was
agreed with Mercatura Forum in advance of this proposal, and is disclosed here rather
than settled quietly after launch.

Genesis neurons are locked for four years. An 18 month dissolve delay that cannot begin
until a 30 month vesting period ends. They vote in full from day one and cannot be sold
for 48 months.

The treasury carries named earmarks: 10,000,000 for Mercatura Forum as pre-seed
investor, 8,000,000 for the
team's redemption, 27,500,000 treasury and liquidity, 10,000,000 for exchange listing
and market making, 9,000,000 as the Tjati Council reserve for future DAO approved
raises, 7,000,000 staking emissions, 5,000,000 community, and 3,500,000 for existing
public holders.

## Existing holders

Menese already has a live token, `menes_ledger` at `drgmr-ayaaa-aaaab-aereq-cai`, from
an early public sale at $0.035 and an on chain staking programme. The DAO mints a new
governance token and a redemption canister exchanges the old one 1 for 1 from the
treasury reserve. Redemption has no deadline. Every redeemed token is burned and a
matching amount held back from treasury, so the two together never exceed the
published 100,000,000 cap.

## The swap

| Setting | Value |
|---|---|
| Minimum participants | 50 |
| Minimum raise | 100,000 ICP |
| Maximum raise | 500,000 ICP |
| Minimum per person | 5 ICP |
| Maximum per person | 60,000 ICP |
| Duration | 21 days |
| Neurons' Fund | not participating |
| Country restrictions | none |

Participants receive a basket of neurons dissolving over roughly a year, so voting
power is not immediately liquid on either side of the table. The Neurons' Fund does
not take part, so the raise comes from direct participants and their share is not
diluted by matched NNS capital.

## Swap timing

The swap opens at 12:00 UTC. The calendar date is fixed when the NNS proposal
executes rather than in this file, so the schedule follows the vote.

## Licence

The parameters in this repository are published for public review ahead of an NNS
proposal. Menese Protocol and Mercatura Forum, 2026.
