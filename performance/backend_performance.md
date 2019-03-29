# How to approach backend performance measurement task
This guideline describes the steps you can approach a backend performance measurement task.

## Step 1: Add measuring codes to log performance data



There are three important attributes to be logged:
- Waiting (TTFB)   
The browser is waiting for the first byte of a response. TTFB stands for Time To First Byte. This timing includes 1 round trip of latency and the time the server took to prepare the response.   
Tool to record: Chrome DevTool, Firefox DevTool.   
Reference: https://developers.google.com/web/tools/chrome-devtools/network/reference#timing-explanation

- Backend's cost   
This is the time-taken which backend need to handle one request.

- Critical functions   
The critical functions take the largest proportion in the backend processing. Your task is much easier if you can find a tool allowing to point out the critical functions. If not, you have to add measuring code in functions and keep doing it until you found out the critical functions.

## Step 2: Collect the data
- Collect data in a table as follows:
![](images/2019-03-28-15-31-52.png)

## Step 3: Present insights from performance data
Present insights from the performance data:   

- Expensive functions:   
`Pie chart` is the best chart type to represent proportion data.

![](images/2019-03-28-15-26-28.png)

![](images/2019-03-28-15-31-08.png)

- Data varies:
In real cases, the critical function's time-taken often varies. You should represent it as `Scatter` chart.  

![](images/2019-03-28-15-33-18.png)