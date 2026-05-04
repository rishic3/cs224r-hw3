```bash
python cs224r/scripts/run_algo.py --algo bc --env_name antmaze-umaze-v0 \
  --exp_name bc_antmaze_umaze_seed1 --seed 1 --which_gpu 0
```

```bash
python cs224r/scripts/run_algo.py --algo awac --env_name antmaze-umaze-v0 \
  --exp_name awac_antmaze_umaze_seed1 --seed 1 --which_gpu 0
```

```bash
python cs224r/scripts/run_algo.py --algo iql --env_name antmaze-umaze-v0 \
  --exp_name iql_antmaze_umaze_seed1 --seed 1 --which_gpu 0
```

```bash
python cs224r/scripts/run_algo.py --algo iql --env_name PointmassHard-v0 \
  --exp_name iql_pointmass_hard_seed1 \
  --offline_dataset offline_datasets/pointmass_stitching_dataset.npz \
  --seed 1 --which_gpu 0
```

```bash
for seed in 1 2 3; do
  python cs224r/scripts/run_algo.py --algo awac --env_name antmaze-umaze-v0 \
    --exp_name awac_antmaze_umaze_seed${seed} --seed ${seed} --which_gpu 0
done
```
