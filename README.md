# TriggerPaths

This repo is designed to hold info about HLT trigger paths used in 201[678] (basically a massive python config dump).

It should be especially useful for finding the last module in a HLT path e.g. to match to trigger objects.

It was designed to overcome the slowness of [ConfDB](https://cmsweb.cern.ch/confdb/).

## Howto

e.g.

```hltGetConfiguration /online/collisions/2016/25ns15e33/v4.1/HLT/V11 --data --process DUMMY --full --offline --path HLTriggerFirstPath,HLT_Photon175_v*,HLTriggerFinalPath,HLTAnalyzerEndpath --globaltag 80X_dataRun2_2016SeptRepro_v7 --max-events 100 --unprescale --output none >& hlt_original.py```

