# SPOUT · example data

One example recording session per system, as written by **SPOUT**, part of the
[spout-task](https://github.com/spout-task) project. Use these to test the scripts in the [analyses](https://github.com/spout-task/analyses) repository. The SPOUT1 example is a Pavlovian conditioning session; the SPOUT2 example is an uninstructed lick left, lick right (LL/LR) session.

Both sessions were recorded with an earlier firmware version, so a few parameter names in `*_Settings.csv` differ from the current GUI (for example `MinENL` instead of `MinITI`). The analysis scripts read both versions.

```
SPOUT1/  SPOUT1_example_session/  (+ SPOUT1_example_session.jpg)
SPOUT2/  SPOUT2_example_session/  (+ SPOUT2_example_session.jpg)
```

## File schema
Each session writes a set of UTF-8 CSV files, prefixed with the session name. Times are in
milliseconds on the Teensy clock.

| File | Columns | Meaning |
|---|---|---|
| `*_Settings.csv` | `parameter,value` (no header) | Full task configuration. The first rows hold session information (start time, how the session was stopped, end time); the rest has the same format as a predefined settings file. |
| `*_Events.csv` | `nTrial, iBlock, iTrial, iRewardCount, event, eventTime, duration` | Per-event log (licks, rewards, state changes). |
| `*_Blocks.csv` (SPOUT1) | `nBlock, iTrial, blockLength, nTrials, nCorrect, nIncorrect, nRewards, nNoRewards, nENLPenalties, nOmissions, nFreeRewards, nLicks, nBadTrialsPostReward, nTrialsToSwitch` | Per-block summary. |
| `*_Blocks.csv` (SPOUT2) | `nBlock, iSpout, blockLength, nTrials, nCorrect, nIncorrect, nRewards, nNoRewards, nENLPenalties, nOmissions, nFreeRewards, nLeftLicks, nRightLicks, nWinRepeat, nLoseSwitch, nWinSwitch, nLoseRepeat, nBadTrialsPostReward, nTrialsToSwitch` | Per-block summary. |
| `*_SyncPulses.csv` | `status, time, duration` | Internal sync pulses (`Sync_on`/`Sync_off`). |
| `*_ExtSyncPulses.csv` | `status, time, duration` | External-system sync (empty if none). |

The `.jpg` next to each session is the daily session plot made with the `plot_*_daily_session.m` script in the [analyses](https://github.com/spout-task/analyses) repository.

## License
**CC-BY-4.0** ([`LICENSE`](LICENSE)). See also [`CITATION.cff`](CITATION.cff).
