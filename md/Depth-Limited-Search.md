# DEPTH-LIMITED-SEARCH

## AIMA4e  

__function__ DEPTH-LIMITED-SEARCH(_problem_, _limit_) __returns__ a node or failure or cutoff  
&emsp;_frontier_ &larr; a LIFO queue (stack) with a node for the initial state    
&emsp;_result_ &larr; failure  
&emsp;__while__  _frontier_ is not empty __do__  
&emsp;&emsp;&emsp;_node_ &larr; POP(_frontier_)  
&emsp;&emsp;&emsp;__if__ DEPTH(_node_) > _limit_ __then__  
&emsp;&emsp;&emsp;&emsp;&emsp;_result_ &larr; cutoff  
&emsp;&emsp;&emsp;__else__  
&emsp;&emsp;&emsp;&emsp;&emsp;__for__ _child_ __in__ EXPAND(_problem_, _node_) __do__  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;__if__ _child_ is a goal __then__ __return__ _child_  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;__if__ __not__ ISSHORTCYCLE(_node_) __then__  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;add _child_ to the _frontier_  
&emsp;__return__  _result_  

---
__Figure 3.3__ Iterative deepening and depth-limited tree search. Iterative deepening repeatedly applies depth-limited search with increasing limits. It terminates when a solution is found or if the depth-limited search returns _failure_, meaning that no solution exists. The depth-limited search algorithm returns three different types of values: either a solution, or _failure_ when it has exhausted all nodes and proved there is no solution at any depth, or _cutoff_ to mean there might be a solution at a deeper depth than _limit_. Note that this is a tree search algorithm that does not keep track of _reached_ states, and thus uses much less memory that best-first search, but it runs the risk of visiting the same state multiple times on different paths, and failing to be systematic. To partially counter that, the ISSHORTCYCLE(CHILD) test looks at the parent and several generations of grandparents to see if a cycle is detected, and if so refuses to put the offending child on the frontier.

## AIMA3e
__function__ DEPTH-LIMITED-SEARCH(_problem_,_limit_) __returns__ a solution, or failure/cutoff  
&emsp;__return__ RECURSIVE\-DLS(MAKE\-NODE(_problem_.INITIAL\-STATE),_problem_,_limit_)  

__function__ RECURSIVE\-DLS(_node_,_problem_,_limit_) __returns__ a solution, or failure/cutoff  
&emsp;__if__ _problem_.GOAL-TEST(_node_.STATE) __then return__ SOLUTION(_node_)  
&emsp;__else if__ _limit_ = 0 __then return__ _cutoff_  
&emsp;__else__  
&emsp;&emsp;&emsp;_cutoff\_occurred?_ &larr; false  
&emsp;&emsp;&emsp;__for each__ _action_ __in__ _problem_.ACTIONS(_node_.STATE) __do__  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;_child_ &larr; CHILD\-NODE(_problem_,_node_,_action_)  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;_result_ &larr; RECURSIVE\-DLS(_child_,_problem_,_limit_\-1)  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;__if__ _result_ = _cutoff_ __then__ _cutoff\_occurred?_ &larr; true  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;__else if__ _result_ &ne; _failure_ __then return__ _result_  
&emsp;&emsp;&emsp;__if__ _cutoff\_occurred?_ __then return__ _cutoff_ __else return__ _failure_  

---
__Figure__ ?? A recursive implementation of depth\-limited tree search.
