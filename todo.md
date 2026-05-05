# Commands

## 0

```bash
wandb login
```

## 1.1

```bash
for seed in 1 2 3; do
  python cs224r/scripts/run_algo.py \
    --algo awac \
    --env_name antmaze-umaze-v0 \
    --exp_name awac_antmaze_umaze_seed${seed} \
    --seed ${seed} \
    --use_wandb \
    --which_gpu 0 \
    2>&1 | tee logs/1.1_awac_antmaze_umaze_seed${seed}.log
done
```

## 1.2

```bash
for seed in 1 2 3; do
  python cs224r/scripts/run_algo.py \
    --algo awac \
    --env_name antmaze-medium-diverse-v0 \
    --exp_name awac_antmaze_medium_diverse_seed${seed} \
    --seed ${seed} \
    --use_wandb \
    --which_gpu 0 \
    2>&1 | tee logs/1.2_awac_antmaze_medium_diverse_seed${seed}.log
done
```

## 2.1

```bash
for zeta in 0.2 0.9; do
  for seed in 1 2 3; do
    python cs224r/scripts/run_algo.py \
      --algo iql \
      --env_name antmaze-umaze-v0 \
      --iql_expectile ${zeta} \
      --exp_name iql_zeta_${zeta}_umaze_seed${seed} \
      --seed ${seed} \
      --use_wandb \
      --which_gpu 0 \
      2>&1 | tee logs/2.1_iql_zeta_${zeta}_umaze_seed${seed}.log
  done
done
```

## 2.2

```bash
export BETTER_ZETA="TODO"  # better zeta value from 2.1

for seed in 1 2 3; do
  python cs224r/scripts/run_algo.py \
    --algo iql \
    --env_name antmaze-medium-diverse-v0 \
    --iql_expectile ${BETTER_ZETA} \
    --exp_name iql_zeta_${BETTER_ZETA}_medium_diverse_seed${seed} \
    --seed ${seed} \
    --use_wandb \
    --which_gpu 0 \
    2>&1 | tee logs/2.2_iql_medium_diverse_zeta_${BETTER_ZETA}_seed${seed}.log
done
```

## 2.3

```bash
for seed in 1 2 3; do
  python cs224r/scripts/run_algo.py \
    --algo iql \
    --env_name PointmassMedium-v0 \
    --exp_name iql_zeta_${BETTER_ZETA}_stitching_seed${seed} \
    --iql_expectile ${BETTER_ZETA} \
    --offline_dataset offline_datasets/pointmass_stitching_dataset.npz \
    --seed ${seed} \
    --use_wandb \
    --which_gpu 0 \
    2>&1 | tee logs/2.3_iql_stitching_seed${seed}.log
done
```

```bash
for seed in 1 2 3; do
  python cs224r/scripts/run_algo.py \
    --algo bc \
    --env_name PointmassMedium-v0 \
    --exp_name filtered_bc_stitching_seed${seed} \
    --offline_dataset offline_datasets/pointmass_stitching_dataset.npz \
    --filter_top_percent 10 \
    --seed ${seed} \
    --use_wandb \
    --which_gpu 0 \
    2>&1 | tee logs/2.3_filtered_bc_stitching_seed${seed}.log
done
```
