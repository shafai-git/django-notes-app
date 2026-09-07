@Library("Shared") _
pipeline {
    agent { label "rizvi" }

    stages {
        
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        
        stage("Code") {
            steps {
                script{
                clone("https://github.com/shafai-git/django-notes-app.git", "dev")
                }
            }
        }

        stage("Build") {
            steps {
                script{
                docker_build("notes-app" , "latest" , "shafai-git")
                }
            }
        }

        stage("Test") {
            steps {
                echo "This is testing the codee"
            }
        }

        stage("Push to Docker Hub") {
            steps {
                script{
                    docker_push("notes-app", "latest" , "shafai-git")
                }
            }
        }

        stage("Deploy") {
            steps {
                script{
                docker_compose()
                }
            }
        }
    }
}
