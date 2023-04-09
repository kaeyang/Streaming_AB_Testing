# Streaming_AB_Testing

The problem statement here is to optimize the Netflix.com home page by minimizing the browsing time for any user. The concern at hand is that it takes longer for customers to decide when faced with numerous options to choose from (referred to as choice overload). 

The dataset collected has the features of: <br>
preview tile size: [0.1,0.5] <br>
recommendation match score:[0,100] (integer values) <br>
preview video length:[30, 120] (increments of 5 seconds) <br>
preview type: trailer footage(TT) or actual movie footage(AC) <br>

and the target of: <br>
Browsing Time: (seconds) 

To determine if there is any improvement from my experiments, I would submit my predictions into a web-based simulator provided by the professor which will output response observations. I initially start with a 4 corners approach to determine the best PrevType and then zeroed in on the MatchScore and PrevLength using further grid search. <br><br>

### Phase 1: 4 corners comparison (8 conditions)
First, I determined the optimal preview type using a four corners search of typical values for both types of preview type. I found that preview type “TT”  minimized browsing time, with a mean of 18.21 seconds. <br><br>

### Phase 2: Broader grid search (16 conditions)
Next, I performed a broader grid search for match score and preview length, while using the optimal preview time from the first step (TT) and holding tile size fixed at 0.3. The preview length of 66 seconds and match score of 80% minimized the mean browsing time to 14.39 seconds. <br><br>

### Phase 3: Narrower grid search (8 conditions)
Based on the previous finding, I narrowed down the grid search using preview lengths of 57, 66, and 75 seconds, and match scores of 60%, 70%, and 80%, while holding preview type as “TT” and tile size fixed. From this grid search, a preview length of 66 seconds and match score of 70% minimized the mean browsing time (13.98 seconds). <br><br>

### Phase 4: Narrower grid search (8 conditions)
I narrowed down the grid search even more using preview lemgths of 62, 66, and 70 seconds, with match scores of 65%, 70%, and 75% while holding preview type as “TT” and tile size fixed. Unfortunately, the browsing time increased to 14.08 with the preview length of 66 seconds and match score of 75%. <br><br>

### Phase 5: Final grid search (9 conditions)
I narrowed down the grid search even more using preview lemgths of 64, 66, and 68 seconds, with match scores of 73%, 75%, and 77% while holding preview type as “TT” and tile size fixed. From this grid search, a preview length of 66 seconds and match score of 73% minimized the mean browsing time (13.97 seconds). <br><br>

### Using my findings on the actual test data:
From my findings, I started the grid search at preview length of 66 seconds and match score of 73% with tile size fixed at 0.3 and preview type of "TT". Eventually, I found the optimum features to have a preview length of 75 seconds, match score of 75%, tile size of 0.3, and preview type of "TT". I also constructed a 95% confidence interval of the minimum browsing time using the Student's t-test, resulting in the CI range of 9.71 seconds ~ 10.14 seconds. 
The next steps would be to conduct a hypothesis test to determine if the tile size is really an insignificant feature since the professor hinted that tile size should not be considered in the experiments.
