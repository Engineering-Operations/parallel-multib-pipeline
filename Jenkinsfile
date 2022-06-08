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
            }
        } 
    }
}