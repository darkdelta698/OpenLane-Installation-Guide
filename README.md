OpenLane Installation Guide (WSL + Docker + Sky130)

A beginner-friendly step-by-step guide to installing and configuring the OpenLane ASIC design flow on Windows using WSL2, Ubuntu, Docker, and the Sky130 PDK.

What This Guide Covers:

 WSL2 Installation
 Ubuntu Setup
 Docker Desktop Setup
 OpenLane Installation
 Sky130 PDK Installation
 Verilog Simulation Setup
 GTKWave Setup
 Yosys Setup
 OpenROAD GUI
 Magic Layout Viewer
 Common Error Fixes

System Requirements
Recommended:
 Windows 10/11
 16 GB RAM minimum
 50+ GB free storage
 Docker Desktop
 WSL2 enabled

 
->Step 1 — Install WSL2

Open PowerShell as Administrator:

cmd:

    wsl --install
  
then,

Restart your PC.

->Step 2 — Install Ubuntu

Install Ubuntu from Microsoft Store.

then,
Launch Ubuntu and create:

Username
Password

Update Ubuntu:

cmds:

    sudo apt update
  
    sudo apt upgrade -y

->Step 3 — Install Verilog Tools

cmd:

    sudo apt install -y build-essential git gtkwave iverilog yosys

then Verify:

cmds:

    iverilog -V
  
    gtkwave --version
  
    yosys

->Step 4 — Install Docker Desktop

Download: https://www.docker.com/products/docker-desktop/

During installation:

Enable WSL2 backend

Enable Ubuntu integration

Verify:

cmds:

    docker --version
  
    docker run hello-world

->Step 5 — Clone OpenLane

cmds

    git clone https://github.com/The-OpenROAD-Project/OpenLane.git
  
    cd OpenLane

Checkout stable version:

cmds:

    git checkout 2023.09.07
  
->Step 6 — Install OpenLane

cmd:

    make

If Python venv error occurs:

cmd:

    sudo apt install -y python3-venv

Run again:

cmd:

    make

Step 7 — Install Sky130 PDK

cmd:

    make pdk

This download is large and may take time.

Step 8 — Verify Installation

cmd:

    make test

Expected output:

[SUCCESS]: Flow complete.

Common Errors and Fixes

Docker not starting

Restart Docker Desktop.

Run:

cmd:

    wsl --shutdown

Then restart Docker.

Magic version mismatch

Use Magic inside OpenLane Docker container instead of Ubuntu-installed Magic.

PDN Error in Small Designs

Increase DIE_AREA in config.json.

Example:

"DIE_AREA": "0 0 300 300"

Useful Commands

Start OpenLane container:

cmd:

    make mount

Run design:

cmd:

    ./flow.tcl -design <design_name>

Open OpenROAD GUI:

openroad -gui
 Tools Used
 OpenLane
 OpenROAD
 Magic
 Sky130 PDK
 Docker
 GTKWave
 Icarus Verilog
 Yosys
 
Author:
Rohan Pydipalli
B.Tech ECE (VLSI)
