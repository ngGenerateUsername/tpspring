pipeline{
  agent any
  tools{
    maven 'Maven'
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
        dir("tpspring"){
          sh "mvn clean install"
          sh "sudo docker build -t tpspring ."
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
