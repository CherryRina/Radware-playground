pipeline {
    agent any // Runs the pipeline on any available agent

    triggers { // start the pipeline automaticall
        cron('H */4 * * *') // This cron expression means "every 4 hours"
    }

    stages { // define the sequence of tasks in a pipeline

        stage('Checkout') { // Clones the Python script repository
            steps {
                git branch: 'master', url: 'https://github.com/CherryRina/Radware-playground.git'
            }
        }

        stage('Execute Python Script') { // Executes the Python script
            steps {
                sh 'cd task-02-service-manager && python3 2-service_managment.py'
            }
        }

    }

    post {
        always {
            echo 'Pipeline run complete.'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
