# Max_Flow_Min_Cut_Algorithm
This project finds the feasible flow region of a multi-commodity network via a Max-Flow Min-Cut style duality.

This repository contains code to find the feasible flows in a multi-commodity network using local flows over cuts. See the MaxFlowMinCut Jupyter notebook. The accuracy of the duality used is shown in my thesis (forthcoming).

Note that, unlike for single commodities, the multi-commodity max-flow problem is NP complete. This code may be prohibitively slow for large networks or networks with many possible flow values over each arc. Still, it demonstrates the duality and can determine the feasible flow region (and give realizations of each flow value) for relatively simple networks.

To use, modify the second cell (#INPUTS) with versions of CUTS and CAPACITIES corresponding to your desired network. Then, run cells 1-3. Cell 3 outputs a table containing all flows.

CUTS is a dataframe with column names given by the arcs in the network, rows corresponding to cuts, and entries indicating if the arc corresponding to the column is in the cut corresponding to the row. A 1 indicates the presence of the forward arc, a 0 indicates the absence of the arc, and a -1 indicates the presence of the backward arc.

CAPACITIES is a dictionary linking arc names to a numpy array of lists of allowed flows through the arc. For instance, in a two-commodity network, we might have 'a1':np.array([[0,0],[0,1],[1,0],[1,1],[2,0],[2,1]]) as one entry, meaning [0,0], [0,1],  ... are legal flow pairings of commodities x_1,x_2 along arc a1.