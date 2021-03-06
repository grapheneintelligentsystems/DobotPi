# DobotPi - Control Dobot on the Raspberry Pi 3

#####Quick Demo youtube video: https://www.youtube.com/watch?v=DYDdMDqEmaE

###Warning: controlling stepper motors on the raspberry pi is not 100% reliable

This software allows you to control a Dobot robotic arm with a raspberry pi 3. There are numerous advantages to controlling the Dobot with a raspberry pi as opposed to an arduino, FPGA, or other electronics that requires movement data to be transmitted serially. The code is simpler and less of it is required. The arm can move faster because time is not spent sending data from device to device. Running the code from the raspberry pi means you don't need a separate computer (from say a microcontroller) to control the Dobot. The raspberry pi is the computer! Installing everything needed to edit the code is dead simple, just type one line in the terminal: "sudo apt-get install python3-pyqt5". This works on the raspberry pi 3, but won't work on older versions without more setup (according to a friend, I haven't tested this). The pi 3 (running the raspbian OS at least) comes with the necessary files installed and has sufficient RAM. 

#####Features:
1. _Graphical User Interface (GUI) to manually control the robot_
2. _Move to cartesian (x,y,z) coordinates_
3. _Move in smooth linear lines from point to point_
4. _Step the robot by variable distances (in mm) in x, y, and z directions_
5. _Gives a read out of the current position in terms of x,y,z and angles_
6. _Error checking_
7. _Code is written in python and uses the cross platform Qt library for the graphics_
8. _code has lots of comments_

![alt text](https://github.com/mikef522/DobotPi/blob/master/Schematics/DobotPi_Stepper_Driver_Wiring_Schematic.PNG "DobotPi Wiring Schematic")
###Code and hardware setup instructions:
__________________________________________
1. Create the simple electronic circuit described in the youtube video here (see also the DobotPi Wiring schematic in the "Schematics" folder in this repository): **https://www.youtube.com/watch?v=dwImOfUukV8**

2. Set up a raspberry pi 3 running raspbian (jessie). This is the default OS.

3. In the raspberry pi terminal, type: "sudo apt-get install python3-pyqt5" and press enter.

4. Download the files in the "Python-Code" folder in this repository. Place them in the same folder on the raspberry pi (name the folder whatever you like and place it wherever you like).

5. Open the DobotPiGUIMain.py file using the IDLE 3 editor and select Run > Run Module (_alternatively, use the pi's terminal to navigate to the directory you created in step 4 and type "sudo python3 DobotPiGUIMain.py", and hit enter_)


_**Note on future maintenance:**_ I will not be developing general purpose dobot features like gripper and laser control, and possibly not even a general purpose way to program movement. Someone else will have to pick up that torch. The only reason I'm programming this software is because I need these basic features for lab robot software that I'm programming. Whatever useful general purpose code comes out of that project, I am putting here; therefore, I don't expect to to update this terribly often, especially after I get the basics implemented. On the flip side, if you are a scientist like me and want to use Dobot as a lab robot, I'll post a link here to the relevant github when I create it. 

_**Note on support:**_ I'm a scientist working on making replacement organs, which means I have very little free time and I'm making no guarantees of support, espcially timely. That being said, feel free to contact me, but don't be surprised if I respond after days, weeks, or never.

#####To Do (my personal hardware and software to do list):
-----------------------------------------------------

- [ ] Implement move to angles function

- [ ] Address boundary case where arm transitions from left to right side and vice versa

- [ ] Address case where end point is a valid position, but intervening points aren't

- [ ] Implement acceleration

- [ ] Create an API to enable programming multiple moves from point to point

- [ ] Implement a move to home position button

- [ ] Correct Inverse kinematics floating point problem as identified by Max (open-dobot)

- [ ] Code documentation overview with flow charts

- [ ] Emergency stop

- [ ] Movement speed control / specify time it takes to move from point to point

- [ ] Account for end effector position (currently, all positions are calculated for the very end of the lower arm)

- [ ] Install limit switches on the Dobot and implement the code to control them. Could use a photointerrupter like Max (open-dobot) or some hall effect limit switches that use magnets (or combination). Either is probably better than a manual limit switch. All are only a few dollars each. Will likely need to 3d print some mounts for these.

- [ ] Buy and install NEMA 17 stepper motors that have greater torque (for increased payload ability). Unsure how much these will cost. The stepper motors that came with the Dobot have nice screws on the back that rotate with the motor and would enable one to mount a rotary encoder on the rear, perhaps needing a 3d printed adapter.

- [ ] Buy and install rotary encoders on the stepper motors (to keep track of the actual steps taken and avoid missed steps). These can be used to detect if someone hits the arm for example, and the robot can then account for the missed steps. These will be ~$20-40 each depending on which one you get.

- [ ] Implement 3D Workspace/Arm view

- [ ] Create a video showing how to set up and run the code from start to finish.

- [ ] Create code flow charts. Improve code comments. Reorganize code. Get rid of old code/update comments.

- [ ] Create some sort of simple executable-like version of the software that can be easily distributed (no code setup).

- [ ] Detect loss of power to motors somehow

- [ ] Various code optimization

