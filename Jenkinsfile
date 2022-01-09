pipeline {
    agent any
    
    parameters {
        choice(name: 'PROJECT', choices: ['TATA', 'BATA'], description: 'Select Project name')
        choice(name: 'ENV', choices: ['PROD', 'DR', 'DEV', 'QA'], description: 'Select environment')
        string(name: 'COUNT', defaultValue: '1', description: 'Select number of EC2 instance required')
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/prasadbavkar/provisioning.git'
            }
        }
        stage('Build') {
            steps {
                sh "ansible-playbook createec2.yml -e PROJECT=$PROJECT -e ENV=$ENV -e COUNT=$COUNT"
            }
        }
    }
}
