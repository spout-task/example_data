# SPOUT · example data

One example recording session per system, as written by **SPOUT** — part of the
[spout-task](https://github.com/spout-task) project. Use these to test the scripts in the [analyses](https://github.com/spout-task/analyses) repo. Example session of SPOUT1 is a Pavlovian conditioning session. Example session of SPOUT2 is a LL/LR session.

```
SPOUT1/  SPOUT1_example_session/  (+ SPOUT1_example_session.jpg)
SPOUT2/  SPOUT2_example_session/  (+ SPOUT2_example_session.jpg)
```

## File schema
Each session writes a set of UTF-8 CSV files, prefixed with the session name. Times are in
milliseconds on the Teensy clock.

| File | Columns | Meaning |
|---|---|---|
| `*_Settings.csv` | `parameter,value` (no header) | Full task configuration (same format as a predefined settings file). |
| `*_Events.csv` | `nTrial, iBlock, iTrial, iRewardCount, event, eventTime, duration` | Per-event log (licks, rewards, state changes). |
| `*_Blocks.csv` | `nBlock, iTrial, blockLength, nTrials, nCorrect, nIncorrect, nRewards, nNoRewards, nENLPenalties, nOmissions, nFreeRewards, nLicks, nBadTrialsPostReward, nTrialsToSwitch` | Per-block summary. |
| `*_SyncPulses.csv` | `status, time, duration` | Internal sync pulses (`Sync_on`/`Sync_off`). |
| `*_ExtSyncPulses.csv` | `status, time, duration` | External-system sync (empty if none). |

The `.jpg` alongside each session is a reference image of the rig/session.

## License
**CC-BY-4.0** ([`LICENSE`](LICENSE)). See also [`CITATION.cff`](CITATION.cff).
