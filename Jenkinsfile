pipeline {

    agent any
    stages{
        
        stage('Test') {

            steps{
                echo 'Start testing'
                dir('Grupy/Grupa04/KM305193/Lab07/Docker'){
                    sh '~/docker-compose up -d test-agent'
                }
            }
        }
    }


    post {

        success {
            emailext attachLog: true, 
                body: "Test notification: ${currentBuild.currentResult}: Job ${env.JOB_NAME}, More informations in attachment", 
                recipientProviders: [developers()], 
                subject: 'Test positive', 
                to: 'kmat962@gmail.com'
        }

        failure {
            emailext attachLog: true, 
                body: "Test notification: ${currentBuild.currentResult}: Job ${env.JOB_NAME}, More informations in attachment", 
                recipientProviders: [developers()], 
                subject: 'Test failure', 
                to: 'kmat962@gmail.com'
        }
    }
}
