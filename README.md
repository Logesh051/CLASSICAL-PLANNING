# Experiment No. 10: Implementation of Classical Planning Algorithm

## Name: LOGESH.N.A

## Register Number: 212223240078

## AIM

To implement Classical Planning Algorithm using Python.

---

## THEORY

Classical Planning is an Artificial Intelligence technique used to find a sequence of actions that transforms an initial state into a goal state.

A planning problem consists of:

* Initial State
* Goal State
* Actions
* Plan

The objective is to determine the sequence of actions required to reach the goal state from the initial state.

---

## ALGORITHM

1. Define the initial state.
2. Define the goal state.
3. Define the available actions.
4. Check whether the goal state is reached.
5. Apply valid actions to generate new states.
6. Continue until the goal state is achieved.
7. Display the generated plan.

---

## PROCEDURE

1. Define the initial state and goal state.
2. Define actions with preconditions and effects.
3. Check whether an action is applicable.
4. Apply the action to generate a new state.
5. Compare the new state with the goal state.
6. Repeat until the goal state is reached.
7. Display the sequence of actions.

---

## PROGRAM

```python
def is_goal_state(current_state, goal_state):
    return current_state == goal_state

def apply_action(current_state, action_effect):
    new_state = current_state.copy()
    new_state.update(action_effect)
    return new_state

def is_applicable(current_state, precondition):
    return all(current_state.get(key) == value
               for key, value in precondition.items())

def find_plan(initial_state, goal_state, actions):

    queue = [(initial_state, [])]
    visited_states = set()

    while queue:

        current_state, partial_plan = queue.pop(0)

        if is_goal_state(current_state, goal_state):
            return partial_plan

        if tuple(current_state.items()) in visited_states:
            continue

        visited_states.add(tuple(current_state.items()))

        for action in actions:

            if is_applicable(
                current_state,
                actions[action]['precondition']
            ):

                next_state = apply_action(
                    current_state,
                    actions[action]['effect']
                )

                queue.append(
                    (next_state,
                     partial_plan + [action])
                )

    return None


initial_state = {'A':'Table', 'B':'Table'}

goal_state = {'A':'B', 'B':'Table'}

actions = {
'move_A_to_B':
{
'precondition':
{'A':'Table','B':'Table'},

'effect':
{'A':'B'}
}
}

plan = find_plan(
    initial_state,
    goal_state,
    actions
)

print(plan)
```

---

## SAMPLE INPUT

```text
Initial State:
A on Table
B on Table

Goal State:
A on B
B on Table
```

---

## SAMPLE OUTPUT

```text
['move_A_to_B']
```

---

## RESULT

Thus the Classical Planning Algorithm was implemented successfully using Python.
