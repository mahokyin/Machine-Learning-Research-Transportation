Introduction:
The results of prediction and visualization are under the folder 'Result'. 
What those ML model predicted were the locations of each record and what the html files visualize are the top 10 places 
that vehicles speeded and visited. Those html files are generated by Python scripts, comparing the location speed limit to
the car's record and counting the frequency of all locations.

Instruction:
The description below is the instruction telling you how to run the entire software package. 
Please make sure the software and libraries listed installed, before running it:

1) Python 3.6.x (Data Preprocessing, Data Visualization) and its libraries listed below:
Data Preprocessing:
- csv (read the excel file)
- sqlite3 (access SQLite DB)
- requests (Network call for traffic API)
- json (Read json format data from traffic API)
- statistics (Math calculation)

Data Visualization
- loadmat (Read the matlab file)
- polyline (Decode the encoded data of coordinates)
- gmplot (Plot stuffs on Google Maps)

How to install libraries ?
Run the command line below on Windows console or Mac terminal
python -m pip install [package-name]

2) Matlab (Machine Learning)
- Make sure it includes the ML toolbox

3) DB Browser for SQLite (GUI SQLite software, optional but recommend)

The entire project includes three major parts:
1) Data preprocessing
2) ML model prediction
3) Visualization

Steps:
Data-preprocessing
1) Use DB Browser or command line to create the empty database and  save as traffic.db to the folder '1-data-preprocessing'
2) Run Python scripts in the folder '1-data-preprocessing':
    2.1: Run '1-write-original-sensor-to-db.py' to store the sensor info into the db
    2.2: Run '2-get-speed-mean-to-db.py' to store the speed limit of set sensors into the db
    2.3: Run '3-read-month-traffic-data-to-db.py' to store the training data into the db
    2.4: Run '4-read-month-traffic-test-data-to-db.py' to store the testing data into the db
3) Copy the traffic.db from the folder '1-data-preprocessing', into the folder '2-ml-model'

ML model classification
4) Open Matlab
5) Run Matlab scripts in the folder '2-ml-model'
    5.1: Run 'ml_decision_tree.m' (Decision Tree model)
    5.2: Run 'ml_knn.m' (KNN algorithm, where parameters are given in the 10 - fold cross validation)
    5.3: Run 'ml_svm_linear.m' (SVM with linear kernel)
    5.4: Run 'ml_svm_poly.m' (Optional, my paper doesn't include it because it takes long time for training)
    5.5: Choose the model with the highest accuracy and F1 score
    5.6: Find the matix variable named as 'label' in the model you selected, then right click it, to choose 'Save As...'
    5.7: save the matrix as an independant file called 'test_result.m' to the folder '3-visualization'

Data Visualization
6) Copy the 'traffic.db' from '1-data-preprocessing' to '3-visualization'
7) Run Python scripts below:
    7.1: Run 'original-visualize.py' and it will export 'sensor.html' including the sensor locations
    7.2: Run 'visualize-top-k-speeding.py' and it will export 'topk-speeding-result.html' including the top 10 speeding area
    7.3: Run 'visualize-top-k-visited.py' and it will export 'topk-visited-result.html' including the top 10 places that vehicles visited
    7.4: Open html files built by scripts and observe results

    Remark: If you want to show more or less places, you can change the value of 'topk' in 'visualize-top-k-speeding.py' or 'visualize-top-k-visited.py'



