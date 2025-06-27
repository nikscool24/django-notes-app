@Library("Shared") _
pipeline{
    agent { label "Agent2"}
    
    stages{
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
            steps{
                script{
                clone("https://github.com/nikscool24/django-notes-app.git","main")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                docker_build("notes-app","latest","nikscool24")
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("notes-app","latest","nikscool24")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is Deploying the code"
                sh "docker compose down && docker compose up -d"
            }
        }
    }
}
