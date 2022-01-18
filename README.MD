
**********  Implementation of Gaussian Process with Linear and RBF kernel Report - README file  **********

**Datasets: csv files**

There are currently 4 different categories of data. Each having training features, training labels, testing feature and testing labels. These datasets are -

* crime dataset
* artsmall dataset
* housing dataset
* 1D dataset

Except 1D dataset, all other the train and test feature datasets contain number of feature values in each line.

*1D dataset contains only one feature column in train and test set.*

**Data Format:**

feature dataset ::

```
-0.37509	0.95613	   -0.23422		.	.	-0.68813 . . . . .
-0.29631	-0.02099	0.341426	.	.	-0.68813 . . . . .
	.			.			.		.	.	.
	.			.			.		.	.	.
-0.45387	-0.8149	   -0.62968		.	.	-0.842383 . . . . .
```

label dataset ::

```
-0.459683
0.833985
	.
-0.795076
	.
3.277538
	.
	.
```

**Code Execution Process :** 

* The entire solution is developed in jupyter notebook.
* The ipynb file is kept in a directory and there is a sub-directory called 'pp4data' which contains all the input data files.
* The jupyter notebook contains multiple defined functions as below -
	* read_files(file_name) -  to read input data files
	* get_RBF_Kernel(phi1,phi2,s) -  to calculate Kernel matrix for RBF on train dataset
	* GP_Optimization(phi_train,phi_test,t_train,t_test,kernel,inp) - Model selection and optimization for both the Linear and RBF kernel
	 * get_Prediction(phi_train,phi_test,t_test,alpha,beta,s,kernel) - to predict c and V for test data set
	 * get_Mean_Variance_MSE_MNLL(c,V,C_N_updated,t_train,t_test,inp) - to predict mean, variance, MSE and MNLL on test dataset
	 * plot_MNLL_vs_TrainIter(MNLL_List,Train_Iter,k) - to create the required plots of MNLL as a function of training iterations
	 * plot_Performance_1D(Mean,Var,k) - Visualizing performance on the 1D dataset and plot of mean with +/-2 sd around the mean

* The GP_Optimization() function sets the value for s as 0.1 for 1D dataset else 5 itself and the plot_Performance_1D() function to Visualise the performance on the 1D dataset only gets called if the input dataset is 1D.
* The complete program is written in a single cell with main() function at the end and other user defined functions above. The main() function takes the input selection from user as it prompts to give a data set selection option.
* All the csv input files automatically get detected in the 'pp4data' directory and asks the user to chose which dataset to execute through the prompt.

**Input :**

* Enter 1 for 1D
* Enter 2 for housing
* Enter 3 for artsmall
* Enter 4 for crime

The user selects either of 1/2/3/4 as per their choice of data set and the program proceeds with the selected train, test of feature and labels data set to read it from the directory 'pp4data' and process for the given tasks.

**Output:**

*The below tasks and outputs are generated for both the Linear and RBF kernel*

For Task - GP Optimization

 * This task does the predictive distribution, derivative and model selection by optimizing the parameters until convergence
	* Number of training iteration required to select optimal model
	* Finalised Alpha, Beta and s parameter ie the optimized hyper-parametric values

For Task - Evaluation of Mean and Variance Prediction with MSE and MNLL

 * This task uses the optimized hyper-parameters and predicts the mean and variances of the test data set. With the predicted values, it returns the Mean Squared Error(MSE) and Mean Negative Log Likelihood (MNLL) of the final prediction.
	* Final MSE of test data set
	* Final MNLL of test data set

For Task - Performance as a function of training iterations

 * This task computes the MNLL at every 10th iteration starting from 0 and including the final iteration where the algorithm stops
	* MNLL list with the values per training iteration
	* List of training iterations for performance plot
	* Plot of MNLL as a function of training iteration

For Task - Visualizing performance on the 1D dataset

 * This task just visualizes the true function values for the 1D dataset as it is given in the problem statement and the mean of the predictive distribution with +/-2 standard deviations around the mean. both the graphs are showed in a single plot-box.
 	* Plot of true function values
 	* Plot of the errorbars of Mean of predictive distribution with +/-2 SD




