pipline {
    agent any
    tools {
        jdk 'jdk8'
        maven 'maven'
    }
        stages {
            stage ('Build')
              steps {
                  sh 'mvn clean package checkstyle:checkstyle'
              }
              post {
                  success {
                      echo "Archive Artifact"
                      archiveArtifacts '**/*.war'
                      echo "Publish Unit Result"
                      checkstyle canComputeNew: false, defaultEncoding: '', healthy: '', pattern: '**/target/surefire-reports/*.xml', unHealthy: ''
                    }
              }
        }
}