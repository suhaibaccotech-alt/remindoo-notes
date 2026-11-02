###Clients Table

Text (Single)
~~~
"is" should include the exact text added
"is not" should exclude the exact text added
"is known" should include all non-empty values
"is not known" should include null values only
~~~
Text (List)
~~~
"Is one of" should include the values added in the list of text
"Is not one of" should exclude the values added in the list of text
"Is known" should include all non-empty values
"is not known" should include null values only
~~~
Number
~~~
"is" should include the exact number added
"is not" should exclude the exact number added
"is known" should include all non-empty values
"is not known" should include null values only
~~~
Date
~~~
"Is on" should include values that match the selected date
"Is not on" should include values that do not match the selected date
"During" should include values within the date range selected (Additional, once requested by sir waqas)
"Is known" should include all non-empty values
"is not known" should include null values only
~~~
Dropdown
~~~
"Is one of" should include the values selected from the multi-dropdown
"Is not one of" should exclude the values selected from the multi-dropdown
"is known" should include all non-empty values
"is not known" should include null values only
~~~
Assignees 
~~~
"Any" should include all of the options that include any of the assignees selected
"Are" should include the exact list of assignees selected 
"Is" should include the single assignee selected
~~~

