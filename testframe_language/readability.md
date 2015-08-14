## Improving cluster readability

### Empty lines

Empty lines can be added to a cluster - before or after any one or any group of test lines, as many as desired, and distributed throughout the cluster as desired. In terms of characters, an empty line is no more than an extra newline character in the cluster file.

### Comment lines

TFL offers the possibility to add comment lines to a cluster. For comment lines the action word column must be empty; except for Master/Slave configurations, this is the first column.

### Argument descriptions

Comment lines can contain descriptions of the action word arguments. The Engine offers functionality to store and retrieve these argument descriptions. It should be noted that this functionality is limited. Since the argument descriptions are not explicitely registered to a specific action word, determining them is a matter of interpretation for the Engine. To avoid misinterpretation, the comment line containing the desired argument descriptions should be the last comment line before the line(s) whose corresponding action word function(s) call these descriptions.

2.3.4	Splitting test lines
TFL offers the possibility to split a test line over several cluster lines. To do this, the continue token must be used. The continue token can be set to any value by adding it to the ini file containing the Engine’s settings—to the key ContText in the section SYSTEM. The default value for the continue token, however, is &Cont.

The continue token must be placed in the argument following the last one of each broken-off cluster line and in the first argument of each continued cluster line. 

Example 2.1
The following cluster demonstrates the continue token.
	
|	1	| 2  | 	3	|  4  |  5  |
| -- | -- | -- | -- | -- |
| 1  | check names	| John    | Sue     | &Cont |
| 2	 | &Cont	    | Betty	  | Steve	| &Cont |
| 3	 | &Cont	    | Angela  |         |       |

	
Note that this test line has six arguments - the first being the action word itself - and the argument with index number 4 (the third parameter of the action word) contains the value Betty.
