pipeline{
agent any
  stages{
    stage("checkout-code"){
    steps {
        checkout scm
    }
   }
   stage("Code-Check") {
        when {
          not {
            anyOf {
              branch 'master'
              branch 'development'
            }
          }
        }
      steps {
        sh 'mvn clean compile'
        echo "Code Compile Completed"
      }
    }
    stage("Run Test cases") {
      when {
        branch 'development'
      }
      steps {
        sh 'mvn clean test'
      }
    }
    stage("Code-Build") {
      when {
        branch 'master'
      }
      steps {
        sh 'mvn clean package'
        echo "Build Completed"
      }
      
    }
    stage("Build-Deploy") {
      when {
        branch 'master'
      }
      steps {
        deploy adapters: [tomcat9(credentialsId: 'Tomcat', path: '', url: 'http://172.17.0.3:8090/')], contextPath: null, onFailure: false, war: '**/*.war'
        echo "Build Deployed to Tomcat Server"
      }
    }
  }
}
