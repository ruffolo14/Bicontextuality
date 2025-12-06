the file labelled "0 theta.txt" is a data file formatted as a python dictionary in a txt file and can be read using the following code:

with open('data.txt', 'r') as f:
    s = f.read()
    data = ast.literal_eval(s)

dictionary keys are formatted as a tuple with the first value as the angle parameter in degrees followed by ion label

dictionary values are recorded as binary results (0 indicates qubit spin down and 1 indicates qubit spin up)

simultaneous measurements are recorded for results with the same parameter value but different ion label (for example index 0 of (10,"Ion 1") and (10,"Ion 2") were measured simultaneously and so on)

note: the parameters for the file "0 theta.txt" has no real meaning and is just a placeholder label for the number of repetition cycles



in order to facilitate more efficient data taking the rest of the data files in this folder were recorded in a different format from "0 theta.txt"

the files with "pop" in the name records the average excited state probabilities while files with "parity" records the parity values (parity = 00 + 11 - 01 - 10 where 00 refers to the state population of both qubits being spin down)

the numbers in the file names hold no real meaning and is meant to label the various repetitions of the exact same experiment (for example "delay_pop3_0" and "delay_parity3_0" refers to the same repetition cycle)

the files in the "extra" folder are also repetitions of the same experiment and was included in the paper figures

to read the data in python the following code can be used: 

with open(file, 'r') as file:
     file_data = []
     for line in file:
           arr = json.loads(line.strip())
           file_data.append(arr)

for files with "pop" in the name: 

file_data[0]: array of carrier interaction times in microseconds used to create the initial qubit state which corresponds to the value of theta

note: all times have been calibrated and arranged to correspond to the values of 2*theta in the list [ 10,  20,  30,  40,  50,  60,  70,  80,  90, 100, 110, 120, 130, 140, 150, 160, 170, 180] in degrees

file_data[1]: a list of lists of average excited state probabilities for the different states arranged as such [00, 10, 01, 11, (10 + 01)]

file_data[2]: a list of lists of the errors on the average excited state probabilities for the different states arranged as such [00, 10, 01, 11, (10 + 01)]

file_data[3]: the number of measurement repetitions in order to calculate the average population data in this file


for files with "parity" in the name: 

file_data[0]: array of carrier interaction times in microseconds used to create the initial qubit state which corresponds to the value of theta

note: all times have been calibrated and arranged to correspond to the values of 2*theta in the list [ 10,  20,  30,  40,  50,  60,  70,  80,  90, 100, 110, 120, 130, 140, 150, 160, 170, 180] in degrees

file_data[1]: a list parity values for each value of 2*theta

file_data[2]: a list of the errors on the parity values for each value of 2*theta

file_data[3]: the number of measurement repetitions in order to calculate the average population data in this file


