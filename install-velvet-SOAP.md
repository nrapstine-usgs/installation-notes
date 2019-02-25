## Velvet

On Yeti, navigate to the directory where you want to build the software. For example, do the following in your home directory.

Download the repository from GitHub: [https://github.com/dzerbino/velvet](https://github.com/dzerbino/velvet): 

```bash
git clone https://github.com/dzerbino/velvet.git
cd velvet
make
./velveth
./velvetg
```

Now, the executable is available in this directory. Again, I installed it in your home, the path to the executables will be `/home/kbockrath/velvet/velveth` and `/home/kbockrath/velvet/velvetg`



## SOAP

On Yeti, navigate to the directory where you want to build the software.

We will download the repository from GitHub: [https://github.com/aquaskyline/SOAPdenovo2](https://github.com/aquaskyline/SOAPdenovo2): 

```bash
git clone https://github.com/aquaskyline/SOAPdenovo2.git
cd SOAPdenovo2
make
```

Now, `./SOAPdenovo-63mer`, `./SOAPdenovo-127mer` and `./SOAPdenovo-fusion` are available.



#### Slurm script

The slurm script should look similar:

```shell
#!/bin/sh

#SBATCH --account=mwf
#SBATCH -p UV
#SBATCH --time=00:10:00        # note, this requests only 10 min
#SBATCH --job-name=velvet
#SBATCH -o velvet.out
#SBATCH -n 1
#SBATCH -c 16                  # how many cores to use
#SBATCH -N 1
#SBATCH --mail-type=ALL
#SBATCH --mail-user=katherine_bockrath@fws.gov

export VELVET_HOME=~/velvet

# Run Velvet 
srun $VELVET_HOME/velveth [other velvet flags here]

```



