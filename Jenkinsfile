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
              branch 'master';
              branch 'development';
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
        branch 'development';
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
  }
}
