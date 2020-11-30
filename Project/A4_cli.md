<h1 align="center">

:ship: Course Project Assignment #4: Back End Rapid Prototype :ship: 

</h1>

In this assignment, you will design and rapidly program the first version of your team's Back
Office. Since the next assignment will involve testing it, do not do full testing of your Back Office
at this time (no marks are for correctness yet!). Try to work together on your program using Pair Programming, where one
of you advises on the higher-level design issues while the other does the coding.

The backend is a standalone program that runs on the back office during the night, takes some arguments with no user interactions and exits with output files.

|  |  |  |
|-|-|-|
| Program input | arguments | the names of the output transaction files from all the offices of different locations, as positional arguments. |
|  |  |  |
| Program output | updated_accounts.csv |  the valid account list file to be used for the frontend offices in the next day |
|                |  updated_tickets.csv |  the valid ticket list file to be used for the frontend offices in the next day |


The backend program takes all the output transactions files from all locations (so you will have three files if you have three different locations, i.e. three different runs of the frontend program), process all the transactions, and produce the new account information file and the new ticket information file for the next day. Specificatoins:

- The backend program will first read `accounts.csv` and `tickets.csv`. These two files contain the account information and ticket information at the begining of the day. These two files are also used by the frontend offices of different locations.
- The transaction files, specified by the program input, are processed following an alphabetical order.
- Then the backend program process the transaction one-by-one. Each transaction has to satisfy the constraints specificed in the frontend requirement. For example, a ticket purchase transaction has to make sure that there are enough tickets in order to proceeed.
- For failed/invalid transactions, log the error in the console. There is no specific requirement for the format.
- After processing all the transactions, output the updated account information in `updated_accounts.csv` file and the updated ticket information in `updated_tickets.csv` file. 


As much as possible, try to keep in mind the principles of Incremental Development (IDP) and
eXtreme Programming (XP) while creating your solution. Using Incremental Development,
structure your programming as a sequence of subsets, where at each stage you implement only
the next most essential feature, creating a running prototype before moving on to adding the
next feature. Using XP, work together on your program using Pair Programming, where one of
you advises on the higher-level design issues while the other does the actual coding.



Deliveries:
- A design document in PDF format for your Back Office, giving the overall structure of your solution, showing the classes
and methods as a diagram or table, with a brief (one sentence) description of the intention of each.
- The first version of the source code to implement your design (including all features of the Back End). This version
should run on at least some manual inputs but should not yet be completely tested with requirement tests from
Assignment #1 (since that will be the next assignment, and it’s better to leave some failures until then). The back-end
should follow strictly the original specification regarding its input and expected output.
- **Detail code review** for each pull request.


Submission: create a tag of on your GitHub repository (following our assignment submission instruction using git) and submit the following infomation to onQ.
- tag_name
- pull_request_links for team_member_1, number of pull-request reviews done by team_member_1
- pull_request_links for team_member_2, number of pull-request reviews done by team_member_2
- pull_request_links for team_member_3, number of pull-request reviews done by team_member_3
- pull_request_links for team_member_4, number of pull-request reviews done by team_member_4
  


Your solution to this assignment will be judged on the clarity and readability of the design and the code, so work at using
your best programming practices, including naming variables, classes and methods meaningfully, and commenting liberally to
make it easy for other programmers to understand.
Your solution to this assignment will not be judged on its correctness; rather, on the quality of its design and coding. This
is to be a rapid first version, not a final product. So, design and program it to work correctly, but don’t worry about getting it
fully tested or debugged yet, since that’s what you will do on the next assignment.


Marking: 

|  |  | 10 marks |
|--|--|------|
| Design  |  | 3 |
|  | Architecture |   |
|  | • clearly documents structure of solution |  |
|  | • explicitly describes intention of each class and method |  |
|  | • accurately reflects solution structure |  |
|  | • clearly shows where inputs and outputs fit in |  |
|  | Completeness |   |
|  | • evidently addresses all required functionality |  |
|  | • has considered all kinds of user inputs |  |
| Source Code |  | 4  |
|  | Structure and format |   |
|  | • code is structured and formatted such that architecture is clearly visible in code |  |
|  | • naming of classes and methods clearly reflect their role in the solution |  |
|  | • as little cloning or redundancy as possible | |
|  | Maintainability |   |
|  | • avoidance of coding tricks and hacks |  |
|  | • simplest solution possible, no frills and extras |  |
|  | • clearest solution possible, no gratuitous optimizations | |
|  | Internal documentation |  |
|  | • clear naming of all variables and constants to reflect their role in the solution |  |
|  | • comments for every class and method, clearly documenting their interface and intention | |
|  | • comment at beginning of main program, documenting | |
| Teamwork |  |  |
|  | All the updates to the repository have to go through pull-request. All the pull-request requires reviews from the team members.  | 3  |
