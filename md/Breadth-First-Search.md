# BREADTH-FIRST-SEARCH

## AIMA4e

__function__ BREADTH-FIRST-SEARCH(_problem_) __returns__ a solution, or failure  
&emsp;__if__ problem's initial state is a goal __then return__ empty path to initial state  
&emsp;_frontier_ &larr; a FIFO queue initially containing one path, for the _problem_'s initial state  
&emsp;_reached_ &larr; a set of states; initially empty  
&emsp;__while__  _frontier_ is not empty __do__  
&emsp;&emsp;&emsp;_path_ &larr; the first path in _frontier_  
&emsp;&emsp;&emsp;_parent_ &larr; the last node in _path_  
&emsp;&emsp;&emsp;__for__ _child_ __in__ successors(_parent_) __do__   
&emsp;&emsp;&emsp;&emsp;&emsp;_s_ &larr; _child_.state  
&emsp;&emsp;&emsp;&emsp;&emsp;__if__ _s_ is a goal  __then__  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;__return__  _path_  
&emsp;&emsp;&emsp;&emsp;&emsp;__if__ _s_ is not in _reached_ __then__  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;add _s_ to _reached_  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;add _child_ to the end of _path_  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;add _path_ to the end of _frontier_  
&emsp;__return__  _None_

---
__Figure 3.9__ Breadth-first search algorithm.


## AIMA3e
__function__ BREADTH-FIRST-SEARCH(_problem_) __returns__ a solution, or failure  
&emsp;_node_ &larr; a node with STATE = _problem_.INITIAL\-STATE, PATH\-COST = 0    
&emsp;__if__ _problem_.GOAL\-TEST(_node_.STATE) __then return__ SOLUTION(_node_)  
&emsp;_frontier_ &larr; a FIFO queue with _node_ as the only element  
&emsp;_explored_ &larr; an empty set  
&emsp;__loop do__  
&emsp;&emsp;&emsp;__if__ EMPTY?(_frontier_) __then return__ failure  
&emsp;&emsp;&emsp;_node_ &larr; POP(_frontier_) /\* chooses the shallowest node in _frontier_ \*/  
&emsp;&emsp;&emsp;add _node_.STATE to _explored_  
&emsp;&emsp;&emsp;__for each__ _action_ __in__ _problem_.ACTIONS(_node_.STATE) __do__  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;_child_ &larr; CHILD\-NODE(_problem_,_node_,_action_)  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;__if__ _child_.STATE is not in _explored_ or _frontier_ __then__  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;__if__ _problem_.GOAL\-TEST(_child_.STATE) __then return__ SOLUTION(_child_)  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;_frontier_ &larr; INSERT(_child_,_frontier_)  

---
__Figure__ ?? Breadth\-first search on a graph.
