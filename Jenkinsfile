pipeline {
    agent 'linux'any

    stages {
        stage('clone') {
            steps {
                git branch: 'main', url: 'https://github.com/srinfotechbatch2/spring-petclinic.git'
            }
        }
         stage('Build') {
            steps {
                bat 'mvn clean install'
            }
        }
         stage('Test') {
            steps {
                bat 'mvn test'
            }
        }
        
         stage('Tets Results Reports') {
            steps {
				junit 'target/surefire-reports/*.xml'
            }
        }
		stage('published Artifacts') {
            steps {
				archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
            }
        }
		
    }
}
