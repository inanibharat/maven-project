pipeline {
    agent any
    tools {
        jdk 'JDK8'
        maven 'Maven'
    }
        stages {
            stage ('Build') {
              steps {
                  sh 'mvn clean package checkstyle:checkstyle'
              }
              post {
                  success {
                      echo "Archive Artifact"
                      archiveArtifacts '**/*.war'
                      echo "Publish Unit Result"
                      junit '**/target/surefire-reports/*.xml'
                      checkstyle canComputeNew: false, defaultEncoding: '', healthy: '', pattern: '', unHealthy: ''
                      
                    }
               }
            }
        }
}