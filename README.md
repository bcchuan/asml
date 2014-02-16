AsmL
====

Abstract State Machine Language AsmL is a language for modeling digital systems. Digital systems have discrete structure and discrete operations that can be modeled using AsmL as state and operations.

State is contained in variables. An abstract state machine computes stepwise, simultaneous updates on these variables. When the machine executes assignments, it does not actually change the variables, but just accumulates a so-called update-set. If this update-set is consistent (e.g., no assignments of different values to the same variable have been queued) and the machine makes it step, the update-set is committed and the variables change their state. The consequence is that the new state can only be seen during the following step; state changes are not visible as intermediate results; state changes happen all at once when moving from one step to another. This is called an atomic transaction.

Operations is actions that perform conditional update to state variables.

An AsmL model program is essentially made up of state variables and actions. An AsmL model program is an abstract state machine. The run of a machine is a series of states and state transitions that results from applying operations to each state in succession,

The keyword step marks the transition from one state to another.

