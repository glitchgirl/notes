# what does logic, abstract mathematics, and computer programming have in common

## steps of a classic proof

- premise
    our suppose statement (suppose this is a natural number)
- deduction
    new info from our premise
- proof
    once we get the new info we want from the deductions we get our proof

Proposition
    - statements that can be true or false

Gerhard Gentzen
    - nazi
    - sequent calculus (the trees that have the bottom line for the solution and each step above is a deduction)
        - has left rules and right rules
        - left rules "use" a premise
        - right rules "make" a deduction
    - top level on is the premises
    - cut rules can get rid of premises if they exist somewhere else, through the use of cut elmination can help prove consistency
    - Natural deduction- doesn't have left and right rules, has introduction and elimation rules, is typically easier to understand
    - consistent = means that can't be used to proof false things
    - natural deducution is isomorphic to sequent calculus

Alonzo Church / Alan Turing
    - Lambda calculus / Turing machine > makes functional programming
    - has terms (functions)
    - can apply
    beta - changing terms (lx.t2)t1
    neta - f(x) = g(x) which is just f(x)
    - not super good at false logic
    - loops that cause issues

Bertand Russell
    - activist
    - fixed a problem with loops in lambda calculus using terms

Combinators
    - Ix = x (echo) ((don't need this one because you can use K to get it))
    - Kxy = x
    - Sc1c2x = c1c2(c1x)

Combinatory Logic
    - complete for propositional logic

William Howard
    - proved that natural deduction is the same thing as sequent calc, with simplifications
