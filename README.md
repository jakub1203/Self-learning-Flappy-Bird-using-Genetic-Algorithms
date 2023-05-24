#### Introduction
The purpose of the project was to create a self-learning algorithm that will play modified popular game FlapyBird. In this game except avoiding obstacles, user need to avoid Mario which fly very fast. Genetic algorithms are the main tool that is used to teach neural-network new behavior that will prompt algorithms to overcome new obstacles. This is a very popular problem based on the concept that the player (algorithm) learns how to play a game without any instructions. The project aimed to investigate how genetic algorithms can be used to train neuron networks and to show the power of genetic algorithms in solving complicated problems. For this project, I primarily relied on a YouTube tutorial available at: 
https://www.youtube.com/watch?v=wQWWzBHUJWM&list=PLzMcBGfZo4-lwGZWXz5Qgta_YNX3_vLS2&index=6

#### Algorithm structure
The library that I mainly used is NEAT(NeuroEvolution of Augmenting Topologies) which is a very popular machine-learning library that uses genetic algorithms to train artificial neural networks. 
This part of code contains inputs to our neural network net:
 
There are 6 inputs:
* Y distance between the bird and the top part of the obstacle,  
* Y distance between the bird and the bottom part of the obstacle,  
* Euclidean distance between the position of the "bird" and super_mario1
* Euclidean distance between the position of the "bird" and super_mario2
* Y distance between the bird and the super_mario1
* Y distance between the bird and the super_mario2
To better understand mechanism of algorithm there is picture which shows ours inputs. 

![image](https://user-images.githubusercontent.com/77887361/232574437-e5e156d5-5296-48dd-8711-7c23fdc135d1.png)




The fact that we have only 6 inputs and one output makes our problem easy to solve for the genetic algorithm. In this case, we got only six genses that represent weights for our neural network. Here are also some initial assumptions for our algorithm:
* pop_size  = 10
* activation_default = tanh
* bias_max_value  = 30.0
* bias_min_value  = -30.0
* num_hidden  = 0
* num_inputs    = 2
* num_outputs = 1


Here are also ways to calculate fitness:
* after every iteration we add 0.01 to fitness. It reward birds that stay longer on board
* if bird pass the Obstacle it get 5 points
* if bird pass mario it get 5 points
* if bird hit top or bottom of screen two points are deducted
* if bird hit obstacle one point are deducted
* if bird hit super_mario 5 points are deducted



#### Results
The algorithm was doing better than I expected. Mostly in the second iteration, it find the way to avoid obstacles. Unfortunately it not do so well with Mario obstacles. Here is output for our first generation: 
 ![image](https://user-images.githubusercontent.com/77887361/232574528-328bcb40-7c58-49cb-9c37-e5358d71a835.png)

 
It shows that at the beginning our model not doing so well. Fitness function is about 0.5 and time of game last 2,5 second. But after learning we can notice that the best fitness function achieved 110,31 which is pretty good value. It shows that our algorithm found the way to avoid all obstacles.
![image](https://user-images.githubusercontent.com/77887361/232574545-5830a3be-1a4a-4f62-8a81-0c352d6876bd.png)

The performance you can see under: 

![alt text](https://github.com/jakub1203/Self-learning-Flappy-Bird-using-Genetic-Algorithms/blob/main/giff.gif)

Sources
https://techwithtim.net/wp-content/uploads/2019/08/config-feedforward.txt
https://www.youtube.com/watch?v=wQWWzBHUJWM&list=PLzMcBGfZo4-lwGZWXz5Qgta_YNX3_vLS2&index=6
https://neat-python.readthedocs.io/en/latest/
