pipeline{
agent any
  stages{
    stage('Git Checkout'){
      steps{
        git branch: 'master', changelog: false, credentialsId: 'e11708a0-d94b-4c7b-8935-41cb820523e9', poll: false, url: 'https://github.com/surajjp2508/DevopsCICD.git'
    }
    }
    stage('Code-Compile'){
      steps{
        sh 'mvn clean compile'
        echo "Compile Completed"
      }
    }
    stage('Code-Build'){
      steps{
        sh 'mvn clean package'
        echo "Build Completed"
      }
    }
}
}
