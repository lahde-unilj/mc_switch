# mc_switch
Modelling of magnetocaloric device comprising static thermal switches

Please acknowledge mc_switch by citing paper Ferrofluidic thermal switch in a magnetocaloric device: https://doi.org/10.1016/j.isci.2022.103779

The usage of the code is presented in our STAR protocol article (DOI: 10.1016/j.xpro.2022.101576).

The code comprises two scripts, one-thread script runcycles.py and multiple-thread script runcycles_hpc.py, and 9 other modules that are imported into the scripts.

The preparedata.py module contains a function for importing and initializing the (m)cm data to be used in the simulations.

The simulation.py module contains a class named Simulation with all the attributes needed for the simulation.

The cycle.py module contains a function that defines the processes inside the cycle: magnetization, demagnetization, and both heat-transfer processes. It also updates and returns the temperatures of the nodes after each process.

The magnetization.py module contains a function to calculate the adiabatic temperature change of the nodes inside the (m)cm based on the current temperature and the predicted magnetic field change. It updates and returns the temperatures of the nodes inside the (m)cm after magnetization (increased temperature) or demagnetization (decreased temperature) process.

The heat_transfer.py module contains functions that define the heat-transfer process and the return temperatures of all the nodes after the heat-transfer process.

The makematrix.py module contains the functions for building the system of equations for the process of heat transfer inside the device. It considers the locations of the components, the properties of the nodes inside the components, the thermal resistance between the components, the internal heat generation and the boundary conditions. The system of equations is arranged in a tridiagonal matrix and a vector of right-hand sides.

The myprint.py module contains the functions called by other modules for exporting different data (temperatures, properties, resulting temperatures, heat fluxes, etc.) to the console or in the form of output files.

The thomas.py module contains a function for solving the tridiagonal system of equations by Thomas algorithm (tridiagonal matrix algorithm). The function takes lists of the coefficients a, b, c (under-diagonal, diagonal and above-diagonal coefficients) and z (right-hand sides), calculated with the functions from the makematrix.py module, and returns a new, modified set of temperatures for all the nodes of the device after a heat-transfer step.

The magneticwork.py module contains a function for calculating the magnetic work from the entropy change for each node inside the (m)cm for the whole thermodynamic cycle. For the model to be thermodynamically accurate, the magnetic work of the (m)cm calculated in this way must be equal to the difference between the heat fluxes into and out of the device plus the eventual internal generated heat. Both values are exported at the end of the simulation in the quasi-steady state of the system to check the validity of the simulation.

In each module, there are in-line comments describing the purpose of each method in the code.
