# TREE-CSP-SOLVER

## AIMA3e
__function__ TREE-CSP-SOLVER(_csp_) __returns__ a solution, or failure  
&emsp;__inputs__: _csp_, a CSP with components _X_, _D_, _C_  

&emsp;_n_ &larr; number of variables in _X_  
&emsp;_assignment_ &larr; an empty assignment  
&emsp;_root_ &larr; any variable in _X_  
&emsp;_X_ &larr; TOPOLOGICALSORT(_csp_, _root_)  
&emsp;__for__ _j_ = _n_ __down to__ 2 __do__  
&emsp;&emsp;MAKE\-ARC\-CONSISTENT(_csp_, PARENT(_X<sub>j</sub>_), _X<sub>j</sub>_)  
&emsp;&emsp;__if__ it cannot be made consistent __then return__ _failure_  
&emsp;__for__ _i_ 1 __to__ _n_ __do__  
&emsp;&emsp;_assignment_[_X<sub>i</sub>_] &larr; any consistent value from _D<sub>i</sub>_  
&emsp;&emsp;__if__ there is no consistent value __then return__ _failure_  
&emsp;__return__ _assignment_

---
__Figure ??__ The TREE-CSP-SOLVER algorithm for solving tree\-structured CSPs. If the CSP has a solution, we will find it in linear time; if not, we will detect a contradiction.
