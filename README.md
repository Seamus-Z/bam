# Feetech HLS2915 BAM raw logs

16 unprocessed trajectory recordings (4 trajectories × kp 2, 3, 4, 6)
used to identify `bam/params/feetech_hls`.

Download: [feetech_hls_raw.zip](./feetech_hls_raw.zip)

Then:

```
python3 -m bam.process --raw path/to/extracted --logdir proc --dt 0.005
python3 -m bam.fit --logdir proc --actuator feetech_hls --model m1 \
  --validation_kp 4 --trials 3000 --workers 1 --output m1.json
```
