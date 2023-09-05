# Morsera: A Dead Man's Switch for Safe

This is the main Morsera repository, it contains submodules for contracts, frontend, and docs.

## Morsera Overview

Morsera allows Safes to configure arbitrary transactions that become executable at a given time in the future.
The trigger can be defined by a specific timestamp or by an inactivity delay. 

### Why would someone want this?

In the event of key loss, a solid contingency plan is invaluable.

* Individuals may opt to use a stronger signing threshold than 1/1 (such as 2/2 or 2/3) to bolster security. However, since this scheme may increase the likelihood of losing access, a fallback to a 1/1 or 2/n in case of key loss could be helpful. 
* If an individual wishes to leave their assets to loved ones after they pass, transitioning to a 1/1 scheme or sweeping assets to another address that their family controls would make recovery much smoother.
* If one wants to set up [social recovery](https://vitalik.ca/general/2021/01/11/recovery.html) for their Safe, they can use Morsera to add some guardians to their Safe after some inactivity period. 
* DAOs and institutions that use multisigs to safeguard their assets can benefit from an arbitrary fallback strategy in the unlikely event they lose their keys.

### How does it work?

To set up Morsera, a Safe deploys and adds a single contract (`DeadManSwitch`) as both a module and guard. Being a module allows the contract to execute transactions on the Safe's behalf, and being a guard allows the contract to keep track of the Safe's last tx timestamp.

The Safe can then tell the `DeadManSwitch` to set up arbitrary delayed transactions.

## Implementation Status (WIP)

Morsera is a work in progress, the UI is incomplete and the contracts have not been audited.

