# Fuzzy Reinforcement learning for navigation README  

"Differential drive mobile robot to approach point using reinforcement learning"  

For better look check this note, please visit [HackMD.io](https://hackmd.io/@libernormous/fuzzy_rl_nav)  

by:  
[Liber Normous](https://hackmd.io/@libernormous)   

---

# System description  

This project is developed from our previous project. [It can b ssen here.](https://hackmd.io/@libernormous/ddmr_rl_matlab)   

## Robot dynamic    
The robot dynamic can be seen [here ![](https://i.imgur.com/RmvkGxz.png)
](https://hackmd.io/@libernormous/dynamic_ddmr).  

## Reinforcement agent  
![](https://i.imgur.com/0f2Axag.png)  

### State  
1. Position error fuzzy membership function.
![](https://i.imgur.com/Z2zf69e.png)  
3. Heading error fuzzy membership function.
![](https://i.imgur.com/8DefGed.png)  

### Action  
1. left motor voltage (feeded to sigmoid function).  
2. right motor voltage (feeded to sigmoid function).  

## Reward  
1. Reward of getting closer.  
    a. If $e_p<1$, then $R_1 = (1-e_p)20$ 
    b. Else $R_1 = -0.02e_p$
3. Move away from goal penalty.  
    a. If $\frac{\Delta e_p}{\Delta t}<-0.01$, then $R_2 = 2$  
    b. Else $R_2=-\frac{1}{200}\frac{\Delta e_p}{\Delta t}$  
5. Correct heading reward.  
    a. If $|e_h|<10$, then $R_3=2(10-|e_h|)$  
    b. Else $R_3=-e_h\frac{1}{100}$
7. Heading away from goal penalty.
    a. If $\frac{\Delta |e_h|}{\Delta t}<-0.01$, then $R_4 = 2\frac{\Delta |e_h|}{\Delta t}$     
    b. Else $R_4=-\frac{1}{200}\frac{\Delta |e_h|}{\Delta t}$  

## Actor Network  
![](https://i.imgur.com/1otORrs.png)  
![](https://i.imgur.com/y1GjrRa.png)  

## Critic Network  
![](https://i.imgur.com/6M6pIa1.png)
![](https://i.imgur.com/v1lhDqa.png)  

---

# Result  

## Training result  
**The training converge faster!!**  
![](https://i.imgur.com/nyABrVx.png)  

## Target approaching with and without disturbance  
![](https://i.imgur.com/HTwMHJG.png)  

## Target approaching with and without disturbance  
![](https://i.imgur.com/57DCgZz.png)  
  

## Following figure of 8  
The robot can approach the point with 0.07m tollerance. Better than previous!  
![](https://i.imgur.com/hURelX7.png)  
![](https://i.imgur.com/ZmsdX6e.png)  

## Following figure of 8 under disturbance  
Can still reach every point with 0.07m tollerance!  
![](https://i.imgur.com/JEDDjTc.png)  

---

# Tutorial  
1. For testing, open `testing.m` and run.  
2. For training, open `training.m` and run.  
3. To follow path, use `path_generator.m` to follow point array.  
