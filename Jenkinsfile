pipeline {
    agent {
        dockerfile {
        args '''
                -v /root/.m2:/root/.m2
                --network host
      	'''
        }
    }          
  
  stages {
  	stage('vault testing'){
  		steps{
  			withCredentials([
                string(credentialsId:'vault-token', variable: 'VAULT_INIT_TOKEN')
            ]) {
                ssh "${VAULT_INIT_TOKEN}"   
                sh 'cat ~/output.txt'
                sh 'rm ~/output.txt'
            }
  		}
  	}

  }
}