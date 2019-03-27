# jersey_scripts (Work in progress)
Scripts and instructions specific to the shared analysis machine in Lisbon

## Deeplabcut
The analysis machine is equiped with one GPU (GeForce GTX 1050 Ti) that can be used to accerelate the training of the classifier and analyze data.

### Step 1: create the conda environment containing Deeplabcut and tensorflow-gpu
```bash
conda env create -n <nameyourenvironment> -f dlc2.yml python=3.6
```
### Step 2: Set up password for jupyter notebook
```bash
conda activate <nameyourenvironment>
jupyter notebook password
```
Will prompt you to define a password to access your jupyter notebooks. Follow the instructions, i.e. type the password and then confirm by retyping.

### Step 4: Create an Xpra display
```bash
xpra start :NNN
```
Where NNN is a display number (e.g.    xpra start :201)

### Step 3: Launch jupyter notebook
```bash
DISPLAY=:NNN jupyter notebook --no-browser --ip=10.40.11.164
```
Where NNN is the number you used above. The IP is technically not fixed but it should almost never change. Check the slack channel to see if there have been announcements on IP change in case you have problems here.

### Step 4: Open the notebook on your local computer
Open your favorite browser and type the address https://10.40.11.164:8888 You will be prompted for a password. This is the password you defined in Step 2.

### Step 5: Open your notebook and start analyzing your data
Open the notebook you wish to run and proceed with your analysis.

### Step 6: Connect to your Xpra display to access GUI windows created by Deeplabcut
Deeplabcut uses a separate window to display a GUI that lets you mark the points of interest in your data. Those windows will be displayed on the Xpra screen :NNN you have specified above. In order to be able to access them open Xpra Launcher on your local computer and connect using the options: SSH, yourusernameonjersey, 10.40.11.164, port 22, NNN.

Type your login password on jersey and your are good to go.

## Inscopix Data Processing
We have versions 1.2.0 and 1.1.2 installed. The full paths are ```/opt/Inscopix\ Data\ Processing\ 1.1.2/Inscopix\ Data\ Processing``` and ```/opt/Inscopix\ Data\ Processing\ 1.2.0/Inscopix\ Data\ Processing```, respectively. There is a symbolic link in ```/usr/local/bin/idp``` pointing to version's 1.2.0 executable.

### Step 1: Create an Xpra display
```bash
xpra start :NNN
```
Where NNN is a display number (e.g.    xpra start :201)

### Step 2: Launch Inscopix Data Processing
```bash
DISPLAY=:NNN idp
```

### Step 3: Activate the license (first run only)
Inscopix Data Processing requires a license, which we were granted. Unfortunately online activation using license number doesn't work in Ubuntu. Hence, we perform activation offline using a license confirmation file we got from Inscopix. To perform this activation follow these steps:

1. Download the file ```capabilityResponse.bin``` from this repository.
2. Upload the file to ```jersey``` using any of the methods available (```sftp```, ```sshfs```, through an external drive, etc.).
3. After launching the Inscopix Data Processing GUI choose the option for offline activation.
4. In the next step you are going to be asked to open the activation file. Open the ```capabilityResponse.bin``` file and confirm.
5. Done!
