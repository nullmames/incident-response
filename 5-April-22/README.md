# Chain Halt

Chain halted at approximately ~4:30 AM PST while processing block 2578098. The network is still in voting rounds currently.

- [x] Human Readable list of transactions in 2578097
- [x] List of all contracts called in 2578097
- [ ] Human Readable list of transactions in 2578098
- [ ] List of all contracts called in 2578098

### UPDATE 9 AM PST 6 April 2022

Root cause has been identified. Two paths are being explored. One path is to restart network with current data folders on top of a new version. The other path is an export and height increment and restart network with same chain-id. The below list is for restarting from export.

#### Tasks 
- [ ] Verify that 3 exports from block 97 only differ by the hash generated by the malicous contract (@faddat and team)
- [ ] Verify state changes between v2.1.0 and v3.0.0 (nee v2.3.2) and make list that would need to happen to genesis file (@faddat and team)
- [ ] Write a `junod migrate` command that takes the JSON from the export and makes modifications to it according to list of changes needed (@faddat and team, but likely need more hands and eyes on this work)
    * [ ] Increment `.initial_height` in the export to be 99
    * [ ] Remove lupercalia upgrade proposal and votes from state
    * [ ] additional TBD modifications
- [ ] Test upgrade using ibc test framework to impersonate the top 29 validators (@agouin and @jackzampolin)
    * [ ] Make list of their valoper keys 
    * [ ] Generate the new validator set
    * [ ] Find and replace all instances of one validator's key with the new validator's key
    * [ ] start the network and ensure that it runs smoothly
    * [ ] TBD testing to ensure validatity of ugprade
- [ ] Hardfork planning (needs resourcing)
    * [ ] Plan timing of network restart
    * [ ] Notify validators
    * [ ] Write instructions for upgrade
