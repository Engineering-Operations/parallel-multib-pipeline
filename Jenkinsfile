pipeline{
    agent any
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