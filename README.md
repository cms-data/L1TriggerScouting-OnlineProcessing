# L1TriggerScouting-OnlineProcessing

This repository contains files used by the plugins in `L1TriggerScouting/OnlineProcessing` (Level-1 Scouting).

 - File: `JEC_AK4CaloTowerL1S_Run3Winter25_v2.txt`
   - Jet-energy-scale corrections corresponding to option "C" shown in
     [these slides](https://indico.cern.ch/event/1664868/contributions/7000276/attachments/3240001/5778821/260317_l1sRun3_caloTowerJECs.pdf)
     (method suggested by Giovanni Petrucciani).
   - Derived using MC samples from the Run3Winter25 campaign, and conditions from 2025 data-taking
     (more info [here](https://indico.cern.ch/event/1658920/contributions/6972516/attachments/3230391/5758319/260303_l1sRun3_caloTowerJECs.pdf#page=9)).
   - Input jets: AK4 "CaloJets" (jets created by clustering CaloTowers using the anti-kt algorithm with R=0.4).
   - Structure of the file.
     - Every row corresponds to a different JEC category/bin based on jet transverse momentum ($p_{T}$),
       jet pseudo-rapidity ($\eta$), and a PU proxy (number of CaloTowers with `hwPt > 0` and `abs(hwEta) <= 4`).
     - Every column corresponds to a different quantity (see next bullet).
   - Meaning of the columns (from left to right).
     - [1] Min uncorrected jet $p_{T}$ of this JEC category.
     - [2] Max uncorrected jet $p_{T}$ of this JEC category.
     - [3] Min jet $\eta$ of this JEC category.
     - [4] Max jet $\eta$ of this JEC category.
     - [5] Min value of PU proxy of this JEC category (ignored if negative).
     - [6] Max value of PU proxy of this JEC category (ignored if negative).
     - [7] Analytic function to determine the corrected jet $p_{T}$ for this JEC category.
     - [8] Number of parameters in the function in column-7.
     - [9-*] Values of the function's parameters for this JEC category.
   - _Note_ : the function in column-7 returns the corrected jet $p_{T}$ (not the JEC factor);
     the JEC factor can be obtained by dividing the corrected $p_{T}$ by the uncorrected one.
   - Software to read these corrections in CMSSW originally included in
     the `L1ScoutingCaloJetProducer` plugin (see https://github.com/cms-sw/cmssw/pull/50785).
