# Policy Consistent update;

## Background:
* Network exist in a constant state of flux:
  - Operators frequently modify routing tables, adjust link weights, and change access control lists to perform tasks from planned maintenance, to traffic engineering, to patching security vulnerabilities, to migrating virtual machines in a datacenter.
* configuration changes lead to instability in networks;
  - outages, performance disruptions, and security
vulnerabilities;
* Good initial and final configurations, but no guarantee on the update process -- itself often steps through intermediate configurations that exhibit incorrect behaviors.

so we need to: preserve well-defined behaviors when transitioning between configurations.

## Contents:
Then, how to guarantee policy update consistency?

* Update all the switches in the network simultaneously. 'atomic update'; -- packets in flight when the update happens will suffer from configuration mixture.
* To guarantee that every packet traversing the network is processed by exactly one consistent global network configuration.
(When a network update occurs, this guarantee persists: each packet is processed either using the configuration in place prior to the update, or the configuration in place after the update, but never a mixture of the two.)

(By extending the second method, we can define two levels of consistency:)
### Define the problem:
* consistency level:
  - per-packet: every single packets is processed with the same configuration.
  - per-flow; all packets in the same flow are processed with the same configuration.
