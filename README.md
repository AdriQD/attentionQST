# attentionQST

In this repo are stored the codes used for throughout the experiments for the realization of the article "Enhancing general quantum state tomography via attention-based neural networks".

In this project we carry out a quantum state tomography task (QST) with an hybrid protocol, that combines a pre-procesing stage and a deep learning post-processed stage. In this repo, classical reconstruction method considered are linear inversion (available) and maximum likelihood estimation (available soon).
The deep learning model is a combination of 1D convolutional neural networks and self-attention transformer. The project goal is doublefold: improve over the classical QST approach, by generating a full-fledge deep learning noise filter function, and second, achieve higher generalization ability, i.e. reducing the training data amount, for the network model (see Fig.2 in the article).

The tompgraphy pipeline consist of two main blocks:

1. pre-processing. In this step, we first generate  random density matrices,  and then we work out the associated born values, using a pre-selected set of operators (SICs, Pauli). We introduce a statistical approximation inside our data by using multinomial function for the SICS, or Gaussian approximation for the Pauli basis. 

2. post-processing step. After the first reconstruction pass, we train a deep neural network model that learns a noise filtering function for the general space of density matrices (mixed or Haar-pure).


All the codes are provided in notebook, with commented markdown blocks.The commented notebooks are thought for being self consistent and indipendent. In this way, we aim at breaking down the whole pipeline in separeted, sorted steps.


##REPO STRUCTURE


1.In the "/basis" folder, the files with the the different basis and the dual basis used to generate the datasets. In the ./4-qbits folder, the 4 qubits basis and dual basis obtained from tensor products of local SIC-POVM and 4 qubits Pauli operators. In the ./square-root-povm the global square-root POVM of dimension d=3,9.

2.In the "pre-processing" folder is loaded data-generation-b.npy file. This file generates the dataset of random density matrices by using the "brute force" Linear Inversion reconstruction function. The LI reconstruction method makes use of the differet dual basis (saved in separeated files) previously generated.  The LI outputs make up for the training/validation/testing datasets for the network numerical experiments. 


3.The "model" folder contains the notebook with the neural network code. Inside the notebook is possible to find explication of the paramater settings used during the different experiments (benchmarking mixed states, OAT reconstruction).


(UNDER CONSTRUCTION)
4.Last, in the "Inference" folder, we file a notebook for model inference, to reproduce the article plots for the OAT states files in Fig.3, the trained model file is also provided. Along with it, the Fisher information plot functions.
