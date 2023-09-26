pipeline{
agent any
  stages{
    stage("checkout-code"){
    steps {
        git branch: 'development', credentialsId: 'e11708a0-d94b-4c7b-8935-41cb820523e9', url: 'https://github.com/surajjp2508/DevopsCICD.git'
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
  }
}
