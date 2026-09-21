# Feetech HLS2915 BAM raw logs

64 unprocessed Position-mode recordings (4 pendulum setups × 4 trajectories
× firmware Kp 4, 8, 12, 16) used to identify `bam/params/feetech_hls2915`.

The HLS ran in firmware Position mode (`mode=0`) at 12 V. BAM models it as
a `VoltageControlledActuator`. Hold-out is Kp = 4. The bundled parameters
are the joint fit of all 64 logs; **m5** is the recommended model.

| directory | length | tip mass | arm mass |
| --- | ---: | ---: | ---: |
| `l10cm_m100g/` | 0.10224 m | 0.100 kg | 0.04469 kg |
| `l10cm_m50g/` | 0.10224 m | 0.050 kg | 0.04469 kg |
| `l15cm_m100g/` | 0.15000 m | 0.100 kg | 0.06557 kg |
| `l15cm_m50g/` | 0.15000 m | 0.050 kg | 0.06557 kg |

`params/` in the zip has per-setup m1–m6 plus `joint_4conditions/` (same
JSON as `bam/params/feetech_hls2915` on `feature/feetech-hls`).

Download: [feetech_hls2915_raw.zip](./feetech_hls2915_raw.zip)

```
python3 -m bam.process --raw path/to/extracted/l10cm_m100g --logdir proc --dt 0.005
python3 -m bam.fit --logdir proc --actuator feetech_hls2915 --model m5 \
  --validation_kp 4 --trials 500 --output m5.json
```
