# FlapJax Series 3 — Q103: On-chain audit of treasury FLAPJAX transfers, 2026-11-19 (COT)

**Task:** Taskmarket (Base) task `0x6ebb27085d014b4e4b8cc915c38760ba2578c8208cc75e6466adfd62129bf48f`, reference `TSK-WJ1N1NGR`.
**Question:** list every FLAPJAX transfer out of the FlapJax treasury during **2026-11-19 COT (UTC-5)**, and for each recipient find the wallet that first sent it BNB.

**Scope:** read-only chain research. No wallet was connected, nothing was signed, paid, minted, or submitted. All numbers below come from data actually fetched from public BSC endpoints on 2026-11-21 (see Methodology). Machine-readable copy: [`data.json`](data.json).

## Summary

| Item | Value |
|---|---|
| Day | 2026-11-19 COT = 2026-11-19 05:00:00 UTC → 2026-11-20 04:59:59 UTC |
| First BSC block of the day | **134,443,555** (ts 1795064400 = 2026-11-19 05:00:00 UTC; block before, 134,443,554, is 04:59:59 UTC) |
| Last BSC block of the day | **134,635,477** (ts 1795150799 = 2026-11-20 04:59:59 UTC; next block, 134,635,478, is 05:00:00 UTC) |
| Blocks in range | 191,923 |
| FLAPJAX transfers out of treasury | **11** |
| Total FLAPJAX sent | **225,000** (6 × 25,000 + 5 × 15,000 — exact, no dust) |
| Distinct recipients | **8** |
| Distinct operators evidenced by first-BNB-funder links | **2** (the treasury itself; wallet `0xa5a5…`) |
| Transfers I could not explain | **None in the transfer set.** See "Unexplained / unattributable" for the 5 recipients with no BNB-funding link. |

## The transfers — complete table

Treasury: `0x7C34E9e21eE28A49Ff0b84B61774119E6633359f`
Token: FLAPJAX (BEP-20, BSC) `0x90c8889f428F9Ebb77BB8f15CAD3a50a9aC680df`, 18 decimals.
All 11 transfers are `Transfer` events with `from` = treasury. Times in COT (UTC-5).

| # | Time (COT) | Block | Tx hash | Recipient | Amount (FLAPJAX) |
|---|---|---|---|---|---|
| 1 | 2026-11-19 09:13:04 | 134517255 | `0x6eeb0f6bcc12c8301151ae9033bce03affcb59da3ea8447e5c33aa9597dc7d76` | `0x97cd18b8bbb629b17675d868259ea84c0a2a5a9c` | 25,000 |
| 2 | 2026-11-19 09:13:28 | 134517309 | `0xdca584c9e5fb0c2cadea0bcf6f40cd33faa7294d543be4d4dc73e7da64c6a6ac` | `0x56b40205e0f8cd49eecb253ae82a5308f45a1cf3` | 15,000 |
| 3 | 2026-11-19 09:13:53 | 134517364 | `0x4a4d4715336bcda9acdc52a751694a5cbf002b38931f0a68f928bc3e06b79fcd` | `0xac958f0925a31a2c3844179ab62f12d480baa76d` | 15,000 |
| 4 | 2026-11-19 13:06:02 | 134548305 | `0xb3740e7d9ec21caa0467986bb254db0809ad60cad5147bc5282fa17f19a60eab` | `0xa15c58e7008fc7a0331cfcc86a28af99fd21b93c` | 25,000 |
| 5 | 2026-11-19 13:06:26 | 134548358 | `0xdc3b42c6b34c68d1fc94bbc475ccb857a68b34f8e36547df2e0f0b51053a2a91` | `0xa4c86f4e9d9ec8990f843aa49470083cece5f908` | 15,000 |
| 6 | 2026-11-19 18:23:45 | 134590662 | `0xaab1f7bfcfa7ef9f3e641871f318f3ce7e89c4e8146276f24b4f4095eef119f0` | `0xaf7f0f0fe64e4304a6e48f89b714b21746f0c0f6` | 25,000 |
| 7 | 2026-11-19 18:24:08 | 134590714 | `0x5222ba3fd4d77995809760747b870387a326d65e571aa6cab70c5062628deff4` | `0xaf7f0f0fe64e4304a6e48f89b714b21746f0c0f6` | 25,000 |
| 8 | 2026-11-19 18:24:32 | 134590766 | `0x992f570e3616a94c6cec3e488da88dc6ecbd5ab6160c4ab0dac139a193f59b1c` | `0x97cd18b8bbb629b17675d868259ea84c0a2a5a9c` | 25,000 |
| 9 | 2026-11-19 18:24:55 | 134590817 | `0x0cc4ace68ee20844824ab4bee921148ec7f65e8de4547dde300c6312a6a95b90` | `0x97cd18b8bbb629b17675d868259ea84c0a2a5a9c` | 25,000 |
| 10 | 2026-11-19 18:25:18 | 134590868 | `0xdc412e60c6ccf558d81160cfc43e9afa15c7dcecbf4e0289afe568235cedb36a` | `0xfd5efa5c47fb3be071b2fd38fc88dfa30318c5d2` | 15,000 |
| 11 | 2026-11-19 18:25:44 | 134590926 | `0x129208753d8298f42c584af4796eff3adfba741cd2aaf389494473a6ca56ea0e` | `0xca58696564492ef9c3229c89072365b253bda246` | 15,000 |

The transfers cluster in three bursts: 09:13 (3 txs), 13:06 (2 txs), 18:23–18:25 (6 txs). Every amount is an exact round number (25,000 or 15,000 FLAPJAX, i.e. raw values `25000000000000000000000` / `15000000000000000000000`). No other treasury-out FLAPJAX transfer exists in the day's block range — the full-range log scan (see Methodology) returned 0 logs outside the three chunks above.

Per-recipient totals:

| Recipient | Transfers | FLAPJAX received |
|---|---|---|
| `0x97cd18b8bbb629b17675d868259ea84c0a2a5a9c` | 3 (#1, #8, #9) | 75,000 |
| `0xaf7f0f0fe64e4304a6e48f89b714b21746f0c0f6` | 2 (#6, #7) | 50,000 |
| `0xa15c58e7008fc7a0331cfcc86a28af99fd21b93c` | 1 (#4) | 25,000 |
| `0x56b40205e0f8cd49eecb253ae82a5308f45a1cf3` | 1 (#2) | 15,000 |
| `0xac958f0925a31a2c3844179ab62f12d480baa76d` | 1 (#3) | 15,000 |
| `0xa4c86f4e9d9ec8990f843aa49470083cece5f908` | 1 (#5) | 15,000 |
| `0xfd5efa5c47fb3be071b2fd38fc88dfa30318c5d2` | 1 (#10) | 15,000 |
| `0xca58696564492ef9c3229c89072365b253bda246` | 1 (#11) | 15,000 |

## First BNB funder per recipient

Method: for each recipient, find the first block where its BNB balance became non-zero (binary search on historical `eth_getBalance` via the Blast public RPC, which serves archive state), confirm balance 0 in the block before and at spot checks 1M / 5M / 20M blocks earlier, then identify the funding transaction from that block's full transaction list. For wallets with no funding, the proof is `eth_getCode` = `0x` (plain EOA) + transaction count 0 + BNB balance 0 at latest: an EOA that never sent a transaction and holds 0 BNB cannot have received BNB, because received BNB could only leave via its own signed transaction.

| Recipient | First BNB funder | Funder tx | Funding block / time (COT) | Amount (BNB) |
|---|---|---|---|---|
| `0x97cd18b8bbb629b17675d868259ea84c0a2a5a9c` | **none — never received BNB** | — | — | — |
| `0x56b40205e0f8cd49eecb253ae82a5308f45a1cf3` | **none — never received BNB** | — | — | — |
| `0xac958f0925a31a2c3844179ab62f12d480baa76d` | **none — never received BNB** | — | — | — |
| `0xa4c86f4e9d9ec8990f843aa49470083cece5f908` | **none — never received BNB** | — | — | — |
| `0xaf7f0f0fe64e4304a6e48f89b714b21746f0c0f6` | **none — never received BNB** | — | — | — |
| `0xa15c58e7008fc7a0331cfcc86a28af99fd21b93c` | `0xa5a5491bca93dd4c076e4906e79e7673f4a5a142` | `0x9a2aad5e93baea6dbee144b4a9615172a6dd82eddd26007186436a39caa27639` | 132005597 / 2026-11-06 07:04:40 | 0.000193009353538407 |
| `0xfd5efa5c47fb3be071b2fd38fc88dfa30318c5d2` | **the treasury itself** (`0x7c34e9e21ee28a49ff0b84b61774119e6633359f`) | `0x13ff2afcbc50a6ef03f603650ad84642c23c9c26a896612e8e16f5698e6ef2c6` | 126835416 / 2026-10-10 08:25:35 | 0.0005 |
| `0xca58696564492ef9c3229c89072365b253bda246` | **the treasury itself** (`0x7c34e9e21ee28a49ff0b84b61774119e6633359f`) | `0x87443eff758296585f6d6eb7b68800ea6c73f143239e60541a6ef5b1f072d456` | 130097514 / 2026-10-27 08:29:06 | 0.0005 |

Notes:

- The two treasury fundings are plain transfers (`input 0x`), exactly 0.0005 BNB each — the same fixed gas-money amount, weeks before the FLAPJAX payouts.
- The `0xa15c…` funding is a direct value transfer from `0xa5a5491bca93dd4c076e4906e79e7673f4a5a142` with a 32-byte input (selector `0xf297dd3c` + 28 bytes) to the recipient EOA. The funder is itself an EOA (`code 0x`), nonce 752,675, holding 1.7838561837042337 BNB at 2026-11-21 — a very active wallet, not the treasury.
- The funder `0xa5a5…` was itself first funded by `0xf70da97812cb96acdf810712aa562db8dfa3dbef` — 3.0 BNB, tx `0x72d0a1e82368e88a6dab7045927f2b1610b52692f60be6b89cd003ec383d994a`, block 116978704, 2026-08-19 23:47:01 COT. So the `0xa15c…` funding chain does **not** lead back to the treasury.

## Funder groups

| Group | First funder | Recipients | FLAPJAX in group |
|---|---|---|---|
| T | Treasury `0x7c34…359f` | `0xfd5e…`, `0xca58…` | 30,000 |
| A | `0xa5a5491bca93dd4c076e4906e79e7673f4a5a142` | `0xa15c…` | 25,000 |
| ∅ | None (never received BNB) | `0x97cd…`, `0x56b4…`, `0xac95…`, `0xa4c8…`, `0xaf7f…` | 170,000 |

**Operators implied: at least 2** — the treasury operator (group T, and the treasury itself sent all 11 FLAPJAX transfers) and whoever operates `0xa5a5…` (group A). The 5 recipients in group ∅ have no BNB-funding link to any operator, so they cannot be attributed to either group from funding data alone. They may belong to either operator (or others) — the chain data here does not say. Note the largest recipient by FLAPJAX, `0x97cd…` (75,000), sits in group ∅.

## Uncovered transaction (candidate)

**`0x129208753d8298f42c584af4796eff3adfba741cd2aaf389494473a6ca56ea0e`** — transfer #11: 15,000 FLAPJAX, block 134590926, 2026-11-19 18:25:44 COT, treasury → `0xca58696564492ef9c3229c89072365b253bda246`.

Chosen because its recipient's full chain story is verified end-to-end: first funded with BNB **by the treasury itself** (0.0005 BNB on 2026-10-27, tx `0x87443eff758296585f6d6eb7b68800ea6c73f143239e60541a6ef5b1f072d456`), then paid 15,000 FLAPJAX by the treasury on 2026-11-19. It is a genuine transfer from the audited day, checked in full.

## Unexplained / unattributable

- **Five recipients received FLAPJAX but never received BNB** (`0x56b4…`, `0x97cd…`, `0xa4c8…`, `0xac95…`, `0xaf7f…` — 170,000 of the 225,000 FLAPJAX, including the two largest recipients). This is a finding, not a data gap: each is a plain EOA with nonce 0 and 0 BNB balance, so no BNB funder exists to find. Who operates these wallets cannot be determined from BNB funding; it would need another link (e.g. shared funding of a different asset, or off-chain records).
- **The operator behind `0xa5a5491bca93dd4c076e4906e79e7673f4a5a142` is not identified** — only that it is distinct from the treasury (its own first funder is `0xf70d…`, not the treasury). It is a high-activity EOA (nonce 752,675), which suggests a bot/service wallet rather than a one-off personal wallet, but that is an inference, not an identification.

## Methodology

1. **Day → blocks.** Binary search on `eth_getBlockByNumber` timestamps over public BSC RPCs for the first block with timestamp ≥ 2026-11-19 05:00:00 UTC (1795064400) and the first block ≥ 2026-11-20 05:00:00 UTC (1795150800), minus one. Neighbors re-verified after the search: 134,443,554 = 04:59:59 UTC, 134,635,478 = 05:00:00 UTC. (BSC block time here is ~0.45 s, ~191,923 blocks/day.)
2. **Transfers.** `eth_getLogs` on the FLAPJAX contract, topic0 = `Transfer(address,address,uint256)` (`0xddf252ad…`), topic1 = treasury, over the full range in 2,000-block chunks (96 chunks). 11 logs found — 3 in chunk 134515555–134517554, 2 in 134547555–134549554, 6 in 134589555–134591554 — and 0 in the other 93 chunks. The scan completed with no failed or skipped chunks. Amounts are exact integer raw values (18 decimals); totals computed from integers, not floats.
3. **First BNB funders.** Historical `eth_getBalance` via the Blast public RPC (`https://bsc-mainnet.public.blastapi.io`), which serves archive state (verified: treasury balances at blocks 130,000,000 and 134,000,000 return real non-zero values; standard public nodes return "missing trie node" / "state pruned" for the same queries). Binary search for the first block with balance > 0; funding tx read from that block's full transaction list (`eth_getBlockByNumber` with transactions). Pre-funding spot checks at −1M/−5M/−20M blocks all returned 0. Never-funded proof: `eth_getCode` = `0x` + nonce 0 + balance 0 (see table intro).
4. **No API keys used.** All data came from public JSON-RPC endpoints; no key is stored anywhere in this audit. (Etherscan V2 keyless access returns "Free API access is not supported for this chain" for BSC; `api.bscscan.com` redirects to API docs; `bscscan.com` web returns 403; Subsquid archive was unreachable from this VM. None of those were needed: direct RPC + Blast archive covered everything.)

## How to re-check on BscScan

- Day range: token page `https://bscscan.com/token/0x90c8889f428F9Ebb77BB8f15CAD3a50a9aC680df` → "Transfers" filtered by `a=0x7C34E9e21eE28A49Ff0b84B61774119E6633359f`, or the address page `https://bscscan.com/address/0x7C34E9e21eE28A49Ff0b84B61774119E6633359f#tokentxns` — look for 2026-11-19 entries; each tx hash in the table above opens its own page (`https://bscscan.com/tx/<hash>`).
- Day bounds: block `134443555` (2026-11-19 05:00:00 UTC) and block `134635477` (2026-11-20 04:59:59 UTC) at `https://bscscan.com/block/<number>`.
- Funders: open each recipient address page and sort its BNB transactions oldest-first; e.g. `0xca58…`'s first BNB receipt is tx `0x87443eff758296585f6d6eb7b68800ea6c73f143239e60541a6ef5b1f072d456` from the treasury, and `0xfd5e…`'s is `0x13ff2afcbc50a6ef03f603650ad84642c23c9c26a896612e8e16f5698e6ef2c6`, also from the treasury. The five never-funded recipients show no BNB transactions at all.
- `uncoveredTx` candidate: `https://bscscan.com/tx/0x129208753d8298f42c584af4796eff3adfba741cd2aaf389494473a6ca56ea0e`.

## Limitations

- The first-funder search assumes a wallet's BNB balance does not return to exactly 0 and get re-funded before the found block. Spot checks at −1M/−5M/−20M blocks and monotonically decreasing balances since funding support the single-funding reading for all three funded wallets.
- Internal-transaction funding was not traced with `debug_trace*`: it was not needed, because each funded wallet's first balance increase coincides exactly with a direct value transfer in the same block, which fully explains the increase. Had a wallet's first increase shown no matching direct tx, a trace would have been required — no such case occurred.
- Recipient addresses are shown in lowercase as returned by the RPCs (checksummed forms differ only in letter case).

*Audit performed 2026-11-21 (WIB). Latest block observed during checks: 134,833,819.*
