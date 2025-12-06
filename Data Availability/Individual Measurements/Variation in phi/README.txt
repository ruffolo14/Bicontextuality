data file formatted as a python dictionary in a txt file and can be read using the following code:

with open('data.txt', 'r') as f:
    s = f.read()
    data = ast.literal_eval(s)

dictionary keys are formatted as a tuple with the first value as the angle parameter in degrees followed by ion label

dictionary values are recorded as binary results (0 indicates qubit spin down and 1 indicates qubit spin up)

simultaneous measurements are recorded for results with the same parameter value but different ion label (for example index 0 of (10,"Ion 1") and (10,"Ion 2") were measured simultaneously and so on)