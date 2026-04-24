@Library('shared') _
pipeline{
    agent{label 'vinod'}
    stages{
        stage ('hello'){
            steps{
                script{
                    hello()
                }
            }
        }
        stage('code'){
            steps{
                script{
               clone ('https://github.com/Raman-2025/django-notes-app.git', 'main')
                }
            }
        }
        stage('build'){
            steps{
                script{
                    docker_build('notes-app','latest',"raman20260"  )
                }
            }
        }
        stage('push to dockerhub'){
            steps {
                script{
                    docker_push('notes-app','latest','raman20260')
                }
            }
        }
        stage('deploy'){
            steps{
                echo 'this is deploying the code'
                sh 'docker compose down && docker compose up -d '
            } 
        }       
    }
