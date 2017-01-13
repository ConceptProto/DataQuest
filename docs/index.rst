.. DataQuest data analyst documentation master file, created by
   sphinx-quickstart on Mon Jan 09 22:34:42 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to DataQuest: Data Analyst course notes!
==================================================

.. toctree::
   :maxdepth: 2
   :caption: Contents:



Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

Popular functions
#############
*type() - gives the type
*str() - converts to string
*int() - convers to integer
*.replace() - substitutes a word for another
*.lower() - converts all uppercase text to lowercase text

Lists
#############
*months = [] - initialise a list
*months.append('value') - Adds to the end of the list
*months = [1, "January", 2, "February"] - creating list with values
*months[0] - accessing values in list
*len(months) - returns the length of the list
*month_slice = months[2:4] - give the list items 2 and 3, not 4.
*split_list = g.split(",") - split the data in g into a list

Files
#############
*f = open("crime_rates.csv", "r") - open files
*g = f.read() - returns a string representation of a text in a file

shorthand:
*g = open("crime_rates.csv").read()


for loops
#############
for row in rows:
	do something

list of lists
#############
three_rows = ["Albuquerque,749", "Anaheim,371", "Anchorage,828"]
final_list = []
for row in three_rows:
    split_list = row.split(',')
    final_list.append(split_list)

If you have a list of lists
	* first_element = data[0] will first give you the list (from the list of lists) for whatever is in that list - it may be a couple of items
	* first_element[0] will give you the first item in the list
	* shorthand: data[0][0]

To get a list of lists from a csv:
Long way - 

f = open('dq_unisex_names.csv', 'r')
names = f.read()
names_list = names.split('\n')

nested_list = []
for element in names_list:
    comma_list = element.split(',')
    nested_list.append(comma_list)
    
print(nested_list[0:5])

short way -

import csv

f = open("world_alcohol.csv")
reader = csv.reader(f)
world_alcohol = list(reader)


Booleans
#############

Booleans help you to filter data according to specified criteria:
	* == returns True if both variables are equivalent, and False if they're different
	* != returns True if both variables are different, and False if they're equivalent

Use parentheses for cleaner code.
t = (8 == 8) # True

Remember that when using len() to retrieve the last element from a list you should subtract 1:
crime_last = crime[len(crime) - 1]
The length of the list is does not specify the last element in the list as the list index begins at 0.

If Statements
#############
if value > 500:
	do something

If Else Statements
#############
if temperature > 50:
    print("It's hot!")
else:
    print("It's cold!")

In Statement
#############
The Instatement checks of there is a specific element in a list

animals = ["cat", "dog", "rabbit"]
if "cat" in animals:
    print("Cat found")

Or assign to a variable

animals = ["cat", "dog", "rabbit"]
cat_found = "cat" in animals

The In statement can also check to see if there is a specific key in a dict

students = {
    "Tom": 60,
    "Jim": 70
}

"Tom" in students will return True

Dictionaries
#############
scores = {} - initialise a dictionary
Stupid way: scores["Tom"] = 70 - Will assign "Tom" with a score of 70. "Tom" is the index of the dict.
Clever way:

students = {
    "Tom": 60,
    "Jim": 70
}

This gives us key/value pairs

Functions
#############
def clean_text(string_value):
    cleaned_value = string_value.replace(",", "")
    return(cleaned_value)
sentence = "Howdy,james,bond!"
sentence = clean_text(sentence)

NumPy
#############
NumPy gives you the ability to work with multidimensional arrays.
e.g. a table where table 2,2 gives you the value at row 2, column 2.

import numpy
nfl = numpy.genfromtxt("nfl.csv", delimiter=",")

generate an array:
matrix = numpy.array([[5, 10, 15], [20, 25, 30], [35, 40, 45]])

find the shape of an array:
matrix.shape OR vector.shape

type of an array:
numbers.dtype

* a numpy array has to be of the same type
* numpy will convert all of the leements in the array to a type it guessed.
* elements that can't be converted to the selected type will be NaN 0 Not a Number
* missing elements will resolve to na - Not Available

To specify that the genfromtxt() function should read in the data as string:
import numpy
world_alcohol = numpy.genfromtxt('world_alcohol.csv', delimiter=",", dtype='U75', skip_header=1)
print (world_alcohol)

#slice vectors and lists the same
*indexing (getting the element) for vectors and lists are the same

To get the entire column (slicing) from an array
countries = world_alcohol[:,2]

To get a matrix from a matrix
matrix = numpy.array([
                    [5, 10, 15], 
                    [20, 25, 30],
                    [35, 40, 45]
                 ])
print(matrix[:,0:2])

[
    [5, 10],
    [20, 25],
    [35, 40] 
]

This specifies that the matrix should include column 0 to 3, but excluding column 3 (and all the rows)

Array comparisons:
vector = numpy.array([5, 10, 15, 20])
vector == 10

numpy will compare 10 to each value in vector and build a new vector with True/ False values.
e.g
[False, True, False, False]

Select a row or column from an array or matrix according to specified criteria
matrix = numpy.array([
                [5, 10, 15], 
                [20, 25, 30],
                [35, 40, 45]
             ])
    second_column_25 = (matrix[:,1] == 25)
    print(matrix[second_column_25, :])












Recipes
#############
Open a file and read in each row into a list of lists

f = open("la_weather.csv", 'r')
data = f.read()
rows = data.split('\n')
weather_data = []
for row in rows:
    split_row = row.split(",")
    weather_data.append(split_row)

Counting frequency in a dict
pantry = ["apple", "orange", "grape", "apple", "orange", "apple", "tomato", "potato", "grape"]

pantry_counts = {}
for element in pantry:
    if element in pantry_counts:
        pantry_counts[element] = pantry_counts[element] + 1
    else:
        pantry_counts[element] = 1

a function to read a csv, split the string ('\n'), converts the elements in the list (of lists) to integers.

def read_csv(filename):
    data = open(filename).read()
    data_split = births_data.split("\n")
    string_list = data_split[1:len(data_split)-1]
    
    final_list = []
    for element in string_list:
        int_fields = []
        string_fields = element.split(",")
        for elmnt in string_fields:
            int_fields.append(int(elmnt))
        final_list.append(int_fields)
    return (final_list)
    
cdc_list = read_csv("US_births_1994-2003_CDC_NCHS.csv")
print (cdc_list[0:10])

function to retrieve the frequency from a list of lists for a specific column
def calc_counts(data, column):
    column_total = {}
    for element in data:
        chosen_column = element[column]
        birth_column = element[4]
        if chosen_column in column_total:
            column_total[chosen_column] = column_total[chosen_column] + birth_column
        else:
            column_total[chosen_column] = birth_column
    return (column_total)

convert the second element in the list of 2 elements to a numerical value
temp_list = []
numerical_list = []

#print (nested_list[0][1])

for element in nested_list:
#    print (element)
    first_element = element[0]
    second_element = float(element[1])
    temp_list.append(first_element)
    temp_list.append(second_element)
    numerical_list.append(temp_list)
    temp_list = []

Get the second column from a list
weather = []
for element in weather_data:
    weather.append(element[1])

counting the number of unique values in a list
pantry = ["apple", "orange", "grape", "apple", "orange", "apple", "tomato", "potato", "grape"]

pantry_counts = {}
for element in pantry:
    if element in pantry_counts:
        pantry_counts[element] = pantry_counts[element] + 1
    else:
        pantry_counts[element] = 1

Remember
#############
months = ["Jan", "Feb"]
print (months[0:1])

NOT

print (months)[0:1]

This entire document is written with the RST syntax. In the right sidebar, you should find a link **show source**, which shows the RST source code.