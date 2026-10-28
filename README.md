Pre-reqs

* Does everyone have zscaler installed? [installation instructions](https://www.imperial.ac.uk/admin-services/ict/self-service/connect-communicate/remote-access/unified-access/)
* Can everyone see [wodin-dev](https://wodin-dev.dide.ic.ac.uk)? You are good to go!


Why cluster?

* Personal devices not powerful enough - throughput
* Don't have to keep your laptop on all the time


What is a cluster?

* Manager that holds a queue of jobs with workers
* Workers run code for you


Docs for cluster are [here](https://github.com/reside-ic/cluster-docs)


Let's talk about the architecture

* see [diagram](https://mermaid.live/view#pako:eNqNlGFr2zAQhv-K0KcWYtduHDs1Y7A1WymsZZD2ywgEVb5aoraUSfLSLPS_7-QkjROnMH2x76z39aM7SWvKdQE0p8-VXnLBjCMPX2eK4LDNU2nYQpBHC4bcMS6kgs2n9rMVmwBUMVNHktvrB_KFO_kHyEQa4E6b1V46uZ18m3MDBSgnWWU_9rkHt9TmhXyXFZDpyjqo-yRO8hdwcy4An6ZDuHOZ4u9Z2VH4IXQN86IP12J8xDOjP3QpFbnHopGz5UKyoHoV6nxG9wYlsmyQ9rknZsXcgamlYtUJwmutnNFV1cX343cDzRH3drUWqeG_qW9-PrbMXc6VbkwPtE1yXdfsyHBraQUJgjhsW0gWzFpsTxEEn3ur3scouDwhOL0JjrMoHobkoTXyqhOFPEiRT0GQ7ATkTAEUljhNeEGkwqfvOnnv-rm3PLV9Dj2DYBQSaxp1YZ-Y48KrOp05MXm78rZJRecnna51MyhKQ3KDCl__nRpb8AG3d-y1ryU6ctp2srVCfiLdu_Sgyd2ML2EWkinDw1vp0l4YsE3lLIIcYZCldGJL26-k9924Hx41708WRjsMoSB9IR3QGqvJZIH30tpbzKgTUOPuzfEVK9q8BgUzLwHXlTZ-T7-hhjVOT1eK09yZBgbU6KYUNH_GXYRRsyiYg4lkeCTq3ZQFU7-0fg-hkAh4t7kQ23uxnULzNX2leTrKwiRNo6soGqdpNhzQFc3j6DJMxsPs8ipOoyyNktHbgP5tPaNwHGdJPBplaZzE4zi6GtDS-EVtkQweLTDXulGO5sMkfvsH_hTHag)
* important to know what machine your code is running on
* tickets are your access into your home directory, explain what tickets are


Demo time - refer to architecture diagram during this

* `ssh hpc1@wpia-lxhn.hpc.dide.ic.ac.uk` with password in the teams chat
* `hostname` to see name of machine
* `klist` to see your ticket - explain different dates
* `mkdir <some-unique-string>` and then `cd <some-unique-string>`
* `pwd` to check you are in there
* I will do `squeue` and show the jobs running
* `srun hostname` - thats different to just `hostname` earlier, your command ran on another machine
* how to target machines? try `srun --nodelist=gpu1 hostname` - we only get gpu1
* issue with `srun`? It is attached to your terminal, if you leave, it exits the job, try `srun sleep 10`
* `sbatch` does jobs in background, but we need to give it a script to run, I have some example scripts `git clone https://github.com/reside-ic/slurm-cluster-training.git`
* what is in this repo? `cd <folder>` then `ls` and then `cat <script>`
* `sbatch sleep-script` check to see your job id is on `squeue`
* we get a file? delete it for now, its empty `rm <file>`
* `echo hello` prints hello, try it
* `srun echo hello` prints hello but on another machine and you get the output to your terminal
* where does output from `sbatch hello-script` go? That file from earlier! `cat <file>`


If extra time
* 2TB user limit and 7 day time limit on jobs so checkpointing is recommended
* CPU only jobs require `--partition=cpu` flag
* etiquette about not saturating or fragmenting the cluster
* explain ticket renewal with `auks -g` to get ticket and `auks -a` to add new ticket
