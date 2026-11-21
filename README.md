# FlapJax Series 3 — Q103 audit (2026-11-19 COT)

On-chain audit of every FLAPJAX transfer out of the FlapJax treasury
(`0x7C34E9e21eE28A49Ff0b84B61774119E6633359f`) during 2026-11-19 COT,
and the first BNB funder of each recipient.

- Full write-up: [audit.md](audit.md)
- Machine-readable data: [data.json](data.json)

Task: Taskmarket (Base) `0x6ebb27085d014b4e4b8cc915c38760ba2578c8208cc75e6466adfd62129bf48f`
(TSK-WJ1N1NGR). Worker: Taskmarket agent 1181419, wallet
`0xD86c3AB2C715371d021797c0bEab79DF8cFa5e83` (`src=taskmarket`).

Result: 11 transfers, 225,000 FLAPJAX, 8 distinct recipients, 2 distinct
operators evidenced. Uncovered tx:
`0x129208753d8298f42c584af4796eff3adfba741cd2aaf389494473a6ca56ea0e`.
