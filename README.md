#ECE2112 Programming Assignment 3

**By: Leye Quillo, 2 ECE-B**

#Introduction 
This repository is about a programming assignment in full detail of the problems and the solutions made done by the author. The goal is for the author to understand the uses of programming techniques such as slicing, finding the location of certain cells, and subsetting. This is to further strengthen the author's foundation of coding knowledge throughout the School Year 2026-2027.

#Preparation
These commands were used to execute these codes:
1. "Import pandas as pd" - A command used to import and loads the Pandas library into your Python script and assigns it the standard shortcut alias. Gives you access to its core data structures like DataFrames and Series.
2. "pd.read_csv" - A command used to read files that are uploaded in the notebook. As the file gets read by the code, it will be put in the code/program interface. For this situation, "cars.csv" was uploaded by the author in the notebook and in order to display it in the code, the command was used.

# Problem 1 - POSITIONAL AND LABEL-BASED SLICING
After loading cars, complete the following operations.
a. Display the shape and complete list of column names of cars.
b. Using positional slicing, create cars 6 to 10 containing rows 6 through 10 of the dataset, where
the first data row is row 1.
c. From cars 6 to 10, display only the columns Model, mpg, cyl, hp, and gear, in that order.
Requirement: The row selection in part (b) must use iloc; the column selection in part (c) must
use column labels.

print("Shape:", cars.shape) - Accesses the .shape attribute to return the overall dimensions of the DataFrame as a (rows, columns) tuple.

print("Column names:", cars.columns.tolist()) - Converts cars.columns (a Pandas Index object) into a native Python list. 

cars_6_to_10 = cars.iloc[5:10] - Applies integer-location indexing using zero-based position bounds. The slice 5:10 extracts row index positions 5, 6, 7, 8, and 9, which correspond to dataset rows 6 through 10 (5 total records).


Shape & Columns: Used cars.shape and cars.columns.tolist() to output DataFrame dimensions and list column headers.

Positional Slicing: Applied 0-based integer slicing via cars.iloc[5:10] to capture 1-based rows 6 to 10 (indices 5 through 9).

Column Selection: Passed a list of requested column labels to select the target subset.

# Problem 2 - MODEL LOOKUP
Use Boolean indexing on the Model column to answer both requests.
a. Display the complete row for Toyota Corolla.
b. For Pontiac Firebird, display only Model, mpg, hp, and wt.
Store the two results in toyota and pontiac, respectively. Do not use a hard-coded row number to
locate either model.

toyota = cars[cars['Model'] == 'Toyota Corolla'] - cars['Model'] == 'Toyota Corolla' across the entire column to generate a 1D Series of Boolean flags. Passing this mask into cars[...] filters out all False rows.

pontiac = cars[cars['Model'] == 'Pontiac Firebird'][['Model', 'mpg', 'hp', 'wt']] - Combines row filtering and column selection into a single sequential operation. The first bracket expression isolates the matching row, while the second bracket selects only the specified columns.

[['Model', 'mpg', 'hp', 'wt']] - Uses nested outer brackets containing a list of strings inside the indexing operator. This forces it to return the output as a 2D DataFrame structure instead of collapsing it into a 1D Series.


Created dynamic Boolean masks (cars['Model'] == <Model_Name>) to select exact matching rows without relying on static row indices.

Applied label-based column sub-indexing directly on the filtered output for pontiac.

# Problem 3 - MULTI-MODEL SUBSETTING
Create a DataFrame named selected cars containing only the records for three models: Datsun 710,
Lotus Europa, and Ferrari Dino.
For these records, retain only Model, mpg, cyl, hp, and gear. Select the rows by their model values
rather than by row numbers. Display selected cars and its shape.
Required check: The final DataFrame must contain exactly three rows and five columns.

cars['Model'].isin(selected_models) - Replaces multiple OR (|) conditions with .isin(), evaluating whether each value in the Model column exists within the selected_models array.

selected_cars = cars[cars['Model'].isin(selected_models)][selected_columns] - Executes row membership matching via .isin() and column projection via a target column list (selected_columns).


Passed a target list of models into cars['Model'].isin(...) for multi-condition row matching.

Applied column filtering using double-bracket indexing with the target column list.



===END===
