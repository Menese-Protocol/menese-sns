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

The full source of all four, with a pinned Docker builder, is held at
[Menese-External-Reviewers](https://github.com/Menese-Protocol/Menese-External-Reviewers).
Each one rebuilds byte for byte to the module hash installed on mainnet, and the
repository ships a script that checks all four against the live network in one command.

The repository is access controlled. Reviewers can request access from the forum thread
and we will grant it.

The installed module hashes need no access at all. Anyone can read the hash on each of
the four canisters straight off the network and compare it with the build.

## Token distribution

100,000,000 MENES. Fixed supply. No inflation.

| Bucket | MENES | Share |
|---|---|---|
| Team, as genesis neurons | 18,000,000 | 18% |
| Mercatura Forum, as a genesis neuron | 10,000,000 | 10% |
| Decentralization swap | 10,000,000 | 10% |
| DAO treasury | 62,000,000 | 62% |
| **Total** | **100,000,000** | **100%** |

Team and Mercatura Forum hold 28,000,000 MENES between them on the existing ledger,
staked in the sale canister. Those entitlements are unchanged in size, and both are
issued in full at genesis, in the open, as the neurons listed in `sns_init.yaml`.

The team's 18,000,000 is each person's pro rata share of the published allocation. The
team takes no part in the redemption programme below: the MENES the team holds on the
existing ledger is retired against these neurons rather than exchanged, so the same
entitlement is never issued twice.

Mercatura Forum is Menese Protocol's pre-seed investor, and its 10,000,000 is issued at
genesis as a neuron on exactly the same terms as the team's. An earlier draft parked it
in a named treasury earmark to be released by the DAO's first treasury proposal.
Issuing it here is stricter in both directions: the investor's position is locked by
the same four year schedule as the team's instead of being liquid on release, and the
DAO is not asked to approve a large treasury transfer in its opening weeks.

Genesis neurons are locked for four years. An 18 month dissolve delay that cannot begin
until a 30 month vesting period ends. They vote in full from day one and cannot be sold
for 48 months.

Every insider allocation in this DAO is a neuron in that table. None of it is a
treasury balance that becomes liquid on a vote the insiders can themselves influence.

The treasury carries named earmarks: 27,500,000 treasury and liquidity, 10,000,000 for
exchange listing and market making, 9,000,000 as the Tjati Council reserve for future
DAO approved raises, 7,000,000 staking emissions, 5,000,000 community, and 3,500,000
for existing public holders.

## Voting power at genesis

Token share and voting power are not the same thing.

Treasury tokens carry no voting power, so the 62% held by the DAO does not vote. An SNS
neuron's weight rises with its dissolve delay, and it carries no weight at all below the
26 week minimum required to vote. That makes the swap's neuron basket schedule, not just
the size of the swap bucket, the thing that decides how much say the public has on day
one.

The baskets are laddered out to 1,274 days rather than the year that is more usual.
Under a five by 73 day ladder, three of every five neurons in a participant's basket
could not vote at genesis and the public's share of voting power was 10.8%. Under the
schedule in this file it is 25.3%.

| Cohort | MENES | Share of supply | Share of voting power |
|---|---|---|---|
| Contributors and Mercatura Forum | 28,000,000 | 28% | 74.7% |
| Swap participants | 10,000,000 | 10% | 25.3% |
| DAO treasury | 62,000,000 | 62% | none |

That 74.7% is not a bloc. It is eleven separate principals, nine individual
contributors and two institutions, Mercatura Forum and MR Research. There is no common
control between them, no shared custody, and no following relationship configured at
genesis.

| Holder | Share of voting power |
|---|---|
| Mercatura Forum, the pre-seed investor | 26.7% |
| Largest of the other ten holders | 6.7% |
| Those other ten holders, combined | 48.0% |
| Swap participants, combined | 25.3% |

No holder other than Mercatura Forum reaches 6.7%. The largest single holder in the DAO
is the pre-seed investor at 26.7%, and the public who buy in this swap outweigh it.

That ratio moves toward the community as existing MENES holders redeem and stake, and
as the treasury funds the community allocation.

## Why the swap is 10% and not 20%

20% of supply is set aside to reach the public, not 10. It is split in half because the
two halves buy different things.

10% is sold on chain through the decentralization swap. The other 10% is the exchange
listing earmark: it is what pays for a tier one launchpad and a tier one centralised
exchange listing, together with the market making a listing needs to be worth having.
The SNS has no primitive for that; a swap can only sell the swap bucket. So it sits in
the treasury as a disclosed earmark and is released by a treasury proposal the DAO votes
on, once there is a venue and terms to vote on. Selling the full 20% on chain would
leave the listing unfunded.

## Existing holders

Menese already has a live token, `menes_ledger` at `drgmr-ayaaa-aaaab-aereq-cai`, from
an early public sale at $0.035 and an on chain staking programme. The DAO mints a new
governance token and a redemption canister exchanges the old one 1 for 1 from the
treasury reserve. Redemption has no deadline. Every redeemed token is burned and a
matching amount held back from treasury, so the two together never exceed the
published 100,000,000 cap.

Redemption covers everyone outside the team: MENES held directly, and MENES staked in
the sale canister, principal and accrued interest alike. The team is excluded from it
by design, because the team's entire allocation is already issued as locked neurons.

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

Participants receive a basket of eight neurons whose dissolve delays step up by 182
days, from 0 up to 1,274 days, so voting power is not immediately liquid on either side
of the table. The ladder is deliberately long: it is what carries the public's share of
genesis voting power from 10.8% to 25.3%, as set out above. The Neurons' Fund does not
take part, so the raise comes from direct participants and their share is not diluted
by matched NNS capital.

## Swap timing

The swap opens at 12:00 UTC. The calendar date is fixed when the NNS proposal
executes rather than in this file, so the schedule follows the vote.

## Licence

The parameters in this repository are published for public review ahead of an NNS
proposal. Menese Protocol and Mercatura Forum, 2026.
