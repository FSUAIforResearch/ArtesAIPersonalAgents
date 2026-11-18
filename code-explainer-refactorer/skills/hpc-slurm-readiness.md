---
name: hpc-slurm-cluster-readiness
description: Converts a desktop script into a headless CLI script (argparse, seed control, non-interactive plots) and generates an FSU RCC SLURM sbatch job script. Use when the user types /hpc-ready or asks to run code on FSU RCC, an HPC cluster, or SLURM.
---

# HPC & SLURM Cluster Readiness (`/hpc-ready` — FSU Research Computing Center)

## When to Apply This Skill
Trigger this skill when the user types `/hpc-ready` or asks to adapt a laptop/desktop script to run on Florida State University's **Research Computing Center (RCC)** HPC cluster (`rcc.fsu.edu`) or another SLURM scheduler.

## FSU Research Computing Center (RCC) SLURM Guidelines (`rcc.fsu.edu`)
When generating SLURM scripts and cluster instructions for FSU researchers, apply these FSU RCC conventions:
1. **FSU RCC Accounts / Queues / Partitions (`#SBATCH -A` or `#SBATCH -p`)**:
   At FSU RCC, accounts, queues, and partitions are specified with `#SBATCH -A <queue>` (users can check their authorized queues with `rcctool my:partitions`):
   - **`genacc_q`** *(General Access Queue — Default)*: Up to **14 days** max runtime (`-t 14-00:00:00`), default `3.9G` memory per CPU core (`#SBATCH --mem-per-cpu=3.9G`).
   - **`backfill`** *(Short / Idle-Resource Queue)*: Up to **4 hours** max runtime (`-t 04:00:00`), default `1.9G` memory per CPU core—ideal for fast turnaround on short jobs.
   - **`backfill2`** *(Preemptible Backfill Queue)*: Up to **4 hours** max runtime with **preemption enabled** (recommend checkpointing if using `backfill2`).
   - **`quicktest`** *(Quick Testing Queue)*: Up to **10 minutes** (`-t 00:10:00`) for smoke-testing a script before launching a full run.
   - **`condor`** *(Long Non-MPI Queue)*: Up to **90 days** for long-running serial/non-MPI jobs.
   - **Lab Investor / GPU Queues**: Note where the user can substitute their PI's owner queue or add `--gres=gpu:1` if needed.
2. **FSU RCC Environment Modules & Compute Node Network Isolation**:
   - Load required software modules *inside* the `.sh` batch script (never rely on login-node environment state), e.g., `module load gnu` or `module load anaconda/2023.09`.
   - **No Default Outbound Internet on Compute Nodes**: FSU RCC compute nodes are isolated from the external internet by default. Remind users to install packages and download datasets on the login node beforehand—or add `module load webproxy` inside the batch script if the job must fetch remote data.
   - Execute binaries/scripts under SLURM resource tracking with `srun`.
3. **FSU RCC Storage & I/O Best Practices**:
   - Recommend reading/writing large datasets and simulation outputs in high-performance parallel research storage (`/gpfs/research/<your_group>/...`) rather than quota-constrained `$HOME` directories (check quotas with `rcctool my:storage`).

## Step-by-Step Instructions
1. **Refactor the Script for Headless Batch Execution**:
   - Replace hardcoded desktop file paths and magic numbers with command-line arguments (`argparse` in Python or `commandArgs(trailingOnly = TRUE)` / `optparse` in R).
   - Remove blocking interactive GUI windows (e.g., set `matplotlib.use("Agg")` before importing `pyplot` and replace `plt.show()` with `fig.savefig(..., dpi=300, bbox_inches="tight")`).
   - Vectorize slow loops where possible, add explicit random seed control (`--seed`), and print timestamped progress logs to `stdout` so progress appears in `slurm-%j.out`.
2. **Generate a Companion FSU RCC SLURM Batch Script (`submit_job.sh`)**:
   - Include FSU RCC `#SBATCH` directives (`--job-name`, `-N`, `-n` or `--cpus-per-task`, `-t`, `-A genacc_q`, `--mem-per-cpu=3.9G`, `-o`, `-e`), commenting when to switch `-A genacc_q` to `backfill` (`<= 4h`) or `quicktest` (`<= 10m`).
   - Include `module load` commands, optional `module load webproxy` note, and `srun` invocation with CLI flags.
3. **Include FSU RCC Job Management & Job Array Tips**:
   - Show the exact FSU RCC terminal commands to check partitions/storage (`rcctool my:partitions`, `rcctool my:storage`), submit (`sbatch submit_job.sh`), monitor (`squeue --me`), and cancel (`scancel <job_id>`).
   - Briefly show how to scale parameter sweeps or multi-seed runs using a **SLURM Job Array** (`#SBATCH --array=1-10` with `$SLURM_ARRAY_TASK_ID`).
