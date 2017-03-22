# SIMULATED-ANNEALING

## AIMA3e
__function__ SIMULATED-ANNEALING(_problem_,_schedule_) __returns__ a solution state  
&emsp;__inputs__: _problem_, a problem  
&emsp;&emsp;&emsp;&emsp;_schedule_, a mapping from time to "temperature"  

&emsp;_current_ &larr; MAKE\-NODE(_problem_.INITIAL\-STATE)  
&emsp;__for__ _t_ = 1 __to__ &infin;  __do__  
&emsp;&emsp;&emsp;_T_ &larr; _schedule(t)_  
&emsp;&emsp;&emsp;__if__ _T_ = 0 __then return__ _current.state_  
&emsp;&emsp;&emsp;_next_ &larr; a randomly selected successor of _current_  
&emsp;&emsp;&emsp;_&Delta;E_ &larr; _next_.VALUE - _current_.VALUE  
&emsp;&emsp;&emsp;__if__ _&Delta;E_ > 0 __then__ _current_ &larr; _next_  
&emsp;&emsp;&emsp;__else__ _current_ &larr; _next_ only with probability e<sup>_&Delta;E_/_T_</sup>

---
__Figure__ ?? The simulated annealing algorithm, a version of stochastic hill climbing where some downhill moves are allowed. Downhill moves are accepted readily early in the annealing schedule and then less often as time goes on. The _schedule_ input determines the value of the temperature _T_ as a function of time.
