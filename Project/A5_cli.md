<h1 align="center">

:ship: Course Project Assignment #5 - Back End Requirements Testing  :ship: 

</h1>


In this assignment, you will test the prototype back-end program you built in Assignment 4 using unit testing. 
You should proceed as follows:

### QA Lead Setups

(Your team can choose a different lead this time if anyone else is interested.)

1. If you haven't done so, please add `327qabot` to your repo as a contributor. 
This cute little bot will help us gather information and statistics of all the repos, monitor activities/build-status, and interact with your team to facilitate PRs.

1. Make sure you have enough Action minutes left. If you ran out of minutes, you can transfer the ownership of the repo to another team member then you will have more minutes.

1. All the PRs have to follow the agreed template. 
All the PRs require ***approval*** and ***comments*** before merging. 

### Creating and Running Test Cases


1. You are to create two separate sets of white box unit tests, one for the method or section of code that handles all ticket creation transactions, and one for the method or section of code that handles all ticket sale transactions.


1. For each of these two methods or sections of code,
   1. choose any systematic white box test method but you must choose a different method for each of the two kinds of transaction
   1. analyze the code according to the system of the test method you choose and create a table of cases to be tested
   1. create a set of tests (transaction inputs) to cover each of the test cases you have identified in the table
   1. run the test cases

1. For the failing test cases, fix either the test case or the source code. 
Both of the test cases and your source code have to strictly follow the requirement regarding the printed message and behavior. 

1. Any fixes to the source code as well as the test cases have to be documented and compiled into a failure report (see requirement below). 
Usually, we will do integration testing as well but we skip this for now.

1. Recommended practice for the beginner: don't try to create all the test cases and then ran it all. 
Instead, create one and make sure it works, then proceed to the next. 


### PRs and Merging

Each pull request has to follow the template selected in the earlier step. Before merging, make sure all checks passing. 
Emoji are encouraged to facilitate your company's cultural development.
Example [1](http://greena13.github.io/blog/2016/08/19/emojis-are-the-solution-to-useless-commit-messages/).
Someone please watches the Action CI minutes left (avoid pushing with very minor updates)

### Delivery:

1.	Descriptions on how you modified the template to conduct the testing if any. 
If you propose a different approach than the template, explain how you did that and justify why. 

1.	The detailed failure report for your test runs, 
with a row for each observed test failure and columns showing the test name, 
what it was testing, how its output was wrong, what the error in your code was, 
and how you changed the program (or test input) to fix it. 
You can put it on a markdown table. 

1. Following the assignment submission guide to submit the link of the repo tag as well as each team member's pull request:
```
link_to_repo_tag
pull_request_links for team_member_1, number of pull-request reviews done by team_member_1
pull_request_links for team_member_2, number of pull-request reviews done by team_member_2
...
```

### Marking:

| Test Code      |              |                                                                                                                                                                                            | 5 marks |
|----------------|--------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------|
|                | Organization |                                                                                                                                                                                            |         |
|                |              | - clear, readable scripts or testing code                                                                                                                                                  |         |
|                |              | - understandable variable names                                                                                                                                                            |         |
|                |              | - clear internal comments in the testing code showing test case IDs and the purpose/requirement being tested                                                                               |         |
|                | Automation   |                                                                                                                                                                                            |         |
|                |              | - all testings are done automatically                                                                                                                                                      |         |
| Failure Report |              |                                                                                                                                                                                            | 3 marks |
|                | Organization |                                                                                                                                                                                            |         |
|                |              | - failure report in clear table form, listing test name or number, what was being tested, the nature of the failure, what the error in the code was, and what actions were taken to fix it |         |
|                | Completeness |                                                                                                                                                                                            |         |
|                |              | - all tests have been run, and all failures addressed                                                                                                                                      |         |
| Teamwork      |              |                                                                                                                                                                                            | 2 marks |
|                |              | All the updates to the repository have to go through pull-request.                                                                                                                         |         |
|                |              | All the pull-requests require approval before merging.                                                                                                                                     |         |
|                |              | All the pull-requests require reviews (comments/recommended fixes) from the team members.                                                                                                  |         |
|                |              | All the pull-requests have to follow a PR template (cannot be an empty template)                                                                                                           |         |


