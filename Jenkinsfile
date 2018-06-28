pipeline {
/* A declarative Pipeline */
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        	post {
            	success {
                	echo 'Now Archiving...'
                	archiveArtifacts artifacts: '**/target/*.war'
            	}
        	}
        }
        stage('Deploy to Staging'){
            steps {
                build job:'deploy-to-staging'
            }
        }

        stage('Deploy to Prodcution'){
            steps {
                timeout(time:5, unit: 'DAYS'){
                    input message: 'Approve PROD Deployment?'
                    /* input message: 'Approve PROD Deployment?', submitter: grp_approver or user
                     */
                }

                build job: 'deploy-to-prod'
            }
            post {
                success {
                    echo 'Code deployed to PROD'
                }
                failure {
                    echo 'Deployment failed'
                }
            }
        }
        
    }
}