> notes of Stanford CS231n Deep Learning for Computer Vision 2017 edition [Lecture 14 | Deep Reinforcement Learning](https://www.youtube.com/watch?v=lvoHnicueoE&list=PLC1qU-LWwrF64f4QKQT-Vg5Wr4qEE1Zxk&index=15&ab_channel=StanfordUniversitySchoolofEngineering)

## What is reinforcement learning?

![](../assets/img/reinforcement-learningg.png)

### Examples of reinforcement learning: the states, actions and rewards

#### Cart-Pole problem

![img.png](../assets/img/cart-pole-problem.png)
- Objective: balance a pole on top of a movable cart
- State: angle, angular speed, position, horizontal velocity
- Action: horizontal force applied on the cart
- Reward: 1 at each stept if the pole is uprigght

#### Robot locomotion

![img.png](../assets/img/robot-locomotion.png)

- Objective: make the robot move forward
- State: Angle and position of the joints
- Action: Torques applied on joints
- Reward: 1 at each time step uprigght + forward movement

#### Atari Games

![img.png](../assets/img/atari-games.png)

- Objective: complete the game with the highest score
- State: Raw pixel inpupts of the game state
- Action: Game controls e.g., left, right, up, down
- Reward: Score increase / decrease at each time step

#### Weiqi

![img.png](../assets/img/weiqi.png)

- Objective: win the game
- State: Position of all pieces
- Action: Where to put the next piece down
- Reward: 1 if win at the end of the game, 0 otherwise

