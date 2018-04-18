# ssd_simulation
Empirical results and the parameter files used to obtain them, should anyone wish to replicate the results. An Excel spreadsheet of results / graphs / tables is also provided. Our project (for those who haven't seen the paper/presentation) centered around modeling SSD behavior under various workloads and configurations. This was a term project for an Advanced Operating Systems class in the CS Graduate Program at Florida State University, Spring 2018. 


First and foremost, my team and I are indebted to Kamil Jakubovič (@jakubkam on GitLabFIT), though he likely doesn't know it. We had a lot of trouble porting DiskSim 4.0 to 64-bit Ubuntu and patching to include the SSD Extension developed by Microsoft Research. Kamil has an excellent solution to this mysterious problem, which can be found at the following URL:

https://gitlab.fit.cvut.cz/jakubkam/disksim

We highly recommend Kamil's solution to anyone having trouble installing DiskSim 4.0 with the SSD extension on 64-bit machines.

Currently (as of 18 April 2018), this repository contains three categories of information. First, inside the folder named "/parvs" can be found the various parameter files which we used for our project. Second, inside the folder named "/results" you will find the output files from testing. These output files are ascii-text format, though they do not have a filename extension. Finally, there is an Excel spreadsheet that systematically categorizes the output data. Much more data has been collected than has been used; in fact, this is only a small fraction of what *should* be collected in order to develop a more complete picture of the behavior of an idealized SSD under any workload. Future work will attempt to fill in these gaps in empirical knowledge.

The naming convention for parameter files and output files is detailed in tables that may be found inside the Excel file, on the individual sheet named "Tables". The fundamentals are as follows:

There are three classes of testing: A, B, and C. A is a single SSD. B represents a RAID 3 configuration. C is a RAID 5 configuration of 3 disks, one of which is only a parity disk.

There are five differing workloads: balanced r/w with a 50% chance of sequentialization, sequential read, sequential write, random read, and random write. These are numbered 1 through 5, respectively. All workloads (with the exception of the balanced load) follow a 70/30 rule. For example, the random read load has a 70% chance of the IO request being a random read; otherwise, the IO request follow a balanced yet random pattern.

A quick side note: project testing was done in two rounds. In Round 1, for all workloads and configurations we assigned a 15% chance that the generated IO request would be time-critical. In Round 2, this chance was changed to 100% for all configurations and workloads. 100% is the default value for RAID configurations. A time-critical IO request is a request which must be completed before the next request can begin to be serviced. This effectively serializes IO on a FIFO basis.

If/when additional information is added to this repository, the README will be updated accordingly in edits that will appear below this point.

