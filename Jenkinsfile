pipeline {
    agent {
        dockerfile {

        }
    }          
  
  stages {
      stage('Sonar analysis'){
          steps{
              withSonarQubeEnv('sonar'){
                  sh 'mvn clean package sonar:sonar'
              }
          }
      }
      stage('Quality Gate'){
          steps{
              timeout(time: 1, unit: 'HOURS'){
                  waitForQualityGate abortPipeline: true
              }
          }
      }

      stage('Did it pass?'){
          steps{
              sh 'echo yes'
          }
      }

  }	
}

  
