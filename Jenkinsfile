pipeline {
    agent any
 
    stages {
        stage('Clone') {
            steps {
               git branch: 'main', credentialsId: 'AMDN', url: 'https://github.com/meghavathveeresh/DevVMS.git'            }
        }
          stage('Build') {
            steps {
               bat 'mvn clean install'
            }
        }
         
          stage('Generate Artifacts') {
            steps {
               archiveArtifacts artifacts: 'target/*.war', followSymlinks: false
            }
        }
		stage('deploy') {
            steps {
            deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'AMDN', path: '', url: 'http://localhost:8080/')], contextPath: 'Maha Dev Kumar', war: 'target/*.war'
            }
        }
    }
}
