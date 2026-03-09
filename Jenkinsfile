@Library("Shared@dev") _
pipeline{
    agent {label "Harshal1122"} 
    
    
    stages{
        
        stage("hello"){
            steps{
                script{
                    Hello()
                }
            }
        }
        stage("Code"){
            steps{
                script{
                  clone("https://github.com/HarShal2233/django-notes-app.git","dev")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                    DockerBuild("notes-app","latest","harshal2op")
                }
            }
        }
        stage("test"){
            steps{
                echo "Testing the Code"
            }
        }
        stage("Push To DockerHub"){
            steps{
                script{
                    DockerPush("notes-app","latest","harshal2op")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "Deploying the Code"
                sh "docker compose down && docker compose up -d"
            }
        }
    }
}
