# Automated Findings
https://gist.github.com/CloudEllie/eafeb9865761200397c00d70febe5f9d

## Important Findings
- [M‑02]	Excess funds sent via msg.value not refunded
- [M‑05]	Use of transferFrom() rather than safeTransferFrom() for NFTs in will lead to the loss of NFTs
- [L‑02]	calc_token_amount() has slippage added on top of Curve's calculated slippage
- [L‑28]	latestAnswer() is deprecated

# Certora Formal Verficiation Audit Report
https://3014726245-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FfBay3bZwWmLdUX02P7Qc%2Fuploads%2FZ0lrDxhdqWHMX5UdMrtC%2FTapioca_Certora_Audit.pdf?alt=media&token=9fbc7bd3-cccd-42a1-b6d3-22c36e2b795f
https://3014726245-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FfBay3bZwWmLdUX02P7Qc%2Fuploads%2FPIVXvEmuf0FzFZi1poyS%2FTapioca_Certora_Audit%20(Appendix).pdf?alt=media&token=49ad2755-e67c-4fb7-9d6b-3fea9081be12

## Coverage
YieldBox.sol

## Important Findings
- ERC721 assets can be withdrawn without burning any shares.
- First depositor accounting logic bug
- First depositer can block subsequent deposits from other userss
- DepositETHAsset() uses a different amount than provided msg.value(DoS)
- BoringBatchable's Batch() function can delegate-call a payable function `msg.value` multiple times

# Audit Report for similar projects
- [Alchemix v2 report by Runtime Verification](https://github.com/runtimeverification/publications/blob/main/reports/smart-contracts/Alchemix_v2.pdf)
- [Radiant Capital v2 report by PeckShield](https://github.com/peckshield/publications/tree/master/audit_reports/PeckShield-Audit-Report-RadiantV2-v1.0.pdf)
- [Radiant Capital v2 report by Zokyo](https://github.com/zokyo-sec/audit-reports/blob/main/Radiant/Radiant%20Capital%20audit%20report_06_March.pdf)
- [Abracadabra.money audit report by DefiYield](https://files.safe.de.fi/safe/files/audit/pdf/abracadabra.pdf)

# Reference
https://solodit.xyz/