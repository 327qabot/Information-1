<h1 align="center">

:ship: Course Project Assignment #5 - Back End Requirements Testing  :ship: 

</h1>


In this assignment, you will test the prototype back-end program you built in Assignment 4 using the test cases you created in Assignment 1. 
You should proceed as follows:

### QA Lead Setups

(Your team can choose a different lead this time if anyone else is interested.)

1. If you haven't done so, please add `327qabot` to your repo as a contributor. 
This cute little bot will help us gather information and statistics of all the repos, monitor activities/build-status, and interact with your team to facilitate PRs.

1. Set up GitHub Action if you haven't done so. Please use the YAML file we provided in our python template. You were asked to set up at the beginning of the project. 
The original template comes with some test cases that do not meet the specifications, so the status of your current repo may be build-failing after you added/changed the code in A2. 
If so, comment out the existing test cases to make it build passing locally (i.e. running `pytest` locally) then make a pull request to make the master branch build-passing. 

1. [***Important***] One elected team member, preferably the most experienced one as QA lead, starts by creating one test case based on A1, make sure it builds successfully, create PR, pass all checks, get approved by all, and merge to master. 
Then make sure all the team members can build successfully at their own workstation/laptop. 

1. [***Important***] In your repo's README.md file (the cover page), QA Lead should add the line below if you don't have it yet:
    1. Replace `repo_owner_id` with the GitHub ID of the repo's owner. 
    1. Replace `repo_name` with the repo's name. 
    1. `Python%20application` is the YAML file name where `%20` is space. 
    1. In the YAML file there is a `name` attribute, it controls the shown name on the badge. You can rename it if you want (e.g. `SeekGeek-Build`)
    1. This link will show you a build status badge on the repo home page like this: [![](https://github.com/CISC-CMPE-327/CI-Python/workflows/Python%20application/badge.svg)](https://github.com/CISC-CMPE-327/CI-Python/actions)

```
[![](https://github.com/repo_owner_id/repo_name/workflows/Python%20application/badge.svg)]()
```

1. [***Important***] The QA Lead following this [guide](https://docs.github.com/en/free-pro-team@latest/github/building-a-strong-community/creating-a-pull-request-template-for-your-repository) to create a pull request template agreed upon by the team members. 
[Example](https://embeddedartistry.com/blog/2017/08/04/a-github-pull-request-template-for-your-projects/) of a PR template.
Starting from this point of the assignments, all the PRs have to follow the agreed template. 
All the PRs require ***approval*** and ***comments*** before merging. 

### Creating and Running Test Cases

1. Now divide the test cases you created at A1, and assign each team member the test cases to be created and ran locally. 
Again, each team member should be working on their branch and later merge to master after passing all the checks.

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


