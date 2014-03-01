AsmL
====

An AsmL program is an abstract state machine in which the run of machine is a series of states and state transitions that results from applying operations to each state in succession.

State is contained in variables. An abstract state machine computes stepwise, simultaneous updates on these variables. When the machine executes assignments, it does not actually change the variables, but just accumulates a so-called update-set. If this update-set is consistent (e.g., no assignments of different values to the same variable have been queued) and the machine makes it step, the update-set is committed and the variables change their state. The consequence is that the new state can only be seen during the following step; state changes are not visible as intermediate results; state changes happen all at once when moving from one step to another. This is called an atomic transaction.

The keyword step marks the transition from one state to another. The order of updates within a step does not matter, but all of the updates in a step must be consistent, not contradicting with each other. If updates do contradict, then they are called "inconsistent updates" and an error occurs.

Example: Quantifying expressions
--------------------------------
S = {1,2,3,4,5,6}

Odd(i as Integer) as Boolean

  return (1 = i mod 2)

Main()

  v1 = forall i in S holds odd(i)

  v2 = exists i in S where i > 4 

  v3 = forall i in S where i > 4 holds odd(i)

  v4 = forall i in S where i > 100 holds odd(i) 

  v5 = forall i in S holds exists j in S where i < j

  v6 = exists i in S where exists j in S where i < j

  v7 = exists i in S, j in S where i < j

  v8 = exists i in S, j in S where i + 1 = j

  v9 = forall i in S, j in S holds i mod j < 6

  WriteLine(v1,v2,v3,v4,v5,v6,v7,v8,v9)

Example: Selection expressions
------------------------------
Main()

  let S = {1,2,3,4,5}

  let y = any i | i in S where i < 4

  let z = the i | i in S where i < 2

  let w = sum i+1 | i in S

  let m = min i | i in S where i < 4

  let x = max i | i in S where i < 4

  WriteLine(y,z,w,m,x)

Example: Selection expressions
------------------------------
const S = {1,2,3,4,5,6,7,8,9,10}

const T = {-1,2,3,5,7}

IsOdd(x as Integer) as Boolean

  return (x mod 2 = 1)

Main()

  let v1 = (any x | x in T where IsOdd(x) and x > 0)

  let v2 = (the val | val in T where val notin S)

  let v3 = (max x + y | x in S, y in T)

  let v4 = (min x | x in S + T)

  WriteLine(v1,v2,v3,v4)

Example: Select Expression
--------------------------
Choose() as (Integer, Integer)

  x = any i | i in {1..3}

  y = any i | i in {2..x}

  return (x, y)

Main()

  WriteLine(explore Choose()) // prints pairs (2,2),(3,2),(3,3) in any order

  WriteLine(search  Choose()) // prints exactly one pair

Example: Enumeration of constrained type
----------------------------------------
type MyType = Integer where value in {1,2,3}

Main()

  WriteLine(Size(enum of MyType)) // print 3

