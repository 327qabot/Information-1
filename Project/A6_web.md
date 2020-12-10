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


## SQL-Injection Security Report [Optional but Recommended]

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


## XSS Security Report [Optional but Recommended]

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


## SHIP the Container!!

Now let's ship it!! Deploying a web application is not easy. By using docker containers, we can bundle all the dependencies into a single image. Follow the steps below:

1. Insteall and start docker. Think of it as a virtual machine (well on linux it is on the same host but different namespace but you can `treat` it as a virtual machine for now). 
2. Get used to some typical commands:
 - `docker ps` # list running processes and their containers 
 - `docker kill ps_id` # kill a process
 - `docker image list` # list out available images
3. check out [here](https://github.com/CISC-CMPE-327/CI-Python/pull/9/files) to see changes we made in the web application source code. Specifically make sure that you understand why:
   - `qa327/__init__.py `: we added `db_string` variable that is read from the environment. This allow us to use a different database such as MySQL than the original single database file. 
   - `qa327/__main__.py `: we added the `host='0.0.0.0'` to the main function so you can access the web application using all IP addresses on the host rather than just `127.0.0.1`. (for example, your laptop/host also has an IP from the router 192.0.0.1 you can use that to visit your app as well)
   - `requirements.txt` : added `pymysql` library to enable us connecting to a MySQL database
   - `wait-for-it.sh ` : a bash file that will wait for certain port to be open before running some commands. You don't need to understand what is inside. We use this to wait for the MySQL database server is ready before starting our web application in the deployment. 
   - `Dockerfile ` : define what is installed and included in the container for our web application. Basically the `FROM` statement defines the base image, then we just install dependencies and copy the application over the image. We also copy the `wait-for-it.sh ` file there for later use. The `EXPOSE 8081` statement means that the container will expose its port 8081 to the outside of the container. So we can visit the app with our host.
   - `docker-compose.yml `: define all the services (our web app, SQL server, and the database web UI) and all the resources (data storage volumn & network) to be deployed
   - `db_init.sql` : database initialization file for a proper database such as MySQL. (basically we only created a database using this script)
   - `.gitignore` : stop tracking some data files (as well as the data folder for MySQL to be created later). 
4. Apply the chances above to your own project. Please make sure that files are in the right path (e.g. `Dockerfile` is in the same folder as the `qa327` folder). Or you can change the paths in `Dockerfile`. 
5. Register your company/group on dockerhub. We will use it to store the image so you can deploy it anywhere! Then on dockerhub, create a **public** repostiroy (usually it is your application name)
5. Compile your image: `docker build --tag=your_docker_hub_name/your_docker_hub_repo_name:version_info .` For example, `docker build --tag=test_company/app:v1 .`
6. Once done, you will find your image by `docker image list`
7. You can run your web application by  `docker run -p 8081:8081 your_docker_hub_name/your_docker_hub_repo_name:version_info python3 -m qa327`. For example: `docker run -p 8081:8081 test/app:v1 python3 -m qa327`.
   - you can build the image with different versions. If you put the same version, it will just overwrite the original one.
   - when running the container, `-p 8081:8081` means we map the port 8081 of the container to 8081 of the host. `python3 -m qa327` is the command to be run in the container (which starts our application)
8. Publishing your web application container
   - use `docker login` command to login
   - use `docker push your_docker_hub_name/your_docker_hub_repo_name:version_info` to push your image to the hub repository. You should be able to see the image on your docker hub page.

9. Now, anywhere (e.g. your friends machine), you can run your web application with docker by follwoing commands, without worrying about the platform, python versions etc. 
 - `docker pull your_docker_hub_name/your_docker_hub_repo_name:version_info` 
 - `docker run -p 8081:8081 your_docker_hub_name/your_docker_hub_repo_name:version_info python3 -m qa327`


## SHIP the WHOLE SYSTEM

However, we don't stop from a single container deployment. In a lot of situtation, your applicaton (or it is now more like a system) consists of a lot of micro-services and applications. For example, here we have our web application services and we also want a proper database services to serve millions of users. Additionally, we want to add web interface so we can easily manage the database. Now our system consists of these services:
 - `seetgeek-web`: Flask web application (including frontend and backend, in reality people like to further break backend into different independent services)
 - `seetgeek-db` : MySQL database
 - `phpmyadmin`  : Web interface for MySQL
These services are all defined in our `docker-compose.yml` file. 
It also defines some resources:
  - `seetgeek-site` : the network connects everything
  - volumes mounted to the MySQL database instance, including the folder for database data and the database initialization file for MySQL. 
1. The only thing you need to change in the `docker-compose.yml` file is the `image` property of the `seetgeek-web:` service. It should point to your own image i.e. `your_docker_hub_name/your_docker_hub_repo_name:version_info`. 
2. To run the WHOLE system just issue `docker-compose up`. Then everything should start!! You will see a new folder `mysql_data` created for data store. 
  - web app is running at `0.0.0.0:8081` 
  - database web interface is running at `127.0.0.1:8082`. user name `root`, password `root`, server `db`. (all of these are defined in the docker compose file). 


## Evalution Rubic:
- Teamwork (PR practice, build-passing, review, etc.) 2
- Successfully building and publishing a working docker image 4
- A working docker-compose file 4
