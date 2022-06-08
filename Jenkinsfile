pipeline{
    agent any
    stages{
        stage('version-control'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github-id', url: 'https://github.com/Engineering-Operations/parallel-multib-pipeline.git']]])
            }
        }
    }
    stages{
        stage('parallel-job'){
            parallel{
                stage('syscheck'){
                steps{
                    echo 'This is to check for operating system statistics'
                    sh 'lscpu'
                }
                }
                stage('jenkins-stat'){
                    steps{
                        echo 'This is to check the current status of jenkins'
                        sh 'sudo systemctl status jenkins'
                    }
                }
            }
        stage('parallel-job2'){
            parallel{
               stage('mem-stat'){
                    steps{
                        echo 'This is to check disk free space'
                        sh 'df -h'
                    }
               }
            }   
        }
        stage('code-deploy'){
            steps{
                echo 'This is to deploy the code'
            }
        }
    }
}