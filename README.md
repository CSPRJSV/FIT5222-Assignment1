# FIT5222-Assignment1
# VX: csprojhelp 备注: github
FIT5222-Assignment1 1v1 cs tutor 专业辅导

Assignment 1: Flatland Challenge

In this assignment your job is to schedule a set of trains through a railway network.

You need to coordinate every train from its starting station to its destination as quickly as possible. As there can be many trains moving at the same time you need to guarantee that each path is collision-free.

The assignment has three sections, in increasing order of difficulty. The amount of points relative to each question is stated in the question heading. A passing grade is 50%.

Be sure to watch the introductory video on Moodle and to read the Introduction to Flatland documentation which we have prepared for you. Both are available from Moodle.

You must update your flatland code and installation before starting the assignment:

● Under flatland folder

● git pull

● python3 setup.py install

● Now, run command python3 -m pip list , you should see flatland-rl version is updated to 2.2.4

● (Hint, use python instead of python3 if python points to the right one on your machine)

Instructions to get code base (in assignment1_2023 branch of piglet repo) for assignment is in the Introduction to Flatland documentation.

When the contest server is ready, you will see your f score upon submission.

QUESTION 1: Warm up (15 points)

You are given start and target locations, one at a time. Your job is to route each train independently from all the rest. In this question collisions are not possible and there is no time dimension.

For this question, you need to implement a successor function for the Flatland domain. You also need to choose an algorithm to help you find paths. You are free to use any of the techniques we have discussed in the lectures, that you have read about in the literature or can write your own new approach.

Your solution will be evaluated on 40 evaluation instances (only staff have these instances) with 2 hours timelimit and each instance has 1 agent. We will compare your sum of individual cost(SIC, for agents did not arrive goal location, its cost will be Assignment 1 - FIT5222 Planning and automated reasoning

𝑇

𝑚𝑎𝑥

=

8 * ( 𝑤 𝑖

𝑑 𝑡 ℎ

+

ℎ 𝑒

ℎ 𝑡 )

𝑖 𝑔

of the map) and success rate to an optimal solution

implemented by teaching team and calculate your score using following method:

( 𝑙 𝑑 𝑆𝐼𝐶 𝑇 * 𝑓 𝑙 𝑑 )/ 𝑙 𝑝 𝑠𝑐𝑜𝑟𝑒 = 𝑐𝑜𝑚𝑝 𝑒 𝑡 𝑒 𝑎𝑔𝑒𝑛 𝑡 𝑠 + 𝑎 𝑖 𝑒 𝑎𝑔𝑒𝑛 𝑡 𝑠 𝑡 𝑜 𝑡 𝑎 𝑎𝑔𝑒𝑛 𝑡 𝑠 _ _ 𝑚𝑎𝑥 _ _

𝑓 𝑠𝑐𝑜𝑟𝑒 𝑝 𝑠 𝑡 𝑎 𝑓𝑓 / 𝑝𝑠𝑐𝑜𝑟𝑒  =

where

𝑝𝑠 𝑡 𝑎 

is the p score of staff implementation. Generally, a good solution has small 𝑓

𝑓𝑓

𝑝

score and large

score. 𝑓𝑠𝑐𝑜𝑟𝑒  Your final score will be

× 1 5

(since there are 15 points available for this question).

QUESTION 2: Easy mode (25 points)

You are given start and target locations, one at a time, as well as a set of existing paths for trains that are already moving. Your job is to route each train individually while avoiding collisions with all the rest. You are free to use any of the techniques we have discussed in the lectures, that you have read about in the literature or can write your own new approach.

For this question, you need to modify your successor function to account for time. In addition, there might be the situation that the search algorithm failed to find a feasible solution as dynamic obstacles block all possible paths. Just return an empty list in this case.

Furthermore, each action and each location for every computed plan need to be collision-free.

Your solution will be still evaluated on 56 instances with a 2 hours timelimit and your score in this question will again be computed as the sum of individual path costs (SIC) and compared to the best solution from students (and staff)!

𝑓𝑠𝑐𝑜𝑟𝑒  Your will be computed in the same way as for Question 1. But there are some

differences:

● Here we compute

𝑓𝑠𝑐𝑜𝑟𝑒 

for each instance.

● Each instance contains 𝑛 multiple agents. ∑ 𝑓 𝑠𝑐𝑜𝑟𝑒 𝑖 ÷ 5 6 × 2

● Your final points will be

5

, where

𝑖

is instance id.

𝑖

There are up to 25 points available for this question. Assignment 1 - FIT5222 Planning and automated reasoning

QUESTION 3: Challenge (60 points)

You are given sets of start and target locations at the same time. Your job is to route all the trains simultaneously in a way that is collision-free. But, each agent has an expected arrival time, late arrival will result in a penalty.

You are free to use any of the techniques we have discussed in the lectures, that you have read about in the literature or can write your own new approach.

Now, as all agents are under your control, you need to make all agents reach their goal locations.

In this question agents may run into malfunctions during execution. The evaluator will call the replan function when a new malfunction occurs. Implement the replan function to properly handle malfunction. Refer to the “Introduction to Flatland” document for details about malfunction and replan function.

Your solution will be still evaluated on 56 instances with different difficulty levels in 2 hours and your score in this question will again be computed as the sum of individual path costs (SIC) and compared to the best solution from students (and staff)!

𝑓𝑠𝑐𝑜𝑟𝑒  Your computation is similar to Question 1. But there are some differences:

𝑝 𝑠𝑐𝑜𝑟𝑒 ( 𝑐𝑜𝑚𝑝 𝑙 𝑒 𝑡 𝑒 𝑑 𝑎𝑔𝑒𝑛 𝑡 𝑠 𝑆𝐼𝐶 + 𝑝𝑒𝑛𝑎 𝑙 𝑡 𝑦 + 𝑇 * 𝑓 𝑎 𝑖 𝑙 𝑒 𝑑 𝑎𝑔𝑒𝑛 𝑡 𝑠 )/ 𝑡 𝑜 𝑡 𝑎 𝑙 𝑎𝑔𝑒𝑛 𝑡 𝑠 = ● _ _ 𝑚𝑎𝑥 _ _

𝑝𝑒𝑛𝑎 𝑙 𝑡 𝑦 2 * 𝑡 𝑜 𝑡 𝑎 𝑙 𝑑 𝑒 𝑙 𝑎𝑦𝑒 𝑑 𝑚𝑒𝑠 𝑡 𝑒𝑝𝑠 𝑖 𝑡 ● The is _ _ .

● Each instance 𝑓 𝑠𝑐𝑜𝑟𝑒 contains multiple agents. 𝑝𝑏 𝑎𝑠𝑒 

● Each instance’s will refer to a baseline implementation 𝑝𝑎 𝑑 𝑣  implementation (or best student solution which ever is better):

𝑓 𝑠𝑐𝑜𝑟𝑒 𝑝 𝑏 𝑎𝑠𝑒 𝑝 𝑏 𝑎𝑠𝑒 𝑝 𝑠𝑐𝑜𝑟𝑒 0 * 0 5) ( 0 ) ( 0 5 5 * = 𝑚 𝑖 𝑛 + 𝑚𝑎𝑥 . 𝑝 𝑠𝑐𝑜𝑟𝑒 , . . 𝑝 𝑏 𝑎𝑠𝑒 − 𝑝 𝑎 𝑑 𝑣 ,

𝑛 ∑ 𝑓 𝑠𝑐𝑜𝑟𝑒 𝑖 ÷ 5 6 × 60 𝑖 ● 𝑖 , where is instance id.

and an advanced

There are up to 60 points available for this question.

Report (50 points)

You need to create a report that describes your approach to each of the questions. This includes a textual description of your approaches, why you adopted that particular approach and a thorough discussion along with any supplementary material required (such as pseudo code, images, graphs, tables…).
