# Semester Project TP4: The beta spectrometer
Git repository with the Geant4 program used in my Semester Project of Master at École polytechnique fédérale de Lausanne.

The program is a simualator of a beta spectrometer written in C++ and using Geant4. To run the program, it is necessary to have Geant4 installed (https://geant4-forum.web.cern.ch/) and the BxDecay0 library with extension to Geant4 to use the soruce generator (https://github.com/BxCppDev/bxdecay0). This library includes an option to generate the primary particles in a solid angle desired instead of in a isotropic emission in the unit circunference. 

Put the file "SB_sim_new_generator.tar.gz" where you want it. Unwrap it: 
tar -xzvf SB_sim_new_generator.tar.gz

The tarball contains three folders:
-SB_sim_min (this contains the actual files with the simulation)
-SB_sim_REQ (this contains a bunch of additional files that the simulation will need)
-SB_sim_run_maker (this contains a little piece of code you can use to generate script for doing an energy scan in the simulation) 

Make a new folder: 
mkdir SB_sim_min_build

Go into that folder, and copy the additional required files: 
cd SB_sim_min_build
cp -r ../SB_sim_REQ/* .

Tell CMake to prepare for building the source:
cmake ../SB_sim_min

Then actually do the building
make

If all of this completes correctly, it will generate an executable named exampleN02. You can run it: 
./exampleN02

This will generate an interactive GUI which you can issue commands. You can also run it in batch mode (no gui, just simulation): 
./exampleN02 run2.mac

The .mac file is the macro that controls how the batch simulation runs. Note that if you re-issue the cmake command above, the .mac files (and some others) are overwritten, so if you think they are valuable save them somewhere.
