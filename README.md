# POLICY ITERATION ALGORITHM

## AIM
Implement policy iteration algorithm to find optimal policy by iteratively maximizing the value function.

## PROBLEM STATEMENT
Finding the optimal policy to start from start state and reach goal state in the frozen lake environment using policy iteration.

## POLICY ITERATION ALGORITHM
# Step 1:
Import required libraries.
# Step 2:
Load the frozen lake environment.
# Step 3:
Define the value evaluation, value improvement and value iteration functions.
# Step 4: 
Run the functions and display the results.

## POLICY IMPROVEMENT FUNCTION
### Name: SANDHIYA R
### Register Number: 212223240146
```python
def policy_improvement(V,P,gamma=1.0):
  Q=np.zeros((len(P),len(P[0])),dtype=np.float64)
  for s in range(len(P)):
    for a in range(len(P[s])):
      for prob, next_state, reward, done in P[s][a]:
        Q[s][a]+=prob*(reward+gamma*V[next_state]*(not done))
      new_pi=lambda s: {s:a for s,a in enumerate(np.argmax(Q, axis=1))}[s]
  return new_pi
```
## POLICY ITERATION FUNCTION
### Name: SANDHIYA R
### Register Number: 212223240146
```python
def policy_iteration(P,gamma=1.0,theta=1e-10):
  random_actions=np.random.choice(tuple(P[0].keys()),len(P))
  pi=lambda s: {s:a for s, a in enumerate(random_actions)}[s]
  while True:
    old_pi={s: pi(s) for s in range(len(P))}
    V=policy_evaluation(pi,P,gamma,theta)
    pi=policy_improvement(V,P,gamma)
    if old_pi=={s:pi(s) for s in range(len(P))}:
      break
  return V,pi

```

## OUTPUT:
### 1. Policy, Value function and success rate for the Adversarial Policy
<img width="583" height="158" alt="image" src="https://github.com/user-attachments/assets/fc5f9e13-6acf-4467-9e94-aef896263d46" />

<img width="721" height="176" alt="image" src="https://github.com/user-attachments/assets/c70a6b5a-8f09-42d9-81a2-0f307ee4868b" />

### 2. Policy, Value function and success rate for the Improved Policy
<img width="767" height="171" alt="image" src="https://github.com/user-attachments/assets/7ed6e56a-b7f5-4d9f-9e88-e416c79f994d" />
<img width="875" height="192" alt="image" src="https://github.com/user-attachments/assets/46df37d2-7a47-428d-bda1-7463e944c8ad" />


### 3. Policy, Value function and success rate after policy iteration
<img width="1090" height="157" alt="image" src="https://github.com/user-attachments/assets/fa039408-9bfc-4749-8074-13092c02af87" />
<img width="977" height="177" alt="image" src="https://github.com/user-attachments/assets/e5dda94a-868d-4d48-810f-ec3cb7480d24" />

## RESULT:

Therefore, policy iteration algorithm to find optimal policy by iteratively maximizing the value function is successfully implemented.
