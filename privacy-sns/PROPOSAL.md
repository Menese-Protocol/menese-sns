# Proposal to create an SNS DAO for the Menese privacy infrastructure

DRAFT, 2026-11-13. Not submitted. Token: Menese Privacy, ticker MPV.

---

## What this proposal does

It creates a DAO that owns and runs the Menese privacy infrastructure: the shielded ledgers that let people hold and
send ICP and ckBTC privately, and the key directory that lets them read their own private balance. Holders who stake the DAO's
token earn from the fees the infrastructure collects, paid in ICP and ckBTC.

Once existing MENES holders receive their 15%, the community holds 72% of the voting power, and the team and Mercatura
Forum together 28%.

We announced this in the Menese Protocol SNS thread on the forum on 21 October 2026, under the working name pMenese.
The token launches as Menese Privacy, ticker MPV. This proposal carries it out.

## Why the privacy infrastructure matters

Payments need privacy. A business does not publish its payroll, a shop does not publish its takings, and a person does
not want every payment they have ever made readable by anyone who knows their address. On a public ledger that is
exactly what happens. Without privacy, most real payments cannot move on chain at all.

The Menese shielded ledgers fix that on the Internet Computer, for ICP and for ckBTC. Coins go in, and from then on what each person holds and
whom they pay is hidden, while the ledger still proves on chain that every payment is valid and that no coin is created
from nothing. People can leave at any time, back to an ordinary ICP or ckBTC account.

Both are live on mainnet. People already hold ICP privately in them today, and every payment is checked by a
zero-knowledge proof inside the canister before it is accepted.

The proving keys come from a public setup ceremony that anyone could join. The coordinator canister that ran it is
blackholed, so nobody controls it, and its final randomness was taken from a named ICP ledger block. Each person's
viewing keys come from the Internet Computer's own vetKeys, so no server of ours ever sees them.

The code is open source: github.com/Menese-Protocol/Shielded-Ledger-Hivemind. The work comes from the Hive Mind research
programme funded by Mercatura Forum, and a wider version of the same design has been accepted for publication at an
IEEE conference.

## Why decentralize it

A privacy layer is only as trustworthy as whoever can change it. While one company holds the keys to upgrade the
shielded ledger, its users have to trust that company. Once a DAO holds them, an upgrade needs a public proposal and a
vote, and anyone can read the proposed code before it lands.

This DAO does three things.

1. **It takes the privacy infrastructure out of one company's hands.** Upgrades, fees and settings change only by vote.
2. **It pays the people who secure it.** The fees the infrastructure collects go to those who stake and vote, so the
   people with a say over its future are the ones with a reason to keep it safe.
3. **It makes privacy shared infrastructure for the ecosystem.** It funds a team that works only on adoption, and it
   gives every other project a base it can build private payments on and rely on.

## Why this is good for the Internet Computer

Private payments rest on pieces that are hard to build and rare on any chain: zero-knowledge proofs checked inside a
smart contract, proving keys that the public helped create, and keys for each person that no server ever holds. The
Menese shielded ledger has all three running on the Internet Computer today, in the open.

- **Proofs checked on chain.** Every private payment carries a zero-knowledge proof, and the canister checks it itself
  before it accepts the payment. Nothing is checked on a server somewhere else.
- **Keys made in public.** The proving keys came from a public ceremony. Its coordinator canister is blackholed, and its
  final randomness came from a named ICP ledger block that nobody could choose in advance.
- **Keys nobody else holds.** Each person's viewing keys come from vetKeys, the Internet Computer's own threshold key
  derivation, so no company and no server ever has them.
- **Open and checkable.** The code is open source and the build is reproducible.

Every team that wants private payments on the Internet Computer would otherwise have to build these pieces again. A DAO
that owns them turns them into shared infrastructure for the whole ecosystem:

- **A team that works only on adoption.** The DAO funds a team dedicated to the privacy infrastructure, answerable to
  its holders: bringing more tokens into private pools, helping wallets, exchanges and apps add private payments, and
  supporting the developers who build on it.
- **Build on it, don't rebuild it.** Any project can add private balances and private payments by using the shielded
  ledger and the Menese SDK, and the fees it brings in pay for the work.
- **A base others can rely on.** Every change goes through a public proposal and a vote, so a project that builds on it
  can see and weigh in on anything that would affect it.

## What comes next: more tokens, more chains, and stocks

ICP and ckBTC are the first two. The same design can carry any token, and the Menese multichain OS already signs and
settles transactions on the chains people use, through the Internet Computer's chain-key signing, and already gives
people access to tokenized stocks and real-world assets. That lets the privacy infrastructure grow to more tokens, more
chains, and stocks too: a person brings coins or shares in, holds them privately, and moves them back out, with no
bridge in the middle. Nobody watching the chain sees what a person holds in their portfolio.

Every new shielded ledger comes under this DAO. Each one is added by a public proposal that registers it with the DAO,
its fees flow to the same fee splitter, and stakers earn from all of them. The more the privacy infrastructure is used,
across more tokens, chains and stocks, the more it pays the people who govern it.

## What the DAO controls

| Canister | ID | What it does |
|---|---|---|
| zk_ledger | 3pwrb-oiaaa-aaaao-bbqba-cai | The shielded ICP ledger: private balances, private payments, proof checking, fees |
| zk_ledger_ckbtc | g5hy5-3yaaa-aaaao-bbsea-cai | The shielded ckBTC ledger: the same proving keys and checks, for Bitcoin held privately |
| key_directory | 3gv25-yaaaa-aaaao-bbqaq-cai | Gives each person their viewing keys through vetKeys, so they can read their own private balance |
| fee_splitter | 2t23t-taaaa-aaaae-ahfoa-cai | Collects the fees and pays them out in the shares below |
| holder_canister | ecx5m-jaaaa-aaaak-qzfyq-cai | Holds the 15% for existing MENES holders from genesis and hands it to them, with no admin |

Each shielded ledger's administrator role, and the key directory's, passes to the DAO's governance canister
automatically when the DAO is created: each canister finds the governance canister through the DAO's root canister and
binds to it once, permanently, with no key involved. From then on fees, the fee recipient, new pools and key limits
change only by vote, and no team key can change them. Both ledgers already send their fees to the fee splitter.

## You can check this yourself

Every canister the DAO takes over is open source, and the build is reproducible: building the published source gives
the same module hash that is installed on mainnet. Anyone can read that hash straight off the network
(`dfx canister info <id> --network ic`) and compare.

| Canister | Module hash (sha256) | Source |
|---|---|---|
| zk_ledger `3pwrb` | `df8453a91cda7dc894024219ecfcabdbc1dc6660b37138d551eca4a24e52be6e` | github.com/Menese-Protocol/Shielded-Ledger-Hivemind, tag `3pwrb-patched-df8453a9` |
| zk_ledger_ckbtc `g5hy5` | `4c26e0669b33f03679fc9fa11e8aa06e760b4b8beccf54edf601022d8a08014b` | the same repository, tag `g5hy5-patched-4c26e066` |
| key_directory `3gv25` | `b052e46a1c54043a985e4f92352f04684f123622ad86232764d4ae4a9c4f0771` | the same repository, tag `3gv25-patched-b052e46a` |
| fee_splitter `2t23t` | `daccbe9bfcaa4a8d9c2d86feeb1dddd692ab3af1884d7893b3c7681273f6b997` | github.com/Menese-Protocol/mpv-fee-splitter |
| holder_canister `ecx5m` | `d3c818b5e07d9945b63d6ea57a457338a0cd5f3acd72d07be0b3ac6833174b20` | github.com/Menese-Protocol/menese-redemption, tag `holder-d3c818b5` |

Each repository's README gives the exact build command.

## Token distribution

100,000,000 MPV. Fixed supply. No inflation.

| Who | MPV | Share |
|---|---:|---:|
| Decentralization swap | 57,000,000 | 57% |
| Team, as genesis neurons | 18,000,000 | 18% |
| Mercatura Forum, pre-seed investor, as genesis neurons | 10,000,000 | 10% |
| Existing MENES holders | 15,000,000 | 15% |

The team and Mercatura Forum receive exactly what they received in the Menese Protocol SNS proposal (144002): 18% to
the team, each person the same amount as there, and 10% to Mercatura Forum, the pre-seed investor. It is locked the
same way: an 18 month dissolve delay that cannot begin until a 30 month vesting period ends, so none of it can
be sold for 48 months. It votes from day one.

The team share is not one institution. It is held by eleven separate holders, each with their own principal and their
own neurons: Mercatura Forum and ten individual team members and advisors. Each of them votes their own neurons; nobody
votes on behalf of the others. Every one of them has confirmed in public, from their own GitHub account, that the
principal below is theirs and that they accept the lock terms: github.com/Menese-Protocol/menese-sns/issues/1. The
MPV allocation uses those same confirmed principals and the same amounts, so anyone can match every line of the
table below to the person who holds it.

| Holder | Principal | MPV |
|---|---|---:|
| Timo | `sugn6-7mjeq-5kzk5-7dph2-w6sq7-ev56n-qt7yd-a5l66-birkn-kpdx5-gqe` | 2,500,002 |
| Menese team | `vw2b5-vc43c-et5cx-guvr4-yt5y6-ttypw-3mef6-jmxcm-hvwby-5l3oq-yae` | 2,499,998 |
| Nour | `tv73a-nsnvr-u3ruc-sly4k-2fygz-wft3h-gdqve-hdw5q-msmac-gvnnk-yae` | 2,250,000 |
| Jumana | `a2gxl-ixyyn-gc6u3-uksho-svlmu-h7wm7-mnjer-e4ynk-fcw35-r4peg-iqe` | 2,250,000 |
| Wael | `4b2em-p3hvn-gyjjn-zvbwo-dapoy-5dzl4-jfnfy-sbx3u-lp5cq-5pldy-bae` | 2,250,000 |
| Abdelrahman A. | `3klrp-ru37l-kaitp-4dvfu-ms5vb-l336m-q35vy-76aak-gylco-arjyx-tae` | 2,000,000 |
| Adham | `atwek-uwz7p-p72f5-32zd7-rtsqt-uhvo6-ghujz-fwm2s-gjheg-vxpku-hae` | 1,500,000 |
| Abdelrahman E. | `5b6kn-x63mz-2ezyn-q4paf-6hx7q-3mwyw-eng6g-4lfla-ydt3n-t7ddw-7ae` | 1,500,000 |
| Saher | `m4kw6-unwcq-rk7b7-7iyfp-a5f4q-e2ysz-jmr75-hpgrt-fiuh6-l5gr3-mae` | 1,000,000 |
| Andy | `eoogn-23szv-p27ny-5btdd-n7mab-klzqz-wlk7f-okepn-hlj7m-collr-sqe` | 250,000 |
| Mercatura Forum | `5elw2-6iogf-6v3bc-weq6n-uhiwc-7umyq-mpxo5-z35cy-6qybd-5sktc-cqe` | 10,000,000 |

## Existing MENES holders

15% goes to the people who hold MENES when the swap ends, directly or staked in the Menese sale canister, in proportion
to what they hold. The holder table is fixed at the last MENES ledger block at or before the swap's closing time, and
the holder canister builds it itself from the MENES ledger when the swap closes. It publishes the table with the block
index, and a public script rebuilds the same table from the ledger, so anyone can check it. Menese's contracts, the unsold supply and the team's staked allocation are left out, since the team's share is in the
table above. MENES the team holds liquid counts like anyone else's.

The holders' 15,000,000 MPV never pass through the DAO treasury. The SNS creates them at genesis as nine neurons owned
by the holder canister, whose source is public at github.com/Menese-Protocol/menese-redemption and whose module hash is
in this proposal. It has no admin and cannot mint. The MPV transfer fee should not be changed until it reports that every holder is paid. When the swap closes it builds the table, and no method can add,
change or remove an entry after that. It then hands every holder their share on its own, with no DAO proposal. If the
table does not agree with the MENES ledger's own totals, it pays nobody.

Internet Identity gives a person a different principal in each app, so the principal that holds MENES in the Menese
app cannot manage neurons in the NNS dapp. Each holder therefore names, once, from the Menese app, the principal that
should own their neurons, for example their NNS dapp principal. Only the holder can name it, nobody can change it once
delivery has started, and a basket waits, with no deadline, until its holder has named one.

Every holder receives their MPV on the same terms as the people who buy in the swap: a basket of nine neurons they
control outright, with dissolve delays from 0 to 1,456 days, 182 days apart. From the day it lands, eight of the nine
vote and earn. A holder whose share is too small for nine minimum-size neurons receives as many as it fills, each with
a dissolve delay of 182 days or more, so every one of them votes and earns. Nobody is paid in liquid MPV. A share too
small for even one neuron (10 MPV) is left out, and it goes to the other holders in proportion; the list of these is
published with the table.

Each holder's basket is split off the holder canister's nine neurons, so it keeps the same dissolve delays and age.

## What stakers earn

The DAO's token pays from real fees. The ICP ledger charges 0.1 ICP per private payment, the ckBTC ledger 83 satoshis,
and both charge 0.3% when coins leave the private pool. After the DAO's canisters are kept topped up with cycles, the fees are shared:

| Share | Goes to |
|---:|---|
| 65% | Staked MPV, by voting power |
| 20% | Buying back MENES, which is then burnt |
| 10% | DAO development and growth |
| 5% | Governance rewards, to neurons that vote in the period |

Fees are shared every quarter (91 days). The fees both ledgers have earned since they went live are shared in the DAO's
first quarter. Payouts are claimed, not pushed: each quarter the fee splitter records every
neuron's share, and the neuron's holder claims it. Unclaimed shares stay claimable.

At the start of each quarter the fee splitter tops up any DAO canister below 10 trillion cycles to 25 trillion,
spending at most 50 ICP on cycles in a quarter. The buy-back spends its share in buys of 0.1 to 1 ICP, one to six hours
apart, and never pays more than 0.057 ICP for one MENES.

The shares live in the fee splitter and change only by a DAO proposal. Holders can raise the governance reward as the
fees grow.

## Voting power: the community holds the majority

The community holds 72% of the voting power, and the team and Mercatura
Forum together 28%.

| Group | Share of supply | Share of voting power |
|---|---:|---:|
| Swap participants | 57% | 57.1% |
| Existing MENES holders | 15% | 15.0% |
| **Community total** | **72%** | **72.1%** |
| Team | 18% | 17.9% |
| Mercatura Forum | 10% | 10.0% |

The team's 17.9% is itself spread across ten people, and no one of them holds more than 2.5% of the voting power.
Mercatura Forum holds 10.0%.

MENES holders vote on exactly the same terms as the people who buy in the swap: the same nine-neuron basket, the same
dissolve delays, the same weight per token. No group gets a better rate.

How the holders' share arrives. The holders' 15% exists as neurons from genesis, owned by the holder canister, so these
figures hold from day one. The holder canister never votes. Until a holder's basket is handed over, its votes are not
cast by anyone, and from the moment it is handed over the holder votes it. The SNS can create at most 100 neurons at
genesis, so the holders' baskets are split off the holder canister's nine neurons after the swap rather than created
one by one at genesis.

## The swap

| Setting | Value |
|---|---|
| Minimum raise | 100 ICP |
| Maximum raise | 200,000 ICP |
| Minimum participants | 5 |
| Minimum per person | 100 ICP |
| Maximum per person | 20,000 ICP |
| Duration | 7 days |
| Neurons' Fund | not participating |

Participants receive a basket of neurons whose dissolve delays step up by 182 days, as in the Menese Protocol SNS, so
most of each basket votes from the start.

## Governance

The voting reward rate is 0%. The supply is fixed and the DAO does not print new tokens to pay voters. Voters are paid
from the fees.

If the swap does not complete, control of these canisters returns to Mercatura Forum and the Menese team, as in the
Menese Protocol SNS. The Menese team runs its upgrades through an MPC setup, so no single person's key can change a
canister.
