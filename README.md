# Two-Tier-application
Using Docker compose 
<br>
step-1 Create a docker-compose.yml file 
<br>
step-2 on terminal: docker compose up (it will run the containers in the foreground to exit press Ctrl+X)
<br>
step-3 docker compose start
<br> 

# Using Jenkins Pipeline  
> script
<br>
pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main' , url:  'https://github.com/SiyaDadheech/Two-Tier-application.git'
            }
        }

        stage('Build Docker Images') {
            steps {
                sh 'docker-compose build'
            }
        }

        stage('Run Containers') {
            steps {
                sh 'docker-compose up -d'
            }
        }
    }
}

#Problem Faced While Creating the project
1. Docker Compose was not installed:

   To install it use command: apt install docker-compose -y
   to verify it: docker-compose --version
   
2. Jenkins did not have permission to access Docker:
   To fix this, add the Jenkins user to the Docker group:  sudo usermod -aG docker jenkins
   restart the jenkins service: systemctl restart jenkins
   


