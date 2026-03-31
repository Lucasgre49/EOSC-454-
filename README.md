# EOSC-454-
Lucas Green EOSC 454 Project Repository
This is a repository for my final project in eosc 454: applied geophysics. I am planning on creating a full inversion of public drone mag data using simPEG. To begin this project I am using 2D synthetic data to first go through the forward problem and will continue on to invert and extend to 3D. 



Project Proposal:

Lucas Green
EOSC 454 Project Proposal
March 19, 2026

Project Question

Can a 2D inversion of line data extracted from a 3D magnetic drone UXO dataset accurately recover the location and geometry of subsurface targets using SimPEG? The accuracy of the inversion will be evaluated based on the accuracy of the position, relative size, and number of anomalies compared to known or reference models.

Methods and Software:

This project will use the Python-based library SimPEG, implemented in a Jupyter Notebook. The project will progress from simple to more complex scenarios in order to build a sound understanding of inversion.

First, I will perform forward modeling and inversion on a simple synthetic dataset containing a single magnetic target with remnant magnetization. A 2D tensor mesh will be constructed, and the magnetic response will be simulated using standard assumptions about induced and/or remnant magnetization. The inversion will be carried out using an L2 data misfit and Tikhonov regularization to stabilize the solution. 

Next, I will extract a 2D line of data from a publicly available 3D drone magnetic survey dataset and apply the developed inversion workflow. This will allow me to assess how well a simplified 2D inversion can approximate features present in a full 3D dataset. If time permits, I attempt to do a full 3D inversion of both datasets using SimPEG. 

Datasets:
This project will use a combination of synthetic and real datasets:

One synthetic UXO dataset:
https://www.kaggle.com/datasets/mbjunior/uxo-classification-from-magnetometry-data

Public Drone UXO datasets by SPH Engineering:
https://www.sphengineering.com/integrated-systems/test-range-for-geophysical-sensors?is-technologies=magnetometer

Goals and Stretch Goals:
Primary Goals:
Successfully perform 2D inversions on simple and complex synthetic UXO datasets
Recover the location and approximate geometry of magnetic anomalies
Evaluate inversion performance based on anomaly resolution and stability

Stretch Goals:
Extend the inversion to full 3D 
Incorporate remanent magnetization effects more rigorously
Compare 2D and 3D inversion results to assess limitations of 2D approaches

;}
