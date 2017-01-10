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


This entire document is written with the RST syntax. In the right sidebar, you should find a link **show source**, which shows the RST source code.