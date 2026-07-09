# rulespec-tz

Tanzania (mainland) RuleSpec source registry.

This repository targets the Tanzania mainland tax-benefit surface: employment and individual income tax under the Income Tax Act (Cap. 332) as amended by the annual Finance Acts (the First Schedule individual rate schedule and the presumptive regime for individuals with turnover below TZS 100,000,000), social security contributions (the Public Service Social Security Fund under the PSSSF Act, 2018, the National Social Security Fund under the NSSF Act (Cap. 50), and National Health Insurance Fund contributions under the NHIF Act (Cap. 395)), value added tax under the Value Added Tax Act, 2014 (Cap. 148), excise duty under the Excise (Management and Tariff) Act (Cap. 147) as amended, and the transfer programmes needed for household-level calculations (the TASAF Productive Social Safety Net fixed and variable conditional cash transfers and public-works eligibility). Zanzibar has its own revenue law and its own SOUTHMOD model and is out of this repository's scope; all encoded law lives under a single `tz/` namespace covering the mainland instruments.

Tanzania's government fiscal year runs July to June and the annual Finance Act commences on 1 July. The validation year for encoded amounts is the **TAZMOD TZ_2023 system state — the rules in force on 30 June 2023** (the Finance Act, 2022 state; the Finance Act, 2023 commences 1 July 2023 and is out of the validation window); effective dates follow each instrument's own commencement provision.

## Source Priority

Policy must come from the furthest upstream available source.

1. Government Printer prints of the Acts and the annual Finance Acts (Gazette supplements; the Attorney General's Chambers Revised Editions of the Laws of Tanzania are the consolidated authority) — the authentic text of the income tax, VAT, excise and social-security law and their amendments. The Tanzania Revenue Authority laws library and TanzLII (Laws.Africa AKN mirror) are acceptable hosts for those prints, recorded with the host in manifest metadata.
2. Regulations and Government Notices made under the Acts (contribution-rate instruments, excise amendment orders) once the governing Act is identified.
3. Tanzania Revenue Authority practice notes and guidance only after the governing Act or instrument is identified.
4. TASAF/government programme documentation (PSSN operational manuals, ministerial programme documents) for rules set administratively rather than by Act.
5. Oracles only for household-level parity tests against an external source that can calculate the same household case, never as law.

## Oracle Scope

An oracle is an executable, pinned external calculator that accepts household-level inputs and returns household-level tax-benefit outputs comparable to Axiom outputs. Aggregate simulators, distributional reports, parameter documentation, and public model summaries are not oracles for RuleSpec parity, even when they are useful as background references.

TAZMOD (the SOUTHMOD tax-benefit model for mainland Tanzania, UNU-WIDER, run on the EUROMOD engine) is the parity oracle for this repository. The SOUTHMOD bundle is licensed and non-redistributable: it is referenced by path/sha only, and no bundle bytes, dataset rows, or model XML appear in this repository or its validation artifacts — only comparison statistics and model-produced values.

## Listing gates

This repo carries `app_visibility = "experimental"` in `.axiom/registry.toml` and stays out of app surfaces until:

1. The encoded surface covers the flagship calculation (individual income tax gross-to-net for a formal employee) end to end with companion tests.
2. Oracle parity suites exist and pass against TAZMOD for the encoded surface.
3. Citation paths are stable (chapter/Act-number form against the Government Printer and Revised Edition prints).
