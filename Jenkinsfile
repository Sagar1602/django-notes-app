@Library("Shared") _
pipeline{
    agent {label "Dev"}
    stages{
        stage("hello"){
            steps{
                hello()
            }
        }
        stage("Code"){
           steps{
               script{
             clone("https://github.com/Sagar1602/django-notes-app.git" ,"main")
           } }
        }
        stage("Build"){
            steps{
                script{
                docker_build("sagar1602", "node-app", "latest")
            }
                
            }
        }
        stage("Test"){
            steps{
                echo "in this step the code is tested for the code quality "
            }
            
        }
        stage("Push to dockerhub"){
            steps{
                script{
                    docker_push("sagar1602", "node-app", "latest")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "in this step the code is to host the app on the server"
                sh "docker compose down && docker compose up -d"
                
            }
            
        }
    }
}
