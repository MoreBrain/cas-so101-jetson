# LeRobot installation from HuggingFace

https://huggingface.co/docs/lerobot/en/installation

#ATTENTION: use uv (not conda)

Create folder for your project e.g.:
```
mkdir -p ~/repos/cas_26_YOUR_NAME/lerobot
cd ~/repos/cas_26_YOUR_NAME/lerobot
```


Install python env and source:
```
uv python install 3.12
uv venv --python 3.12

source .venv/bin/activate
```

Additional packages needed:
```
sudo apt install ffmpeg
```

Install relevant packages
```
uv pip install lerobot[feetech,core_scripts]
```

Maybe needed later:
```
uv pip install 'lerobot[dataset]'      
uv pip install 'lerobot[training]'   
uv pip install 'lerobot[hardware]'   
uv pip install 'lerobot[viz]'   
```


# SO-101 - getting it to run
https://huggingface.co/docs/lerobot/en/so101

- connect your follower robot to your jetson

## Find ports of robot
```
lerobot-find-port
```

give access:
```
sudo chmod 666 /dev/ttyACM0
sudo chmod 666 /dev/ttyACM1
```

### Permission to use the USB ports

The ports (`/dev/ttyACM*`) belong to the `dialout` group. Add yourself once:

```bash
sudo usermod -aG dialout $USER
newgrp dialout
```


## Setup Motor ids and baudrate for leader and follower 
thus should be already done with the shipped arms. If however something fails do this step.

```
lerobot-setup-motors \
    --robot.type=so101_follower \
    --robot.port=/dev/tty.usbmodem585A0076841  # <- paste here the port found at previous step
```

## Calibrate both arms
```
# change the port if needed
lerobot-calibrate --robot.type=so101_follower --robot.port=/dev/ttyACM1 --robot.id=lab_follower_01
lerobot-calibrate --teleop.type=so101_leader  --teleop.port=/dev/ttyACM0 --teleop.id=lab_leader_01 
```


# Teleoperate
from https://huggingface.co/docs/lerobot/en/il_robots



# Troubleshooting
If you encounter build errors, you may need to install additional system dependencies: cmake, build-essential, and ffmpeg libs. To install these for Linux run:

```
sudo apt-get install cmake build-essential python3-dev pkg-config libavformat-dev libavcodec-dev libavdevi
```