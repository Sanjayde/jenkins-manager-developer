pipeline {
	
    agent {label 'master'}
    stages {
	      stage ('Checkout') {
            steps {
                  sh 'echo "Hi Sanjay its Checkout Stage"'
                }
            }  
        stage('Approval for Dev') {
            steps {
                script {
		           timeout(time: 10, unit: 'MINUTES') {
                   env.APPROVED_DEV = input message: 'User input required',
                   parameters: [choice(name: 'Deploy?', choices: 'no\nyes', description: 'Choose "yes" if you want to go for DEV')]
		   		}
                       }
            }
        }
	      stage('Dev'){
	          when {
                environment name:'APPROVED_DEV', value: 'yes'
            }
            steps{
                  sh 'echo "Hi Sanjay its DEV STAGE"'
            }
        }
        stage('Approval for UAT') {
            steps {
                script {
	           	   timeout(time: 10, unit: 'MINUTES') {
                   env.APPROVED_UAT = input message: 'User input required',
                   parameters: [choice(name: 'Deploy?', choices: 'no\nyes', description: 'Choose "yes" if you want to go for UAT')]
		   		}
                       }
            }
        }
	      stage('UAT'){
	          when {
                environment name:'APPROVED_UAT', value: 'yes'
            }
            steps{
                  sh 'echo "Hi Sanjay its UAT STAGE"'
            }
        }
        stage('Approval for PROD') {
            steps {
                script {
	           	   timeout(time: 10, unit: 'MINUTES') {
                   env.APPROVED_PROD = input message: 'User input required',
                   parameters: [choice(name: 'Deploy?', choices: 'no\nyes', description: 'Choose "yes" if you want to go for PROD')]
		   		}
                       }
            }
        }
	      stage('PROD'){
	          when {
                environment name:'APPROVED_PROD', value: 'yes'
            }
            steps{
                  sh 'echo "Hi Sanjay its PROD STAGE"'
            }
        }
  }
    post {
    success {
        sh 'echo "Pipeline Works"'
    }
    failure {
        script {
            sh 'echo "Pipeline Failed"'
        }
    }
    }
}
