# ns3-fl

## Description 
Ns3-fl is a federated learning simulator which takes into consideration data, algorithm, and network. Ns3-fl is built off of two existing simulators, [flsim](https://github.com/iQua/flsim) and [ns-3](https://www.nsnam.org). Flsim is the federated learning simulator, which simulates data and algorithm over an ideal network. Ns-3 is an open source discrete event network simulator, created for research and educational use. 
Ns3-fl also contains an power module which computes the computational time, power, and energy, as well as the transmit power, and energy. 

## Installation 
To install ns3-fl, first clone the respository. To clone the submodules, run 

    cd ns3-fl
    git submodule update --init --recursive
    
Next, install [Anaconda](https://www.anaconda.com/products/individual). 

### Configuring each submodule
To configure the ns3-network submodule, from the root directiory, run
    
    cd ns3-network
    ./waf configure
    ./waf
    
To configure the flsim submodule, from the root directory, run
    
    cd flsim
    conda env create -f environment.yml
    conda activate fl-py37
    
 The above commands create and activate an Anaconda enviroment, with all of the dependencies needed to run flsim. For a more detailed description on setting up and running flsim, refer to the original [flsim repository](https://github.com/iQua/flsim).
 

### If repositories are clean, the project can be updated by the following commands:

    cd ns3-fl
    git pull
    git submodule update --init --recursive

