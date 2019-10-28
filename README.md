# CAV-Intersection-With-Model-Checking
This project implements an Autonomous Intersection Management (AIM) for Connected and Autonomous Vehicles (CAVs). It uses a Formal Verification technique called Model Checking, by using a Fiacre Model (http://projects.laas.fr/fiacre/papers.php). Fiacre stands for Format Intermédiaire pour les Architectures de Composants Répartis Embarqués (Intermediate Format for the Architectures of Embedded Distributed Components). It is a formal intermediate model to represent both the behavioral and timing aspects of systems, in particular, embedded and distributed systems, for formal verification and simulation purposes.

With Fiacre it is possible to generate a state-space model and perform model-checking using Selt (State/Event LTL) model-checker provided with Tina (TIme petri Net Analyzer) Toolbox (Tutorial: http://projects.laas.fr/fiacre/doc/usage.html)

Additionally, the Python library NetworkX (https://networkx.github.io/documentation/stable/index.html) helps to create, manipulate, and study the nodes and edges of the Reachability Graph generated by the TINA. Moreover, Matplotlib livrary is used as a visualization tool in order to analyze the behavior of the CAVs with animations.

To facilitate the compilation of the Fiacre scripts (.fcr files), you may use a Linux system or a Linux distribution for Windows. In the second case, do the following steps:

- Access the folder containing the file 'script.sh'; 
- Open a Power Shell in admin mode (shortcut: Alt+F+S+A);
- Type BASH at the command line to start ubuntu; 
- Type './script.sh file_name.fcr' without ''

After compilation, several files will be generated. The main files are a .tts folder (with petri net and time logic files), a .ktz file (this one generates the reachability graph data), and info.txt (it contains all the state and transition information you will need). The other files are .txt files that will be used to generate views in Python.

## The model

Basically, all Fiacre models have an 8x8 array grid as you can see below:

![grid](https://user-images.githubusercontent.com/50747436/66518370-72f5b500-eabb-11e9-9360-ee2aeeb87d89.png)

0's represent the street cells, 1's are the sidewalk, and the other numbers will be our CAVs. We have a cross intersection, so the CAVs can start from four different roads (A, B, C and D). Each road has four lanes. In the matplotlib each CAVs is represented by colored squares.

The transitions will follow some constraints to play realistic movements. For instance, in a scenario where the yellow CAV below want to cross the intersection (with no road convergence) and it is driving in a straight line, it can't turn over perpendicularly or go back to the same slot that it was. Also, it is not allowed to go ahead, because there is another CAV in front of it.  So, in this situation, the yellow CAV can only turn diagonally.

![mov1](https://user-images.githubusercontent.com/50747436/66520083-e220d880-eabe-11e9-957f-1353b0c2255a.png)

In the same way, if the yellow CAV is making a diagonal movement, it has the following options to choose from.

![mov2](https://user-images.githubusercontent.com/50747436/66580991-b0a71c00-eb55-11e9-971d-d9db89fa0492.png)

These constraints ensure that there will be no abrupt movements.

A round ends when all cars have had a chance to move. So, the model has a starvation-free property that makes all the CAVs to have the opportunity to move in the round. Moreover, it allows the possibility of a CAV to choose to pause and pass its turn.

