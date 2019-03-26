# RECURSIVE-BEST-FIRST-SEARCH

## AIMA4e
__function__ RECURSIVE-BEST-FIRST-SEARCH(_problem_) __returns__ a solution, or failure  
&emsp;__return__ RBFS(_problem_,MAKE\-NODE(_problem_.INITIAL\-STATE),&infin;)  

__function__ RBFS(_problem_,_node_,_f\_limit_) __returns__ a solution, or failure and a new _f_\-cost limit  
&emsp;__if__ _problem_.GOAL-TEST(_node_.STATE) __then return__ _node_  
&emsp;_successors_ &larr; EXPAND(_node_)   
&emsp;__if__ _successors_ is empty __then return__ _failure_,&infin;  
&emsp;__for__ _s_ __in__ _successors_ __do__ /\* update _f_ with value from previous search, if any \*/  
&emsp;&emsp;&emsp;_s.f_ &larr; max(_s.g_ + _s.h_, _node.f_)  
&emsp;__loop do__  
&emsp;&emsp;&emsp;_best_ &larr; lowest _f_\-value node in _successors_  
&emsp;&emsp;&emsp;__if__ _best.f_ > _f\_limit_ __then return__ _failure, best.f_  
&emsp;&emsp;&emsp;_alternative_ &larr; the second-lowest _f_\-value among _successors_  
&emsp;&emsp;&emsp;_result,best.f_ &larr; RBFS(_problem_,_best_,min(_f\_limit_,_alternative_))  
&emsp;&emsp;&emsp;__if__ _result_ &ne; _failure_ __then return__ _result, best.f_  

---
__Figure__ 3.5 The algorithm for recursive best\-first search.


## AIMA3e
__function__ RECURSIVE-BEST-FIRST-SEARCH(_problem_) __returns__ a solution, or failure  
&emsp;__return__ RBFS(_problem_,MAKE\-NODE(_problem_.INITIAL\-STATE),&infin;)  

__function__ RBFS(_problem_,_node_,_f\_limit_) __returns__ a solution, or failure and a new _f_\-cost limit  
&emsp;if _problem_.GOAL-TEST(_node_.STATE) __then return__ SOLUTION(_node_)  
&emsp;_successors_ &larr; \[\]  
&emsp;__for each__ _action_ __in__ _problem_.ACTIONS(_node_.STATE) __do__  
&emsp;&emsp;&emsp;add CHILD-NODE(_problem_,_node_,_action_) into _successors_  
&emsp;__if__ _successors_ is empty __then return__ _failure_,&infin;  
&emsp;__for each__ _s_ __in__ _successors_ __do__ /\* update _f_ with value from previous search, if any \*/  
&emsp;&emsp;&emsp;_s.f_ &larr; max(_s.g_ + _s.h_, _node.f_)  
&emsp;__loop do__  
&emsp;&emsp;&emsp;_best_ &larr; lowest _f_\-value node in _successors_  
&emsp;&emsp;&emsp;__if__ _best.f_ > _f\_limit_ __then return__ _failure,best.f_  
&emsp;&emsp;&emsp;_alternative_ &larr; the second-lowest _f_\-value among _successors_  
&emsp;&emsp;&emsp;_result,best.f_ &larr; RBFS(_problem_,_best_,min(_f\_limit_,_alternative_))  
&emsp;&emsp;&emsp;__if__ _result_ &ne; _failure_ __then return__ _result_  

---
__Figure__ ?? The algorithm for recursive best\-first search.
