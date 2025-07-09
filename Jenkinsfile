pipeline{
    
agent any

stages{
    stage('Clone The Project'){
        steps{
            git branch: 'master', url: 'https://github.com/srinfotechbatch2/onlinebookstore.git'
        }
    }
    
    stage('Build'){
        steps{
             bat 'mvn clean install'
        }
    }
     stage('Test'){
        steps{
             bat 'mvn test'
        }
    }
     stage('Generated the test reports'){
        steps{
             junit 'target/surefire-reports/*.xml'
        }
    }
     stage('published the Artifacts'){
        steps{
            archiveArtifacts artifacts: 'target/*.war', followSymlinks: false
        }
    }
    
    stage('Deploy to Tomcat Server'){
        steps{
            deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tomcatcredential', path: '', url: 'http://localhost:8080')], contextPath: 'SRInfotechOnlinebookStore', war: 'target/*.war'
        }
    }
}
}