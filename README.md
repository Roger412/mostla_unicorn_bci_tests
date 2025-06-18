# Mostla Unicorn C API BCI Tests

This repository contains the developed and acquired codes relevant for the data acquisition from the Unicorn Hybrid Black EEG based on their official C APIs and developing a Python wrapper using the Ctypes library. 

- Visualization and data acquisition tests are on the Unicorn py test folder, developed using the Linux C API python wrapper.  
- The developed codes for an attempt for a BCI with CSP are all in the CSP_Attempts folder, they are incomplete, no successful tests yet 
- The Linux C API Tests folder uses the Linux C API for data acquisition
- The Windows C API Tests folder uses the Windows C API for data acquisition

### To Do

- Replicate mindmonitor in python using data acquisition C APIs 

### Current status

- WINDOWS & LINUX C API SUCCESFUL data acquisition tests

- CSP unsuccessful tests

- Python C API Wrapper success:
>    Must check n samples in get_data to better python live receive

- LSL receive through python with hotspot success

- Lenovo PC with windows 10 driver NIC2 driver not working? Must figure out why or use another computer

- NIC2 for ubuntu? the only option shown is a plugin for matlab (EEGLab)