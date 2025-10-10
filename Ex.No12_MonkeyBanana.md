# Ex.No: 12  Planning –  Monkey Banana Problem
### DATE: 04.10.2025                                                                        
### REGISTER NUMBER : 212223060208
### AIM: 
To find the sequence of plan for Monkey Banana problem using PDDL Editor.
###  Algorithm:
Step 1:  Start the program <br> 
Step 2 : Create a domain for Monkey Banana Problem. <br> 
Step 3:  Create a domain by specifying predicates. <br> 
Step 4: Specify the actions GOTO, CLIMB, PUSH-BOX, GET-KNIFE, GRAB-BANANAS in Monkey Banana problem.<br>  
Step 5:   Define a problem for Monkey Banana problem.<br> 
Step 6:  Obtain the plan for given problem.<br> 
Step 7: Stop the program.<br> 
### Program:
```
(define (domain monkey)
    (:requirements :strips)
    (:constants monkey box knife bananas glass waterfountain)
    (:predicates (location ?x)
        (on-floor)
        (at ?m ?x)
        (hasknife)
        (onbox ?x)
        (hasbananas)
        (hasglass)
        (haswater))
    ;; movement and climbing
    (:action GO-TO
        :parameters (?x ?y)
        :precondition (and (location ?x) (location ?y) (on-floor) (at monkey ?y))
        :effect (and (at monkey ?x) (not (at monkey ?y))))
    (:action CLIMB
        :parameters (?x)
        :precondition (and (location ?x) (at box ?x) (at monkey ?x))
        :effect (and (onbox ?x) (not (on-floor))))
        (:action PUSH-BOX
    :parameters (?x ?y)
    :precondition (and (location ?x) (location ?y) (at box ?y) (at monkey ?y) (on-floor))
    :effect (and (at monkey ?x) (not (at monkey ?y))
                 (at box ?x) (not (at box ?y))))
;; getting bananas
(:action GET-KNIFE
    :parameters (?y)
    :precondition (and (location ?y) (at knife ?y) (at monkey ?y))
    :effect (and (hasknife) (not (at knife ?y))))
(:action GRAB-BANANAS
    :parameters (?y)
    :precondition (and (location ?y) (hasknife)
        (at bananas ?y) (onbox ?y))
    :effect (hasbananas))
;; getting water
(:action PICKGLASS
    :parameters (?y)
    :precondition (and (location ?y) (at glass ?y) (at monkey ?y))
    :effect (and (hasglass) (not (at glass ?y))))
(:action GETWATER
    :parameters (?y)
    :precondition (and (location ?y) (hasglass)
        (at waterfountain ?y)
        (at monkey ?y)
        (onbox ?y))
    :effect (haswater))
```
### Input 
```
(define (problem pb1)
    (:domain monkey)
    (:objects p1 p2 p3 p4 bananas monkey box knife)
    (:init (location p1)
        (location p2)
        (location p3)
        (location p4)
        (at monkey p1)
        (on-floor)
        (at box p2)
        (at bananas p3)
        (at knife p4)
    )
    (:goal (and (hasbananas)))
)
```
### Output/Plan:

<img width="1393" height="710" alt="image" src="https://github.com/user-attachments/assets/45a07433-b058-4abc-8ac4-d7b35d140097" />
<img width="1465" height="707" alt="image" src="https://github.com/user-attachments/assets/ddd45916-58e1-45be-bbef-87872aa00ea7" />
<img width="1470" height="703" alt="image" src="https://github.com/user-attachments/assets/f3979833-252a-4854-b8b5-d27912dcd3ad" />
<img width="1644" height="779" alt="image" src="https://github.com/user-attachments/assets/b2635954-05cc-43a3-926b-d76f8e18f5e5" />
<img width="1654" height="782" alt="image" src="https://github.com/user-attachments/assets/0e3b79b3-e6e7-4fbc-bd4d-b098a69665de" />
<img width="1648" height="773" alt="image" src="https://github.com/user-attachments/assets/860dc31c-2f61-4735-9838-c16e192ea2d1" />

### Result:
Thus the plan was found for the initial and goal state of given problem.
