**Author**: Swetha Yadavalli

**Programming Language**: Python

**Dependencies**:
- pandas
- numpy
- scipy.optimize

**Files required**:
- DecayTimecourse.txt

## Description

This script involves the calculation of the transcript half lives for the yeast genes using the 60 minute time series data and calculate the average of the three calculated half lives for each transcript. It also identifies the genes/transcripts with very high (top 10%) and very
low (bottom 10%) half lives. 

## Execution Steps

1. Import the necessary libraries initially. 
2. Define the file path and provide the path of the file. Start by reading the txt file from the second line with the data. 
3. As the first column is not the data, extract the time courses separately from the actual data frames. The first 10 columns is the first time course, the other ten are the second time course and the last ten are the third time course. 
4. Next drop the rows which have the NaN in the second column, as the absence of the expression level in the first time-point is the same as the absence of the expression levels in any other time points. 
5. Then, apply linear interpolation to each time course DataFrame to fill in any remaining NaN values.
6. Next, define the half_life function, which computes the half-life of a gene's expression decay using an exponential decay model. It first applies curve_fit to the decay model before calculating the half-life.
7. Then, define the calculate_half_lives function, which iterates through each row of a time course DataFrame, calculates the half-life of each gene, and stores the results in a list.
8. Apply the calculate_half_lives function to each time course dataFrame to get a list of half-lives for each gene.
9. Then, create a new dataFrame by merging the half lives of the three time-course with columns including 'YORF' (gene names) and the calculated half-lives for the three time courses. 
10. Then calculate the average half life for the three time courses for each gene. 
11. Sort the merged DataFrame by average half-life in descending order and calculate the top 10% of genes based on the highest average half-lives.
12. Sort the merged DataFrame by average half-life in ascending order and calculate the bottom 10% of genes based on the lowest average half-lives.


