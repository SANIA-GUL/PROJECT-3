# PROJECT-3
SONET

Step 1

For concatenating the audio files generated from a single speaker. Run it on the Data sets TIMIT and McGill by unzipping these folders and before running it create an empty folder with the name 'Concatenated'. Download these datasets from the websites mentioned in the references of the paper below.

Step 2

For creating clips of duration 1.05 sec each for training and testing the U-Net.

Step 3

For creating MAT files containing the ILD/IPD values of each source. The user has to enter the RT60 of the anechoic room and the location of the second source on the prompt. The first source is assumed to be in front of the binaural setup. Just enter 0 there as the room was anechoic. The location of the second source can be from 1 to 18., whichever is your choice. You must have the RIR folder of this room with you. When storing MAT files for target use '=s1' in line 162 and for interferer use '=s2'. If s1 is chosen no effect of the S2 value will occur, as the end mixture has only a single active source S1. (I restricted myself to only 6 S2 values as each will require training a separate network, which was time-consuming).

Step 4

For creating the labels of each class, i.e. white for Target, Black for interferer. Keep the value '=0' for black and '=255' for white in Line 8 of the program.

Step 5

For training the U-Net. Step5NeuralNetwork.m contains a simple U-Net. However, Step5NeuralNetworkNoOverlap.m contains a program with Convolutional Layer modifications causing the stride size to be equal to the Filtersize, ensuring the independence of TF units. You can apply whichever gives you good results. U have to train separate networks for ILD and IPD cues. Save the trained network with any name (e.g. GREGNET, IPDnet) as you will need it for steps coming ahead.

Step6

This is a testing step in which a mixture of two sources is prepared and its ILD and IPD matrices are stored in MAT files. These files are given at the input of GREGNET, IPDnet and the output masks are stored again in MAT files.

Step7

The masks generated in step 6 are reloaded and applied over the speech mixtures and SDR and STOI are calculated.



Cite As: •	Sania Gul, M. S. Fulaly, M. S. Khan, and S. W. Shah.: “Clustering of spatial cues by semantic segmentation for anechoic source separation”, Applied Acoustics, Vol. 171, January 2021.

