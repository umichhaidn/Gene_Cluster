# Gene Expression Clustering with UPGMA
This repository contains the iPython notebook and sample data for the tutorial on conducting a gene expression clustering analysis with UPGMA. Additional demonstration material can be accessed via the Anvil App clone link, which will create a clone of all design and coding elements used to construct a demo app on Anvil.works.


## Setup

### Option 1: Local Machine Environment
To run this analysis locally on your machine, follow the [installation instruction](https://www.anaconda.com/products/individual) for  Anaconda Python. Once installed, be sure that the latest versions of the following libraries are installed: pandas, altair, numpy, scipy, sklearn.
Advantage: Use your own hardware resources to run the analysis.
Limitation: Basic knowlege of python coding environments required.
Use this option if you want to analyze a very large data set (>30,000 data points).

### Option 2: Google Drive
To run this analysis on Google Drive, simply upload the Gene_Cluster_App.ipynb file to a folder on your Google Drive account. All required libraries will either be pre-loaded on the Google Colab environment or installed directly by the code.
Advantage: Simple setup.
Limitations: Resources on Google Colab may not be sufficient to run the model or display graphs of very large data sets. See [here](https://research.google.com/colaboratory/faq.html) for further infomation on Google Colaboratory.
Use this option if you want to analyze moderately sized data sets (<30,000 data points).

### Download Sample Data
Sample data files are provided to demonstrate data formatting. Note, that all data used in this analysis are expected to be in CSV format. It is possible to save excel files in CSV format. The sample data can be found in the 'data' folder. Download this entire folder and place it in your local environement or Google Drive folder. The sample data can be found under the following three titles:
data1_clusters_diff.csv
data2_CO_and_JO_diff.csv
data3_ML data set Whole Data.csv

### Prepare your own data
Save your data in CSV format and add a copy to the data folder.

### Download ipynb file. 
Download the file 'Gene_Cluster_App.ipynb' and place it in your local environement or Google Drive folder. If you are using your own local environment instead of Google Colab, follow [these instructions](https://docs.anaconda.com/ae-notebooks/user-guide/basic-tasks/apps/jupyter/index.html) for using the ipynb jupyter notebook file.

### Optional: Clone the Anvil App
To see how to develop your model into an Anvil app, first set up an account on Anvil.works, then use this [Clone Link](https://anvil.works/build#clone:W4S2YO3XG6UNFSKY=U2UZHBT5VNKJGANIBOU3UCR5) to create a clone of the app.


## Running the Analysis
To run the analysis, open the 'Gene_Cluster_App.ipynb' and execute all of the cells before the section "Run Model in Notebook". Once these cells finish, follow the directions in the last section to run the final cells.


## Using the Interactive Output

### Cluster info and warnings
The first part of the output contains printed statements describing the analysis results. Warning messages are covered in a following section.
![OutputInfo](https://github.com/umichhaidn/Gene_Cluster/blob/main/readme_images/output1.png)

### Graphs
The output contains two graphs. To start, both graphs will contain the entirety of your data. The lefthand graph displays the temporal expression patterns of your genes. The righthand graph uses UMAP diminsionality reduction to display a 2-dimensional projection of each of your data points. Essentially, each line in the lefthand graph has a corresponding point on the righthand graph. Use this to get an idea of how well a given cluster is performing.
![OutputGraphs](https://github.com/umichhaidn/Gene_Cluster/blob/main/readme_images/output2.png)

### Selectors
These selectors are used to filter the graphs. The 'Cluster' selector allows you to page through the various clusters and see which patterns are present and how well they cluster. If you are interested in a specific gene, navigate to that gene in the 'Gene' selector. This will display that gene's corresponding cluster id, which you can then find in the 'Cluster' selector.
![OutputSelectors](https://github.com/umichhaidn/Gene_Cluster/blob/main/readme_images/output3.png)


## Warnings
Under certain circumstances, your model output may generate a warning. This happens when your clusters meet criteria that suggest they might require attention. Below are descriptions of each warning and suggestions on further action.

### Warning: Some of your clusters contain very few members. You may want to check for outliers in your data or increase your distance threshold (t_value)
This warning means that some of yoru clusters contain fewer members than 1/1000th of your sample. This may simply indicate that you chose too strict of a distance threshold. Try running the model again with a larger t-value.

### Warning: You have both very large and very small clusters. This could indicate a lot of noise in your data, or that your data is not suitable for clustering. Consult the ReadMe file for suggestions
This warning happens with data where a large portion of data points fall into a few clusters, and the rest tend to form their own very small clusters. In this case, the large clusters and small clusters may need to be evaluated separately. Consider downloading the labeled file, cutting the large clusters into their own file, then running the analysis again on the isolated datasets.

### "Warning: A single cluster contains at least a third of your data points. Consult the ReadMe file for suggestions
This warning occurs when a large portion of your data falls into a single cluster. If you have only a handful of clusters, this may be fine. But if you have a lot of smaller clusters as well, this could indicate a few things. 
First, the large cluster may represent a single, dominant pattern. This is more likley if you used a low t-value.
Second, the large cluster may represent noise. This is more likely if you used a high t-value.
Third, the large cluster may represent the presence of a number of interesting patterns, and the small clusters may represent noise. This is more likely with intermediate t-values. If this is the case, consider using the next cell to clean noisy data.


## Cleaning Noise
If your results contain a lot of very small, and uninteresting clusters, you can run the cell used to clean out this noise. This cell makes a copy of your labeled data, then removes any row that belongs to a cluster with fewer than 'noise_threshold' members. By default, this threshold is set to 10, so any cluster of 10 or less are eliminated. You can change this threshold for stricter or more permissive cleaning.


## Downloading the labeled file
If you would like to download the labeled data back into CSV files, you can use the last two cells. Select a path where you want the new file to be located, and remember to give it a unique name as the last part of the path. The first of these cells downloads your original data with cluster labels. The second cell downloads your noise-cleaned data (if you ran that cell).


## Using the model in an Anvil App
This section is intended for users who wish to use this model in the form of a guided app. Once you have set up your Anvil.works account and cloned the app as per the setup directions, follow these steps to link your notebook to your clone app.

### Establish Uplink connection between Notebook and App
On Anvil.works, navigate to you the 'My Apps' section and select your cloned app. This should be something like "Clone of Gene_Cluster". 

Once open select the three-cubes icon in the upper left to open the app browser.
![AppBrowser](https://github.com/umichhaidn/Gene_Cluster/blob/main/readme_images/output4.png)

In the app browser, select the gear icon to open the app menu.
![AppMenu](https://github.com/umichhaidn/Gene_Cluster/blob/main/readme_images/output5.png)

In the app menu, select Uplink.
![Uplink](https://github.com/umichhaidn/Gene_Cluster/blob/main/readme_images/output6.png)

Click on the green "Enable the Anvil Server Uplink for the app" button. Then copy the uplink key.
![UplinkKey](https://github.com/umichhaidn/Gene_Cluster/blob/main/readme_images/output7.png)

Finally, open the Gene_Cluster_App.ipynb you downloaded. Under the section "Set Up Anvil Uplink", paste your uplink key where indicated.
![PasteKey](https://github.com/umichhaidn/Gene_Cluster/blob/main/readme_images/output8.png)

### Running the App
Back on Anvil.works, click the "Run" button at the top of the Gene Cluster app and follow the directions to run the model.

### Note on Anvil Limitations
At the time of development for this app, the iFrame component (component where Alair chart is displayed) is more limited in how it displays media than other methods of rendering. If you notice that your model seems to complete, but no graphs are displayed, try reducing your sample size.