@Library("Shared") _
pipeline{
    agent {label "kaustav"}
    
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
                   clone("https://github.com/kaustavGitH/django-notes-app.git/","main")
               }
           } 
        }
        stage("Build"){
            steps{
                script{
                    dockerBuild("notes-app","latest","kaustavsdet")
                }
           }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    dockerPush("notes-app","latest","kaustavsdet")
                }
           }
        }
        stage("Deploy"){
            steps{
               echo "This is deploying the code"
               sh "docker compose up -d"
           }
        }
    }
}
