# Semester Project TP4: The beta spectrometer
Git repository with the Geant4 program used in my Semester Project of Master at École polytechnique fédérale de Lausanne.

The program is a simualator of a beta spectrometer written in C++ and using Geant4. To run the program, it is necessary to have Geant4 installed (https://geant4-forum.web.cern.ch/) and the BxDecay0 library with extension to Geant4 to use the soruce generator (https://github.com/BxCppDev/bxdecay0). This library includes an option to generate the primary particles in a solid angle desired instead of in a isotropic emission in the unit circunference. 

----First program: Simulation with BxDecay Generator----

Put the file "SB_sim_BxDecay.tar.gz" where you want it. Unwrap it: 
tar -xzvf SB_sim_BxDecay.tar.xz

The tarball contains three folders:
-SB_sim_min (this contains the actual files with the simulation)
-SB_sim_REQ (this contains a bunch of additional files that the simulation will need)
-SB_sim_run_maker (this contains a little piece of code you can use to generate script for doing an energy scan in the simulation) 

Go into the folder created:
cd SB_sim_BxDecay

Make a new folder: 
mkdir SB_sim_BxDecay_build

Go into that folder, and copy the additional required files: 
cd SB_sim_BxDecay_build
cp -r ../SB_sim_REQ/* .

Tell CMake to prepare for building the source:
cmake -DBxDecay0_DIR=.. -DGeant4_DIR=..  .../SB_sim_BxDecay/SB_sim_min

Then actually do the building
make

If all of this completes correctly, it will generate an executable named exampleN02. You can run it: 
./exampleN02
In this way, the file used to do the run is vis.mac, where there are some commands for the visualization, the source to use, the position of the source and the MDL action of the BxDecay generator (read here https://github.com/BxCppDev/bxdecay0/tree/develop/documentation/PostGenEventOps/MDL)

This will generate an interactive GUI which you can issue commands. You can also run it in batch mode (no gui, just simulation): 
./exampleN02 run1.mac

Then, all the commands explained before are in run1.mac

In this version, the magnetic map obtained from a simulation is used.


---Second version: Simulation with standard Geant4 generator but adapeted to do a scan in energy + magnetic field applied + solid angle of emission ---

Same steps but using : SB_sim_monoenergetic.tar.xz

Now the files required and copied from SB_sim_REQ are:

test.txt-- It chooses kinetic energy for the magneic field reference value, $B_0$.

primary_angles.txt -- The angles for the emission of the particles

primary_E.txt -- It sets the kinetic energy of the monoenergetic beam to produce. By default they are electrons.


