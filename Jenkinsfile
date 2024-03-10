pipeline{
  agent any
  stages{
    stage ('Build'){
      steps{
        sh 'mvn clean install'
        echo 'Build Stage Successful'
      }
    }
    stage ('Test'){
      steps{
        sh 'mvn test'
        echo 'Test Stage Successful'
        post{
          always{
            junit 'target/surefire-reports/*.xml'
          }
        }
      }
    }
    stage ('Deploy'){
      steps{
        sh 'mvn deploy'
        echo 'Deploy Stage Successful'
      }
    }
    stage ('Test Application'){
      steps{
        sh 'npm test'
      }
    }
  }
  post{
    failure{
      echo 'Pipeline Failed'
    }
  }
}
