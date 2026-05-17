@Library("Shared") _
pipeline{
    agent { label "jenkins-slave" }
    triggers{
        githubPush()
    }
    stages{
        stage('Code'){
            steps{
                script{
                    git_clone("https://github.com/Syeeda-Zooni/django-notes-app-jenkins.git","main")
                }
            }
        }
        stage('Build'){
            steps{
                script{
                    code_build("zoonidevops","notes-app","latest")
                }
            }
        }
        stage('Push to docker hub'){
            steps{
                script{
                    docker_push("notes-app","latest")
                }
                    }
            }
        stage('Deploy'){
            steps{
                script{
                    docker_compose()
                }
            }
        }
    }
}
