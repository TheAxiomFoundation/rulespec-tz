# rulespec-tz Agent Notes

This repo stores United Republic of Tanzania RuleSpec source registry materials, oracle references, and encoded policy rules: mainland instruments under the `tz/` namespace and Zanzibar instruments under the `tz-znz/` namespace (the rulespec-us federation pattern). Union law (the Income Tax Act Cap. 332 chain, the TASAF PSSN transfers) is encoded once under `tz/` and applies to both jurisdictions.

## Scope

- `tz/statutes/`: Tanzanian Acts — the Income Tax Act (Cap. 332) as amended by the annual Finance Acts (First Schedule individual rates and the presumptive regime), the PSSSF Act, 2018, the NSSF Act (Cap. 50), the NHIF Act (Cap. 395), the Value Added Tax Act, 2014 (Cap. 148), the Excise (Management and Tariff) Act (Cap. 147) as amended, and other primary law needed for tax-benefit modeling.
- `tz/regulations/`: regulations and Government Notices made under the Acts (contribution-rate instruments, excise amendment orders).
- `tz/policies/`: TRA practice notes captured as verified reproductions where a primary print is not digitized, and social-protection programme rules (the TASAF Productive Social Safety Net transfers) set administratively.
- `tz-znz/statutes/`, `tz-znz/regulations/`, `tz-znz/policies/`: Zanzibar instruments — the VAT Act 4/1998, the Excise Duty Act 8/2017, the ZSSF Act 2/2005 and its amending instruments (Written Laws (Miscellaneous Amendment) Act 10/2022), and administratively set programmes (the Zanzibar Universal Pension Scheme / Pencheni Jamii, corpus tranche 2). ZANMOD v1.1 (2019–24) is the Zanzibar validation frame.
- `programs/`: declarative compose specs (one per jurisdiction/program/period).
- `data/coverage/`, `data/oracles/`: coverage backlog and comparison references. These are never legal authority.

## Do

- Start from the furthest upstream source: Government Printer / Gazette-supplement prints and the Attorney General's Chambers Revised Editions first (TRA's laws library and TanzLII, the Laws.Africa AKN mirror, are acceptable hosts for those prints — record the host in manifest metadata), regulations and Government Notices next, TRA guidance and programme manuals only after the governing instrument is identified.
- Add RuleSpec under `tz/statutes/`, `tz/regulations/`, or `tz/policies/` with companion `.test.yaml` files.
- Cite corpus paths from modules via `module.source_verification.corpus_citation_path` (or `corpus_citation_paths`).
- Use the TAZMOD TZ_2023 system state as the validation year: the rules in force on 30 June 2023, i.e. the Finance Act, 2022 state (Tanzania's fiscal year runs July–June and Finance Acts commence 1 July; the Finance Act, 2023 is out of the validation window). Indexed/annual values must be corpus-grounded, never invented.
- Keep exact oracle versions in `data/oracles/oracle-index.json`. The TAZMOD bundle (SOUTHMOD A4.0) is licensed and non-redistributable — never commit bundle bytes, dataset rows, or model XML; only comparison statistics and TAZMOD-produced values may be recorded.
- Sync `axiom-encode` and `.axiom/toolchain.toml` before substantial encoding runs (fetch origin and read the current version before every encode run and before choosing any version-bump number).

## Do Not

- Use TRA calculators, PAYE ready-reckoners, or third-party tax alerts as the first legal source when an Act or instrument governs the rule.
- Invent, round, or interpolate any Tanzanian monetary amount, rate band, or threshold. Every number must come verbatim from a captured official provision.
- Migrate TAZMOD, EUROMOD/SOUTHMOD, or agency calculator code mechanically as RuleSpec.
- Add generated source payload dumps, formula artifacts, `parameters.yaml`, or standalone YAML fixtures outside allowed RuleSpec roots.
- Hand-copy statute text into RuleSpec without a corpus `citation_path`.
