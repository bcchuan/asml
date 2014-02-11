AsmL
====

Abstract State Machine Language

State is contained in variables. An abstract state machine computes stepwise, simultaneous updates on these variables. When the machine executes assignments, it does not actually change the variables, but just accumulates a so-called update-set. If this update-set is consistent (e.g., no assignments of different values to the same variable have been queued) and the machine makes it step, the update-set is committed and the variables change their state.

Specification: A description of what a program, component, or system is supposed to do. A specification should be a complete description of behavior that describes everything the system must do, might do, and must not do. A model program can act as a specification. Contrast to design. 

Design. A description of how a system or program is built up from parts and how the parts communicate. Contrast to specification.
