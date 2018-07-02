---
eip: <to be assigned>
title: Gas Estimation adjustments
author: alan@gnosis.pm, denis@gnosis.pm, uxio@gnosis.pm
discussions-to: alan@gnosis.pm
status: Draft
type: Standards Track
category: Core
created: 2018-07-02
---

## Simple Summary
This EIP improves the gas estimation of contract calls

## Abstract
Gas estimation is not very accurate. Gas spent in inner calls is not taken into account. At the end, gas used is retrieved, but sometimes more gas
is needed too because some storage was freed and gas was recovered at the end of the execution.

This EIP proposes

## Motivation
Gas estimation is a very important issue when developing dapps, and it will be convenient to have a more deterministic way to calculate it. Right now
the only way to do it is estimate and then add some gas more just in case.

## Specification
Gas for calling inner calls must be taken into account

Total gas used should be retrieved before releasing. For example, a field `totalGasUsed`

## Rationale
There must be a way to calculate gas usage in a deterministic way.

## Backwards Compatibility
It should be backwards compatible with every application. Existing apps must stop adding more gas and just use gas retrieved from the gas estimation of
the node.

## Test Cases
- Call to a contract which does calls to another contract (CALL and DELEGATECALL)
- Call to a contract that releases storage

## Implementation

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
