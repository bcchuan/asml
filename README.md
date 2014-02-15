AsmL
====

Abstract State Machine Language - AsmL - is a language for modeling the structure (state) and behavior (operational steps) of digital systems.

State is contained in variables. An abstract state machine computes stepwise, simultaneous updates on these variables. When the machine executes assignments, it does not actually change the variables, but just accumulates a so-called update-set. If this update-set is consistent (e.g., no assignments of different values to the same variable have been queued) and the machine makes it step, the update-set is committed and the variables change their state.

Operational Steps is encoded as actions (rules) that perform conditional update to the state variables.`

As such, an AsmL model program is essentially made up of state variables and actions.

