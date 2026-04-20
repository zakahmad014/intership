name: ahmad abdulkarim
id: 202211426

# intership
task 3 : 
test

task 4 :
i used the dataset from kaggle was designed to predict an exact salary based on a person's experience and skills.

RecBole is a Recommendation library (like Netflix or Amazon algorithms), not a regression tool. It cannot predict continuous numbers like $10000.
Instead of predicting the salary,i transformed the data into a Reverse Job Matcher. Now, we feed the system the user's skills + their desired salary bracket, and the AI recommends the Top 10 Job Titles and Industries that perfectly match their profile!

Why i Didn't Use "Sequential" Models
Sequential models need a history of interactions over time (e.g., User worked at Job A then Job B then Job C). In my dataset, every user only has one single job record. Since there is no "sequence" of events, sequential models would completely fail.

AI Models Used
Instead, i used models that perfectly fit our data snapshot:

BPR (General): Learns basic patterns of who gets hired where.

DeepFM (Context-Aware): Looks at the full resume (Experience, Education) and Job details (Salary, Location) to make highly accurate matches.

CKE (Knowledge-Based): Turns the job market into a "Knowledge Graph", discovering hidden semantic links between jobs, industries, and salaries.

How to Run the Project:

open cmd in folder path and type this command:
py run_all_models.py

Compare the Results (TensorBoard):
To visualize the learning curves and see which model performs best, type this command:
tensorboard --logdir=log_tensorboard
Open http://localhost:6006/ in your browser.




task 5 :

I have completed the evaluation of four Context-Aware models (FM, DeepFM, xDeepFM, DCN) on my dataset using RecBole. To ensure rapid prototyping, all models were trained for 5 Epochs on a GPU.

Key Results (At Epoch 5):
   
xDeepFM: 0.0093 (Highest Validation Score)

FM: 0.0091 (Very close second)

DCN: 0.0090 (Failed to converge; extremely high Training Loss)

DeepFM: 0.0083

Training Time: FM took only 17 seconds, whereas xDeepFM took 3.8 minutes (13x slower) due to its complex CIN architecture.

2. The Decision:
   
For Maximum Accuracy: xDeepFM is the winner. It successfully captured the most complex feature interactions early in training.

<img width="1268" height="582" alt="task5_loss_train" src="https://github.com/user-attachments/assets/45fb3cae-bcb8-49c4-9064-3f12935ff9a8" />
<img width="1264" height="572" alt="task5_valid_score" src="https://github.com/user-attachments/assets/06b88dd3-4155-4a2a-8a70-c1e7c4c7470d" />

task 6 :  Comparative Analysis (Jobs vs. Courses Recommendations)
I processed and trained a new related dataset (Udemy Courses) using the exact same setup as Task 5 (5 Epochs, GPU) to compare how our models perform across two interconnected HR domains: Job Matching (Task 5) vs. Course Matching (Task 6).


Key Results :

DeepFM: 0.0060 (Winner - Highest Accuracy)

FM: 0.0080 (Peak score, very competitive and stable)

xDeepFM: 0.0000 (Failed to generalize, score collapsed)

DCN: 0.0000 (Failed to converge, extremely high Training Loss ~75)
<img width="1247" height="532" alt="task6_loss_train" src="https://github.com/user-attachments/assets/604e2430-8a7c-47a1-8aa8-eea3caa094d7" />
<img width="1259" height="551" alt="task6_valid_score" src="https://github.com/user-attachments/assets/2cdd16e7-5429-4f7b-af5c-dd1aa495fc55" />


Comparative Analysis (Jobs vs. Courses): 

xDeepFM wins in Jobs (Hard Matching): In Task 5, job requirements are strict (e.g., 5 years experience). xDeepFM’s complex architecture (CIN) excels at capturing these explicit, strict rules. However, when applied to Courses (where user interest is flexible), xDeepFM overfitted and collapsed.

DeepFM wins in Courses (Soft Matching): DeepFM proved to be the most versatile model. Its combination of low-order (FM) and high-order (DNN) interactions allowed it to perfectly capture the flexible, interest-based nature of course selection.

Conclusion:
To build a unified Career Platform that recommends both Jobs and Training Courses, DeepFM is the smartest choice.
It offers the best balance of accuracy and stability across both strict and flexible data domains.















For Practical Production (Recommended): The classic FM model is the smartest choice. It achieved nearly identical accuracy to xDeepFM (0.0091 vs 0.0093) but trained 13 times faster. This makes FM highly scalable and cost-effective for large datasets.
