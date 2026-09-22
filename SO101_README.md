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
```


## Setup Motor ids and baudrate for leader and follower(maybe already done)
```
lerobot-setup-motors \
    --robot.type=so101_follower \
    --robot.port=/dev/tty.usbmodem585A0076841  # <- paste here the port found at previous step
```

## Calibrate both arms

### follower
lerobot-calibrate \
    --robot.type=so101_follower 
    --robot.port=/dev/tty.usbmodem58760431551 \ # <- The port of your robot
    --robot.id=my_awesome_follower_arm # <- Give the robot a unique name
### leader
lerobot-calibrate \
    --teleop.type=so101_leader \
    --teleop.port=/dev/tty.usbmodem58760431551 \ # <- The port of your robot
    --teleop.id=my_awesome_leader_arm # <- Give the robot a unique name



Then **log out of the desktop session** (system menu → power icon → *Log Out*) or reboot.
Locking the screen is not enough: new terminals keep the old groups until you log in
again. To use it right away in one terminal only: `newgrp dialout`.

Check: `groups` lists `dialout`. Without it you get `Permission denied: '/dev/ttyACM0'`.



# Teleoperate
from https://huggingface.co/docs/lerobot/en/il_robots



# Troubleshooting
If you encounter build errors, you may need to install additional system dependencies: cmake, build-essential, and ffmpeg libs. To install these for Linux run:

```
sudo apt-get install cmake build-essential python3-dev pkg-config libavformat-dev libavcodec-dev libavdevi
```