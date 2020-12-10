<h1 align="center">

:ship: Course Project Assignment #6 - SHIP IT!!!!  :ship: 

</h1>

Now we have developed and tested our first full working version of the application. It is time to ship and delopy!
Before deployment, we will need to conduct several rounds of security validation. 
They are usually conducted throughout the development process and integrated into the automated testing CI process. 
But since we don't have enough time to setup the automation, this part is left to be conducted manually before deployment. 
Deploying application is also not an easy task, considering there are so many different environmental factors such as operating system compatibility, python version, system libraries, python dependencies, etc. 
Docker and docker compose reduce the complexity of deployment by making it environment-self-contained.
Additionally, in our prototype we are using sqlite database, which is great for development and testing purpose. 
However, we are expecting more than 30 million active online users right after our intial deployment. 
With a single database file cannot accomodate the need of the client. Therefore, in this assignment, we have the following tasks:

- Security Check - SQL-Injection
- Security Check - XSS
- Building and publishing your Docker container
- Docker compose integrating A MySQL database, database web interface, and our web application. 


### SQL-Injection Security Report

Before deployment, let's scan for SQL injection bugs and curate an injection vulnerability report, by following the steps below:

- Install [SQLmap](https://github.com/sqlmapproject/sqlmap) (git clone or download & unzip their zip/tar.gz file)
- Manually start your web application.
- Inside the sqlmap folder, you can run their python script through the command `python sqlmap.py -h` without errors.
- Scan your website by using `python sqlmap.py -u http://127.0.0.1:8081/ --forms --batch --crawl=10` 
- Save the log for use later.
- Manually login your website with a valid user account. 
- Check the your session id (let's refer it by `your_session_id`) in the cookie through the request headers of the index page (LocalHost or 127.0.0.1) in the browser. [How?](https://www.google.com/search?q=chrome+how+to+check+request+header&oq=chrome+how+to+check+request+header)
- Scan your website again by using `python sqlmap.py -u http://127.0.0.1:8081/ --forms --batch --crawl=10 --cookie=your_session_id` here `your_session_id` is the one you obtained from the last step.
- You should be able to see that it is scanning restricted forms that only available after login (i.e. authentication).
- Save the log for use later.

Now you have all the logs. Let's compile a SQL injection scanning report by filling a table following this format, then answer the questions below.

|      | Route/URL                      | Parameter | Number of Injection Trials | Number of Successful Trials |
|:----:|--------------------------------|:---------:|:--------------------------:|:---------------------------:|
| Scan | http://127.0.0.1:8081/register |   email   |             14             |             0               |
|      |                                |           |                            |                             |
|      |                                |           |                            |                             |

#### :book: Questions:

1. :ship: Are all the user input fileds in your application covered in all the test cases above? Any successful exploit?
2. :ship: We did two rounds of scanning. Why the results are different? What is the purpose of adding in the session id?
3. :ship: Summarize the injection payload used based on the logs, and breifly discuss the purpose. 


### XSS Security Report

- Install [PwnXSS](https://github.com/pwn0sec/PwnXSS) (git clone or download & unzip their zip/tar.gz file)
- Manually start your application
- Inside the pwnxss folder, scan your web application by `python pwnxss.py -u http://127.0.0.1:8081/`
- Save the log for use later.
- Manually login your website with a valid user account. 
- Check the your session id (let's refer it by `your_session_id`) in the cookie through the request headers of the index page (LocalHost or 127.0.0.1) in the browser. [How?](https://www.google.com/search?q=chrome+how+to+check+request+header&oq=chrome+how+to+check+request+header)
- Scan your website again by using `python pwnxss.py -u http://127.0.0.1:8081/ --cookie='{"session":"your_session_id"}'` here `your_session_id` is the one you obtained from the last step.


Now you have all the logs. Let's compile a scanning report by filling a table following this format, then answer the questions below.

|      | Route/URL                      | Parameter | XSS successful? |
|:----:|--------------------------------|:---------:|:--------------------------:|
| Scan | http://127.0.0.1:8081/register |   password |             NO             | 
|      |                                |           |                            |  
|      |                                |           |                            |   

#### :book: Questions:

1. :ship: We did two rounds of scanning. Why the results are different? What is the purpose of adding in the session id?
1. :ship: Are all the possible XSS (script injection) links/routes covered in the table above? (think about any links that will render user inputs, such as URL paramer, cookies, flask flash calls). If not, are those link/pages vulnerable to XSS?


