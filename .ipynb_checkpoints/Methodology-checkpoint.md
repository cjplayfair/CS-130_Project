# Methodology of my Drug Analysis
## Data Source
[Substance Abuse by State and Age](https://corgis-edu.github.io/corgis/csv/drugs/)
## Data Preparation/Cleaning
- Data from the above link was turned into a pandas dataframe for faster analytical operations
- In preparation of using the data provided in the above link, the first operation performed was to strip any column containing strings to make sure there were no new lines.
- From there, if the column was found to be a string, I performed the pandas to_numeric() to turn all of the data I would be using into numeric values. This would allow for mathematical operations to be performed on the data.
- To make data from each state more accessible instead of reading from one data frame, every state was taken and turned into their own dataframes. If the column was matched with the desired state (i.e. New York was found in the column of the data), that specific state's years and data would be put into its own dataframe.
- In each state's individual dataframe, the following columns were taken to be performed for data analysis: ''Rates.Alcohol.Use Disorder Past Year.12-17', 'Rates.Alcohol.Use Disorder Past Year.18-25', 'Rates.Alcohol.Use Disorder Past Year.26+', 'Rates.Tobacco.Cigarette Past Month.12-17', 'Rates.Tobacco.Cigarette Past Month.18-25', 'Rates.Tobacco.Cigarette Past Month.26+', 'Rates.Illicit Drugs.Cocaine Used Past Year.12-17', 'Rates.Illicit Drugs.Cocaine Used Past Year.18-25', 'Rates.Illicit Drugs.Cocaine Used Past Year.26+', 'Rates.Marijuana.Used Past Year.12-17', 'Rates.Marijuana.Used Past Year.18-25', 'Rates.Marijuana.Used Past Year.26+', 'Rates.Tobacco.Use Past Month.12-17', 'Rates.Tobacco.Use Past Month.18-25', 'Rates.Tobacco.Use Past Month.26+'
- Each state's dataframe would have the astype() function performed to make sure all the data from that point forward would be float datatype, so that there was never a datatype mismatch.
- Each state's dataframe would have the index set to 'Year' so that during data analysis, the data would be matched up for operations against New York's data
- Every state's dataframe, except for New York (as it is the state we will perform the analysis against) was put into a dictionary, which would allow for quick division calculation against New York.
- In a for loop, by performing the div() function against New York's dataframe, every state's rates of substance abuse could be divided against New York's substance abuse rates. From there, a new dictionary could be created that had all these comparisons for each state. The division meant that if a state's value for a specific substance at a specific year was greater than 1.0, it meant that state's rate was higher than New York's. Less than 1.0 meant it was lower, and exactly 1.0 meant it had the exact same rate as New York's.
- The data could then be put into a "master" dataframe so that all the data from the dictionary that had all the new rates could be put into a dataframe, which would allow for matplotlib plots to be made against the newfound data.
## Assumptions
- This analysis assumes that over the period from 2002 to 2018, the way data was collected did not drastically change
- Since the data was compared against New York from every state, I assume in the data analysis that residents in other states answered surveys with the same level of honesty and at the same response rates as residents in New York
- Since substance abuse is historically underreported and comparing the rates, I am assuming that other states aren't significantly more or less likely to lie on a survey about druge use than people in New York
- This data analysis assumes New York as the main standard for drug rates, and assumes that drug trends in New York do not spill over to other neighboring states, treating them as independent data points when drug chains are regional
## Limitations
- It was discovered early on that not every substance's rates had the same timeframes. For example, a lot of the drugs like alcohol, cocaine and marijuana had a past year rate, but cigarettes and tobacco only had a past month rate. This meant that for some drugs, the comparison would be made past off monthly rates, whereas others would be made off of yearly rates.
- The only years that were featured in the data analysis were from 2002 to 2018, which excludes years up to the present as well as any years before 2002.
