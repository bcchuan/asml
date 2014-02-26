AsmL
====

Abstract State Machine Language AsmL models digital systems as a set of state variables and actions. Actions are conditional update rules to state variables. An AsmL program is an abstract state machine in which the run of machine is a series of states and state transitions that results from applying operations to each state in succession.

State is contained in variables. An abstract state machine computes stepwise, simultaneous updates on these variables. When the machine executes assignments, it does not actually change the variables, but just accumulates a so-called update-set. If this update-set is consistent (e.g., no assignments of different values to the same variable have been queued) and the machine makes it step, the update-set is committed and the variables change their state. The consequence is that the new state can only be seen during the following step; state changes are not visible as intermediate results; state changes happen all at once when moving from one step to another. This is called an atomic transaction.

The keyword step marks the transition from one state to another. The order of updates within a step does not matter, but all of the updates in a step must be consistent, not contradicting with each other. If updates do contradict, then they are called "inconsistent updates" and an error occurs.

