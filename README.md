# Ledger Ajuna App

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![GithubActions](https://github.com/zondax/ledger-ajuna/actions/workflows/main.yml/badge.svg)](https://github.com/Zondax/ledger-ajuna/blob/main/.github/workflows/main.yaml)

---

![zondax_light](docs/zondax_light.png#gh-light-mode-only)
![zondax_dark](docs/zondax_dark.png#gh-dark-mode-only)

_Please visit our website at [zondax.ch](https://www.zondax.ch)_

---

This project contains the Ajuna app (https://ajuna.io/) for Ledger Nano S and X.

- Ledger Nano S/X BOLOS app
- Specs / Documentation
- C++ unit tests
- Zemu tests

For more information: [How to build](docs/build.md)

## ATTENTION

Please:

- **Do not use in production**
- **Do not use a Ledger device with funds for development purposes.**
- **Have a separate and marked device that is used ONLY for development and testing**
# Ajuna 1.1.x

## System

| Name                    | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments                         |
| ----------------------- | ------ | --------- | --------- | ------- | --------------------------------- |
| Fill block              |        |           |           |         | `Perbill`ratio<br/>               |
| Remark                  |        |           |           |         | `Vecu8`remark<br/>                |
| Set heap pages          |        |           |           |         | `u64`pages<br/>                   |
| Set code                |        |           |           |         | `Vecu8`code<br/>                  |
| Set code without checks |        |           |           |         | `Vecu8`code<br/>                  |
| Set storage             |        |           |           |         | `VecKeyValue`items<br/>           |
| Kill storage            |        |           |           |         | `VecKey`keys<br/>                 |
| Kill prefix             |        |           |           |         | `Key`prefix<br/>`u32`subkeys<br/> |
| Remark with event       |        |           |           |         | `Vecu8`remark<br/>                |

## ParachainSystem

| Name                     | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments                        |
| ------------------------ | ------ | --------- | --------- | ------- | -------------------------------- |
| Set validation data      |        |           |           |         | `ParachainInherentData`data<br/> |
| Sudo send upward message |        |           |           |         | `UpwardMessage`message<br/>      |
| Authorize upgrade        |        |           |           |         | `Hash`code_hash<br/>             |
| Enact authorized upgrade |        |           |           |         | `Vecu8`code<br/>                 |

## Timestamp

| Name | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments            |
| ---- | ------ | --------- | --------- | ------- | -------------------- |
| Set  |        |           |           |         | `Compactu64`now<br/> |

## Balances

| Name                | Nano S             | Nano S XL          | Nano SP/X          | Nesting            | Arguments                                                                                               |
| ------------------- | ------------------ | ------------------ | ------------------ | ------------------ | ------------------------------------------------------------------------------------------------------- |
| Transfer            | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | `LookupasStaticLookupSource`dest<br/>`CompactBalance`amount<br/>                                        |
| Set balance         |                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | `LookupasStaticLookupSource`who<br/>`CompactBalance`new_free<br/>`CompactBalance`new_reserved<br/>      |
| Force transfer      | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | `LookupasStaticLookupSource`source<br/>`LookupasStaticLookupSource`dest<br/>`CompactBalance`amount<br/> |
| Transfer keep alive | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | `LookupasStaticLookupSource`dest<br/>`CompactBalance`amount<br/>                                        |
| Transfer all        | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    | `LookupasStaticLookupSource`dest<br/>`bool`keep_alive<br/>                                              |
| Force unreserve     |                    | :heavy_check_mark: | :heavy_check_mark: |                    | `LookupasStaticLookupSource`who<br/>`Balance`amount<br/>                                                |

## Vesting

| Name                     | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments                                                                        |
| ------------------------ | ------ | --------- | --------- | ------- | -------------------------------------------------------------------------------- |
| Claim                    |        |           |           |         |                                                                                  |
| Vested transfer          |        |           |           |         | `LookupasStaticLookupSource`dest<br/>`VestingScheduleOf`schedule<br/>            |
| Update vesting schedules |        |           |           |         | `LookupasStaticLookupSource`who<br/>`VecVestingScheduleOf`vesting_schedules<br/> |
| Claim for                |        |           |           |         | `LookupasStaticLookupSource`dest<br/>                                            |

## Authorship

| Name       | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments                  |
| ---------- | ------ | --------- | --------- | ------- | -------------------------- |
| Set uncles |        |           |           |         | `VecHeader`new_uncles<br/> |

## CollatorSelection

| Name                   | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments                |
| ---------------------- | ------ | --------- | --------- | ------- | ------------------------ |
| Set invulnerables      |        |           |           |         | `VecAccountId`new\_<br/> |
| Set desired candidates |        |           |           |         | `u32`max<br/>            |
| Set candidacy bond     |        |           |           |         | `Balance`bond<br/>       |
| Register as candidate  |        |           |           |         |                          |
| Leave intent           |        |           |           |         |                          |

## Session

| Name       | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments                        |
| ---------- | ------ | --------- | --------- | ------- | -------------------------------- |
| Set keys   |        |           |           |         | `Keys`keys<br/>`Bytes`proof<br/> |
| Purge keys |        |           |           |         |                                  |

## XcmpQueue

| Name                              | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments                                            |
| --------------------------------- | ------ | --------- | --------- | ------- | ---------------------------------------------------- |
| Service overweight                |        |           |           |         | `OverweightIndex`index<br/>`Weight`weight_limit<br/> |
| Suspend xcm execution             |        |           |           |         |                                                      |
| Resume xcm execution              |        |           |           |         |                                                      |
| Update suspend threshold          |        |           |           |         | `u32`new\_<br/>                                      |
| Update drop threshold             |        |           |           |         | `u32`new\_<br/>                                      |
| Update resume threshold           |        |           |           |         | `u32`new\_<br/>                                      |
| Update threshold weight           |        |           |           |         | `Weight`new\_<br/>                                   |
| Update weight restrict decay      |        |           |           |         | `Weight`new\_<br/>                                   |
| Update xcmp max individual weight |        |           |           |         | `Weight`new\_<br/>                                   |

## PolkadotXcm

| Name                             | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments                                                                                                                                                                 |
| -------------------------------- | ------ | --------- | --------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Send                             |        |           |           |         | `BoxVersionedMultiLocation`dest<br/>`BoxVersionedXcmTuple`message<br/>                                                                                                    |
| Teleport assets                  |        |           |           |         | `BoxVersionedMultiLocation`dest<br/>`BoxVersionedMultiLocation`beneficiary<br/>`BoxVersionedMultiAssets`assets<br/>`u32`fee_asset_item<br/>                               |
| Reserve transfer assets          |        |           |           |         | `BoxVersionedMultiLocation`dest<br/>`BoxVersionedMultiLocation`beneficiary<br/>`BoxVersionedMultiAssets`assets<br/>`u32`fee_asset_item<br/>                               |
| Execute                          |        |           |           |         | `BoxVersionedXcmTasSysConfigCall`message<br/>`Weight`max_weight<br/>                                                                                                      |
| Force xcm version                |        |           |           |         | `BoxMultiLocation`location<br/>`XcmVersion`xcm_version<br/>                                                                                                               |
| Force default xcm version        |        |           |           |         | `OptionXcmVersion`maybe_xcm_version<br/>                                                                                                                                  |
| Force subscribe version notify   |        |           |           |         | `BoxVersionedMultiLocation`location<br/>                                                                                                                                  |
| Force unsubscribe version notify |        |           |           |         | `BoxVersionedMultiLocation`location<br/>                                                                                                                                  |
| Limited reserve transfer assets  |        |           |           |         | `BoxVersionedMultiLocation`dest<br/>`BoxVersionedMultiLocation`beneficiary<br/>`BoxVersionedMultiAssets`assets<br/>`u32`fee_asset_item<br/>`WeightLimit`weight_limit<br/> |
| Limited teleport assets          |        |           |           |         | `BoxVersionedMultiLocation`dest<br/>`BoxVersionedMultiLocation`beneficiary<br/>`BoxVersionedMultiAssets`assets<br/>`u32`fee_asset_item<br/>`WeightLimit`weight_limit<br/> |

## DmpQueue

| Name               | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments                                            |
| ------------------ | ------ | --------- | --------- | ------- | ---------------------------------------------------- |
| Service overweight |        |           |           |         | `OverweightIndex`index<br/>`Weight`weight_limit<br/> |

## Sudo

| Name                  | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments                                           |
| --------------------- | ------ | --------- | --------- | ------- | --------------------------------------------------- |
| Sudo                  |        |           |           |         | `Call`call<br/>                                     |
| Sudo unchecked weight |        |           |           |         | `Call`call<br/>`Weight`weight<br/>                  |
| Set key               |        |           |           |         | `LookupasStaticLookupSource`new\_<br/>              |
| Sudo as               |        |           |           |         | `LookupasStaticLookupSource`who<br/>`Call`call<br/> |

## Treasury

| Name             | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments                                                               |
| ---------------- | ------ | --------- | --------- | ------- | ----------------------------------------------------------------------- |
| Propose spend    |        |           |           |         | `CompactBalance`amount<br/>`LookupasStaticLookupSource`beneficiary<br/> |
| Reject proposal  |        |           |           |         | `Compactu32`proposal_id<br/>                                            |
| Approve proposal |        |           |           |         | `Compactu32`proposal_id<br/>                                            |

## Council

| Name                | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments                                                                                                         |
| ------------------- | ------ | --------- | --------- | ------- | ----------------------------------------------------------------------------------------------------------------- |
| Set members         |        |           |           |         | `VecAccountId`new_members<br/>`OptionAccountId`prime<br/>`MemberCount`old_count<br/>                              |
| Execute             |        |           |           |         | `Proposal`proposal<br/>`Compactu32`length_bound<br/>                                                              |
| Propose             |        |           |           |         | `Compactu32`threshold<br/>`Proposal`proposal<br/>`Compactu32`length_bound<br/>                                    |
| Vote                |        |           |           |         | `Hash`proposal<br/>`Compactu32`index<br/>`bool`approve<br/>                                                       |
| Close               |        |           |           |         | `Hash`proposal_hash<br/>`Compactu32`index<br/>`Compactu64`proposal_weight_bound<br/>`Compactu32`length_bound<br/> |
| Disapprove proposal |        |           |           |         | `Hash`proposal_hash<br/>                                                                                          |

## CouncilMembership

| Name          | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments                                 |
| ------------- | ------ | --------- | --------- | ------- | ----------------------------------------- |
| Add member    |        |           |           |         | `AccountId`who<br/>                       |
| Remove member |        |           |           |         | `AccountId`who<br/>                       |
| Swap member   |        |           |           |         | `AccountId`remove<br/>`AccountId`add<br/> |
| Reset members |        |           |           |         | `VecAccountId`members<br/>                |
| Change key    |        |           |           |         | `AccountId`new\_<br/>                     |
| Set prime     |        |           |           |         | `AccountId`who<br/>                       |
| Clear prime   |        |           |           |         |                                           |
