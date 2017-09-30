# Jenkins git-flow

Jenkins configuration to illustrate [git-flow](http://nvie.com/posts/a-successful-git-branching-model/)
using multiple git repositories, viz. [frontend-app](https://github.com/NayabSiddiqui/gitflow-frontend-app)
and [backend-api](https://github.com/NayabSiddiqui/gitflow-backend-api)

## Setup

- Start up the Jenkins [docker]() container by issuing the following command
    ```
    docker-compose up
    ```
    
    Alternatively, you can force building up of images by issuing
    ```
    docker-compose up --build
    ```
    
    This should have started a local jenkins server. Verify by visiting `http://localhost:9090/`
    Also note the two container that are created now using two different images that
    we just built. The two images in discussion would be `jenkinsgitflow_jenkins-master`
    and `jenkinsgitflow_jenkins-data`
    
- Login to jenkins
    On the first time startup, Jenkins is going to ask for the initial admin password.
    You can get that as follows:
    
    To get the `container-id` to be used in the above command, use the following:
    ```
    docker ps
    
    # This should result in listing of container, e.g.,
    # CONTAINER ID        IMAGE                           COMMAND                  CREATED             STATUS              PORTS                                              NAMES
    # 116dac89a7aa        jenkinsgitflow_jenkins-master   "/bin/tini -- /usr..."   8 hours ago         Up 8 minutes        0.0.0.0:50000->50000/tcp, 0.0.0.0:9090->8080/tcp   jenkinsgitflow_jenkins-master_1
    ```
    
    Copy the above obtained CONTAINER_ID, in this case it is `116dac89a7aa`
    
    You can get that by issuing following command:
    ```
    docker exec `container-id` cat /var/jenkins_home/secrets/initialAdminPassword
    ```
    Copy the string displayed in the terminal and this is the password that you need :)
    
