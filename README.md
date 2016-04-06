# SLURM cheat sheat

##Submit a job

Submission with sbatch:

	sbatch my_job_file.sh
	
Stop everything going into the nbi-long partition:

	unset SBATCH_PARTITION

##Info on running/pending jobs

Info in all running jobs:

	squeue
	
Just my jobs:

	squeue -u hartleym

Just one job:

	squeue -j 631978
	
When can I expect my jobs to start:

	squeue -u hartleym --start
	
Detailed information about a pending/running job:

	scontrol show jobid -dd 524552
	
##Information about completed jobs

Show detailed information about a single job:

	sacct -j 524552 --format=JobID,JobName,MaxRSS,Elapsed
	
all jobs:

	sacct --format=JobID,JobName,MaxRSS,Elapsed

## Fair shares information

Show information about the fair shares for NBI users:

	sshare -a -A nbi
	
## Sreport

Default reporting period is yesterday. Change with:

	sreport cluster AccountUtilizationByUser accounts=nbi start=1/1/16 end=3/8/16
	
Who's the biggest:

	sreport user TopUsage accounts=nbi start=1/1/16 end=3/8/16
	
See more people:

	sreport user TopUsage accounts=nbi start=1/1/16 end=3/8/16 TopCount=20
	
Better format:

	sreport user TopUsage accounts=nbi start=1/1/16 end=3/8/16 format=Login,Proper,Used
	
## Showing config info

Show information about the scheduler/priority setup:

	scontrol show config | grep SchedulerType
	scontrol show config | grep PriorityType
	
