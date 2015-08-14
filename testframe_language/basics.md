## Basic TFL features

### Action words

An action word is a unique identifier that represents a specific action that is to be performed. There can be only one action word on a cluster line, and this action word has to be in a specific argument of that line - the first one. The exception to this is when the Engine operates in Master mode, then the action word should be in the second argument.

### User  defined action words

A user defined action word is an action word that indicates that the test executioner must perform a specific action. In case of automated testing this means some piece of software associated with this action word is to be executed - this is called the action word function.

### Built-in action words

A built-in action word is an action word that indicates that the Engine itself has to perform an action. 
A complete list of all built-in action words can be found in chapter 6.

### Action word parameters

Action words can be parameterized. These parameters are placed in arguments after the action word. By using parameters, actions that are similar but use different data, can be indicated by the same action word with different parameter values.

### Test lines

A test line comprises the cluster lines which contain an action word and its parameters - including the tab and newline characters. 

