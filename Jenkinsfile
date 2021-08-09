pipeline {
    agent any
    stages {
        stage('Git-CheckOut') {
            steps {
                echo "Checking Out from Git repo";
            }            
        }
        stage('Build') {
            steps {
                echo "Building the check-out project";
                sh '${gitpath}/Build.sh'
            }            
        }
        stage('Unit-Test') {
            steps {
                echo "Performing Junit Test...";
                sh '${gitpath}/Unit.sh'
            }            
        }
        stage('Quality-Gate') {
            steps {
                echo "Varifying the Quality Gate";
                sh '${gitpath}/Quality.sh'
            }            
        }
        stage('Deploy') {
            steps {
                echo "Deploying to Stage";
                sh '${gitpath}/Deploy.sh'
            }            
        }
    }
    post {
        always {
            echo "This will urn always";
        }
        success {
            echo "this runs at success";
        }
        failure {
            echo "this run when job fails";
        }
        unstable {
            echo "This runs olny when the run is marked unstable ";
        }
        changed {
            echo "This run when there is change in the state from success to failure or visa versa";
        }
    }    
}
