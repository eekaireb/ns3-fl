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
To configure the ns3-fl-network submodule, from the root directiory, run
    
    cd ns3-fl-network
    ./waf configure
    ./waf
    
To configure the flsim submodule, from the root directory, run
    
    cd flsim
    conda env create -f environment.yml
    conda activate fl-py37
    
 The above commands create and activate an Anaconda enviroment, with all of the dependencies needed to run flsim. For a more detailed description on setting up and running flsim, refer to the original [flsim repository](https://github.com/iQua/flsim).
 
### Simulation 
To start a simulation, from the root directory, run 

    cd flsim
    python3 run.py --config=configs/config.json 
    
To specify simulation parameters, we use the same configuration JSON files as in [flsim](https://github.com/iQua/flsim), though we add more fields to allow for a wider range of data and algorithm settings, in addition to network settings. 

There are examples of how to set up the configuration file in flsim/configs/ns3-fl.

#### Configuration Options 
The configuration options which are not listed below were a part of the original [flsim](https://github.com/iQua/flsim). Refer to the original [flsim wiki](https://github.com/iQua/flsim/wiki/Configuration) for details on how to set these parameters. 
In the nested model section `model`: 
* `size`: Specifies the model size in kB. The model size will be used in the network code. 
In the nested section `network`, 
* `folder`: Specifies folder in the scratch file which should be run for the network. The default parameter, which works with the rest of our network settings, is `wifi_exp`. 
* `type`: Specifies the type of network to run the simulation on. Currently supported options are `ethernet` and `wifi`. The network code is in the scratch folder of the ns3-fl-network submodule. 
* `wifi`: A nested section, within the `network` section, that specifies configurations for the WiFi network. 
    * `loss`: Specifies the mean of the range of propogation loss in the network. We use the RandomPropogationLossModel in the network code to simulate loss. The range for the loss is 20 below and above the specified mean. 
    * `max_packet_size`: Specifies the maximum size for a packet to be sent over the network. 
* `ethernet`: A nested section, within the `network` section, that specifies configurations for the Ethernet network. 
    * `max_packet_size`: Specifies the maximum size for a packet to be sent over the network. 
* `device_type`: Specifies the device type for the clients in the network simulation. The device type is used when calculating the average power and energy consumed during each round of the simulation. Currently, the supported options are `400` and `4` for Raspberry Pi 400s and 4s, respectively.

#### Troubleshooting
In the event that the submodules are not directly accessible, here are the links to the submodules: 
* [ns3-fl flsim repository](https://github.com/eekaireb/flsim).
* [ns3-fl-network repository](https://github.com/eekaireb/ns3-fl-network).

These repos can be seperated cloned into the ns3-fl folder. The configuration process will be the same as above. 
