# CAV-Intersection-With-Model-Checking
This project implements an Autonomous Intersection Management (AIM) for Connected and Autonomous Vehicles (CAVs). It uses a Formal Verification technique called Model Checking, by using a Fiacre Model (http://projects.laas.fr/fiacre/papers.php). Fiacre stands for Format Intermédiaire pour les Architectures de Composants Répartis Embarqués (Intermediate Format for the Architectures of Embedded Distributed Components). It is a formal intermediate model to represent both the behavioral and timing aspects of systems, in particular, embedded and distributed systems, for formal verification and simulation purposes.

With the Fiacre model we can generate the state space of a model and perform model-checking using the Selt (State/Event LTL) model-checker provided with Tina (TIme petri Net Analyzer) Toolbox (Tutorial: http://projects.laas.fr/fiacre/doc/usage.html)

Additionally, the Python library NetworkX (https://networkx.github.io/documentation/stable/index.html) helps to create, manipulate, and study the nodes and edges of the Reachability Graph generated by the TINA. Moreover, Matplotlib livrary is used as a visualization tool in order to analyze the behavior of the CAVs with animations.

To facilitate the compilation of the Fiacre scripts (.fcr files), use a Linux system or a Linux distribution for Windows. In the second case, do the following steps:

- Access the folder containing the file 'script.sh'; 
- Open Power Shell in admin mode (Alt+F+S+A);
- Type BASH at the command line to start ubuntu; 
- Type './script.sh file_name.fcr' without ''

After compilation, several files will be generated. The main files are a .tts folder (with petri net and time logic files), a .ktz file (generates a reachability graph), and info.txt (contains all state and transition information). The other files are .txt files that will be used to generate views in Python.
