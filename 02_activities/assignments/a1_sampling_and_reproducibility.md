# ASSIGNMENT: Sampling and Reproducibility in Python

Read the blog post [Contact tracing can give a biased sample of COVID-19 cases](https://andrewwhitby.com/2020/11/24/contact-tracing-biased/) by Andrew Whitby to understand the context and motivation behind the simulation model we will be examining.

Examine the code in `whitby_covid_tracing.py`. Identify all stages at which sampling is occurring in the model. Describe in words the sampling procedure, referencing the functions used, sample size, sampling frame, any underlying distributions involved, and how these relate to the procedure outlined in the blog post.

Run the Python script file called whitby_covid_tracing.py as is and compare the results to the graphs in the original blog post. Does this code appear to reproduce the graphs from the original blog post?

Modify the number of repetitions in the simulation to 100 (from the original 1000). Run the script multiple times and observe the outputted graphs. Comment on the reproducibility of the results.

Alter the code so that it is reproducible. Describe the changes you made to the code and how they affected the reproducibility of the script file. The output does not need to match Whitby’s original blogpost/graphs, it just needs to produce the same output when run multiple times

# Author: Jessica Liu

```
There are 3 stages of sampling involved. 

1. Initial infection (ATTACK_RATE = 0.10)

Sampling Procedure: simple random sampling 
Functions: np.random.choice()
Sample Size: 100 individuals
Sampling Frame: all 1000 individuals
Distribution: uniform distribution
Relation to Blog Post: represents the random infection process, where each individual has an equal chance of being infected

2. Primary contact tracing (TRACE_SUCCESS = 0.20)

Sampling Procedure: Bernoulli trials
Functions: np.random.rand()
Sample Size: ~20% of infected individuals
Sampling Frame: infected individuals
Distribution: bionomial distribution
Relation to Blog Post: Represents the tracing process where only some infected individuals are successfully traced.

3. Secondary contact tracing (SECONDARY_TRACE_THRESHOLD = 2)

Functions: value_counts()
Sample Size: all infected individuals attending events that meet the threshold of >=2 traced cases
Sampling Frame: infected individuals at events with enough traced cases
Distribution: N/A
Relation to Blog Post: Represents the tracing process where individuals at events with multiple traced cases lead to additional tracing of all infected attendees at that event. 

No, the code doesn't reproduce the graph from the original blog post. The output histogram for "Infections from Weddings" and "Traced to Weddings" both centre around 0.2 because it treats the attendees as two large clusters rather than multiple small groups. As the result, both clusters can easily meet the second tracing condition, maintaining the 20% proportion. 

Reducing the number of repetitions from 1000 to 100 leads to higher variability between runs, making the results less stable and reproducible.

I modified the random seed setting to ensure reproducibility while maintaining variation across iterations.

```


## Criteria

|Criteria|Complete|Incomplete|
|--------|----|----|
|Altercation of the code|The code changes made, made it reproducible.|The code is still not reproducible.|
|Description of changes|The author explained the reasonings for the changes made well.|The author did not explain the reasonings for the changes made well.|

## Submission Information

🚨 **Please review our [Assignment Submission Guide](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md)** 🚨 for detailed instructions on how to format, branch, and submit your work. Following these guidelines is crucial for your submissions to be evaluated correctly.

### Submission Parameters:
* Submission Due Date: `23:59 - 09/04/2025`
* The branch name for your repo should be: `assignment-1`
* What to submit for this assignment:
    * This markdown file (a1_sampling_and_reproducibility.md) should be populated.
    * The `whitby_covid_tracing.py` should be changed.
* What the pull request link should look like for this assignment: `https://github.com/<your_github_username>/sampling/pull/<pr_id>`
    * Open a private window in your browser. Copy and paste the link to your pull request into the address bar. Make sure you can see your pull request properly. This helps the technical facilitator and learning support staff review your submission easily.

Checklist:
- [x] Create a branch called `assignment-1`.
- [x] Ensure that the repository is public.
- [x] Review [the PR description guidelines](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md#guidelines-for-pull-request-descriptions) and adhere to them.
- [x] Verify that the link is accessible in a private browser window.

If you encounter any difficulties or have questions, please don't hesitate to reach out to our team via the help channel in Slack. Our Technical Facilitators and Learning Support staff are here to help you navigate any challenges.
