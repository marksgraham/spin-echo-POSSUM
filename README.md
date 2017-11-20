This code extends [POSSUM](https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/POSSUM) to enable the simulation of spin-echo pulse sequences. 

## Changes from FSL 5.0.10

# pulse.cc

* Two new functions: spinecho and spinechoepi, adding spin-echo pulses to gradient-echo and epi sequences, respectively.
* New pulse types can be called from the command line using --seq se or --seq se-epi

# possum.cc

* When reading in the MR parameters (MRpar) a fifth column with T2 values is now expected. I've also slightly updated the T2* values to bring them in line with values from the literature. If a four-column MRpar file is supplied, the program will assume T2=T2\*.

Old 3T MRpar:

T1 | T2* |PD | Shift
--- | --- | --- | ---
1331e-03 | 75e-03 | 0.86 |0 
832e-03  |70e-03   |0.77 |0 
3700e-03 |500e-03 |1 |0 

New 3T MRpar:

T1 | T2* |PD | Shift | T2
--- | --- | --- | --- | ---
1331e-03 | 51e-03 | 0.86 |0 | 75e-03
832e-03  |44e-03   |0.77 |0 | 70e-03
3700e-03 |500e-03 |1 |0 | 500e-03

# signal2image.cc 

Support for reconstructing the new pulse types (se and se-epi) that can be generated using pulse

# possumfns.cc 

Implemented support for 180 RF pulses in the simulation.

