# TriggerPaths

This repo is designed to hold info about HLT trigger paths used in 201[678] (basically a massive python config dump of the HLT config).
It should be especially useful for finding the last module in a HLT path e.g. to match to trigger objects. It also lists all triggers in each dataset (e.g. `SingleMuon`).

There is one file per year.

It was designed to circumvent the slowness of [ConfDB](https://cmsweb.cern.ch/confdb/).

Please feel free to contirbute more if they're missing. For now, I'm only doing pp runs.

Note that I'm not doing *every* trigger menu used during the Runs - I don't care about prescales, only paths, which should be the same throughout running.
So using the last trigger in the year should hopefully encapsulate every trigger used that year.

**Caveat**: In theory one could use these configs to re-run the trigger. However I cannot guarantee they are _exactly_ setup as used in data taking.

## Howto

Use the `hltGetConfiguration` tool, e.g.

```hltGetConfiguration /online/collisions/2016/25ns15e33/v4.2/HLT/V8  --data --process DUMMY --full --offline --path HLTriggerFirstPath,HLT_*,HLTriggerFinalPath,HLTAnalyzerEndpath --globaltag 80X_dataRun2_Prompt_v9 --max-events 100 --unprescale --output none >& hlt_2016_v4.2_V8.py```

All configs were made in CMSSW_10_2_5 (shouldn't affect things). Exact commands are at the top of each config file.
Note that the GlobalTag makes no difference to the HLT config, it just sets it in the config file if you wanted to run it later on.

~One can also use `run:runnumber` instead of the trigger menu name.~ That option doesn't work.

~If one wishes to use the menu used during a specific run, one should look up the run in WBM Run Summary (https://cmswbm.cern.ch/cmsdb/servlet/RunSummary), get the trigger menu name from there, and use it in the command instead.~ The database can't connect to e.g. `/cdaq/physics/Run2016/25ns10e33/v2.1.3/HLT/V1`

You can **only** use trigger menus of the from `/online/collisions/` it seems. So you have to try and translate between the one used during runninng (e.g. `/cdaq/physics/Run2016/25ns10e33/v2.1.3/HLT/V1`) and the one you can actually access from `/online/collisions/`.

One can also specify a specific trigger, e.g. `HLT_Photon_*`, instead of all triggers (`HLT_*` in the above command).


## Future features

- Export separate list of HLT name : last filter ?
- Export separate list of just all HLT triggers (divided by dataset?)

## Links

- https://twiki.cern.ch/twiki/bin/view/CMSPublic/SWGuideGlobalHLT
- https://twiki.cern.ch/twiki/bin/view/CMSPublic/SWGuideHltGetConfiguration (old)
