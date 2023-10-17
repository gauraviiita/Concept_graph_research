# Docker dev setup OVMM

## Data setup

### Clone Branch

''' 
git clone https://github.com/facebookresearch/home-robot.git --branch home-robot-ovmm-challenge-2023-v0.1.2
'''

### Install git-lfs

''' git lfs install '''

### Set home_robot_root

''' export HOME_ROBOT_ROOT=<path/to/home-robot>

### Download data

'''
sh $HOME_ROBOT_ROOT/projects/habitat_ovmm/install.sh
'''

## Open container in vscode

### Build Container

'''
cd $HOME_ROBOT_ROOT/projects/habitat_ovmm
docker build . \
    -f docker/ovmm_random_agent.Dockerfile \
    -t ovmm_random_agent_submission
'''

### Setup nvidia container toolkit

See [here](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html)


### Start interactive container 

'''
docker run -dit -v <path/to/home-robot/data>:/home-robot/data \
      --runtime=nvidia \
      --gpus all \
      -e "AGENT_EVALUATION_TYPE=local" \
      -e "LOCAL_ARGS='habitat.dataset.split=minival'" \
      ovmm_baseline_submission bash
'''

### Open container in vscode

Using the remote-container extension in vscode you can open the running container in a new vscode window. 

## Developing contact graph with vscode

you can just install the needed packages into the home-robot environment 

'''
. activate home-robot
'''

this will activate the home-robot environment, in here you can install your dependencies. you can clone the repo inside the container or drag and drop you folders into the vscode window




