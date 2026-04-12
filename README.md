name: ahmad abdulkarim
id: 202211426

# intership
task 3 : 
test

task 4 :
i used the dataset was designed to predict an exact salary based on a person's experience and skills.

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
