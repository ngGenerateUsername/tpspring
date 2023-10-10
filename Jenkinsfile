pipeline{
  agent any
  tools{
    maven 'maven'
  }
  stages{
    stage ("Clean Up"){
      steps{
        deleteDir()
      }
    }
    stage ("Clone repo"){
      steps{
        sh "git clone https://github.com/ngGenerateUsername/tpspring.git"
      }
    }
    stage ("Generate backend image"){
      steps{
        dir("exp1-spring"){
          sh "mvn clean install"
          sh "docker build -t tpspring"
        }
      }
    }
    stage ("Run docker compose"){
      steps{
        dir("exp-spring"){
          sh "docker compose up -d"
        }
      }
    }
  }
}
