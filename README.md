# Programming-Assignment-4

#### Before anything else, import the pandas library *import pandas as pd* since it will be used in all problems. We will also use Matplotlib *import matplotlib.pyplot as plt* but **only in Problem 2** for the charts. Then load and display the data.

 **Code**

     import matplotlib.pyplot as plt #import the Matplotlib library as 'plt'
     import pandas as pd #import the pandas library as 'pd'

     bd = pd.read_csv ('board2.csv') #Read a CSV file into a pandas DataFrame
     bd #print
     
 **Output**
  
  <img width="903" height="727" alt="image" src="https://github.com/user-attachments/assets/7ca6c41e-e759-451b-a7d1-911913f69e77" /><br/>
  <img width="903" height="690" alt="image" src="https://github.com/user-attachments/assets/67d26211-851d-4ecd-962f-aac6b957415e" /><br/>
  <hr/>

### Problem 1
a. Filters the table to Instrumentation students from Luzon with Electronics > 70, then shows only their Name, GEAS, and Electronics.

 **Code**

      bd.loc [(bd['Track'] == 'Instrumentation') & # keep only Instrumentation track
       (bd['Hometown'] == 'Luzon') & # also keep only that are from Luzon
       (bd['Electronics'] > 70), # And also the ones with Electronics greater than 70 only
       ['Name', 'GEAS', 'Electronics']] # show only these columns
       
 **Output**

  <img width="315" height="172" alt="image" src="https://github.com/user-attachments/assets/4b1292ba-9574-4da8-aed5-858fe7ba36a3" /><br/>
  <br/>

b. Creates an Average per student (mean of Math, Electronics, GEAS, Communication), then keeps female students from Mindanao with Average ≥ 55 and shows Name, Track, Electronics, and Average.<br/>

**Code**

     bd['Average'] = bd[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1) #compute the average of all the subjects per examinee and then add it as a new column

     bd.loc [(bd['Gender'] == 'Female') & # keep only female students
       (bd['Hometown'] == 'Mindanao') & # also keep only that are from Mindanao
       (bd['Average'] >= 55), # And also the ones with the Average of greater than or equal to 55 only
       ['Name', 'Track', 'Electronics', 'Average']] #show only thhese columns


 **Ouput**

  <img width="498" height="268" alt="image" src="https://github.com/user-attachments/assets/b6495cf0-8a4b-4c9e-92df-ee63ceffaa55" /><br/>
  <br/>

 **Conclusion**<br/>
     In conclusion, this pandas program filtered the dataset into two subsets using conditional selection with .loc[]. For the first part, I selected only those students whose Track is Instrumentation, Hometown is Luzon, and with Electronics greater than 70, then displayed their Name, GEAS, and Electronics. For the second part, I first created a new column Average by computing the mean of Math, Electronics, GEAS, and Communication for each student. I then filtered the data to keep only female students from Mindanao with an Average ≥ 55, showing their Name, Track, Electronics, and Average.   
  

<hr/>

### Problem 2
A visualization that shows how the different features contributes to average grade. Does chosen track in college, gender, or hometown contributes to a higher average score?<br/>
<br/>
  a. Average by Track: Groups by track and draws a bar chart of the mean Average for each track.<br/>

**Code**

    bd['Average'] = bd[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1) #compute the average of all the subjects per examinee and then add it as a new column

    avg = bd.groupby('Track')['Average'].mean() # Compute the mean or 'Average' for each Track
    
    plt.bar (avg.index, avg.values, color = ['skyblue', 'salmon', 'bisque']) # Draw one bar per Track using its mean and also assign custom colors (order follows avg.index)
    plt.title('Average by Track') # Add title to the chart
    plt.ylabel('Mean') # Label the y-axis to show mean values
    plt.xlabel('Tracks') # Label the x-axis to show the categories
    plt.show() # display

**Output**

  <img width="852" height="672" alt="image" src="https://github.com/user-attachments/assets/8bac2145-5e91-4d58-afac-1d2965762ef7" /><br\>
  <br/>
  <br/>

  b. Average by Gender: Groups by gender and draws a bar chart of the mean Average for each gender.

**Code**

    avg = bd.groupby('Gender')['Average'].mean() # Compute the mean or 'Average' for each Gender

    plt.bar (avg.index, avg.values, color = ['skyblue', 'salmon', 'bisque']) # Draw one bar per gender using its mean and also assign custom colors (order follows avg.index)
    plt.title('Average by Gender') # Add title to the chart
    plt.ylabel('Mean') # Label the y-axis to show mean values
    plt.xlabel('Gender') # Label the x-axis to show the categories
    plt.show() # display

**Output**

  <img width="840" height="660" alt="image" src="https://github.com/user-attachments/assets/054a2141-a20e-43c2-b678-c0586ff5c2a8" /><br/>
  <br/>

  c. Average by Hometown: Groups by hometown and draws a bar chart of the mean Average for each region.<br/>

**Code**

    avg = bd.groupby('Hometown')['Average'].mean() # Compute the mean or 'Average' for each Hometown
    
    plt.bar (avg.index, avg.values, color = ['skyblue', 'salmon', 'bisque']) # Draw one bar per gender using its mean and also assign custom colors (order follows avg.index)
    plt.title('Average by Hometown') # Add title to the chart
    plt.ylabel('Mean') # Label the y-axis to show mean values
    plt.xlabel('Hometown') # Label the x-axis to show the categories
    plt.show() # display

**Output**

  <img width="848" height="666" alt="image" src="https://github.com/user-attachments/assets/0dec699c-4014-417f-bd64-c140559f05f3" /><br/>
<br/>
    
**Conclusion**

In conclusion, this pandas and Matplotlib program computed an Average column from the four subjects and then used groupby() with bar charts to compare mean scores by track, gender, and hometown. The results showed that the Communication track had the highest overall average, Luzon students scored slightly higher than those from Visayas and Mindanao, and the difference between male and female students was very minimal. These visualizations demonstrate how pandas can be used for summarizing data and Matplotlib for presenting clear comparisons, making it easier to see how different features contribute to variations in average performance.
