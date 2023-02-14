# Directory Purpose
Home of the CyTracker Graphical User Interface (GUI)

# Dev v Release
Dev = Devlopment branch. All changes live here.
Release = Copies of the GUI files that were used for each flight. These DO NOT change post flight & therefore serve as a memory book of what was used.

# Installation / Run Guide

## Platform Target: 
Windows 7, 10, or 11 (64 bit)

## Required Tools:
Python 3.6.5 (untested w/ newer versions)
Ardunio IDE (version doesn't matter)

## Installing Python:
1. Navigate to: https://www.python.org/downloads/windows/
2. Scroll down to 3.6.5 & Select the "Download Windows x86-64 executable installer"
3. In the first popup check the box "Add Python to PATH:"
4. In a following popup get rid of the max path length by checking/unchecking that box. 
5. To test if python has successfully installed, open up Powershell on your windows PC & type "python". If successful, it will state "Python version... blah"

## Installing Required Python Packages:
Before you launch the GUI, you need to install a package that the code base was built on. Without this it will not launch & errors will occur.
1. In your PowerShell terminal/prompt, type "pip install pyserial". 


# LAUNCH THE GUI!
Context: The mission control, recovery, and dev environment are all built into a single set of python files. Technically when we launch this application it will run all 3, BUT since mission control, recovery, and developers have different roles/permissions during flight, they all have differnet "passwords" that inform the GUI to only show them their necessary controls/info. Of course developer mode bypasses this and shows you everything.

1. Assuming you have checked out the CyTracker repository (repo) from the M2I-HABET github, using your powershell terminal navigate to where you installed the repo.
2. Once at the top level of the repo, go into the GUI folder then into your dev/Release copies. Lets go with dev for now.
3. Once inside of the dev folder, launch the GUI by typing "python ./GUI.py".
4. Password options are "dev" for development, "mc" for mission control, and "recovery" for recovery. Proceed w/ "dev".

# Explaining the GUI
Let me walk you through what you're seeing. If you you entered "dev" mode, on the top left you will see two tabs named "Mission Control" & "Recovery". If you had entered the other GUI modes, you would only see your respective tab. 

## For Mission Control:

On the top left is the "Node Status" indicator. The four red boxes will toggle between Red -> Yellow -> Green depending on the communication state of the opposing device. All of these boxes update when data is recieved from each corresponding device. 

PLATFORM is the Lora/release box that holds the payload to the ground until you press "Release Balloon" below.

Going along the top, you will see received & sent boxes, these hold the last sent / recieved radio transmission to/from your device. 

Below this are the RSSI & Contact boxes. RSSI = Received Signal Strength Indicator. 0 is the max possible signal strength and it weakens as this number drops negative. Contact is the # of seconds since Mission Control last heard from that device's radio. 

Below this the GUI is split into 3 main sections. Each holds the most fresh data from the other devices in your network. Once the payload/recovery team has GPS signal, the GUI will start displaying google maps pictures w/ location markers to show where the device is located. Note: The mission control picture will show you a very zoomed out picture showing the realtive positioning of mission control, the payload, and recovery team. You can toggle road/hybrid maps at your pleasure as well as zoom in and and out. Lastly, the "Up Time" category counts seconds since each device has powered on. This allows the network to effective pass around the newest data between devices in case Line of Sight LOS is lost between any of the two devices.

## For Recovery:

Similar to the mission control tab above, this display is a simplified version to show the relative lat & long of the payload & recovery vehicle. Due to the recovery laptop not having internet during flights, they do not get a map pictures like mission control does above. 
