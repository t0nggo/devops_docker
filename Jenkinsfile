pipeline {
    agent none
    environment {
        imageName = 'tongclubza/my_web'
        port = 80
    }
    
    stages {
       stage('Package') { 
          agent {label 'mgr1'}
          steps {
              sh "docker --version"
              sh "docker build -t ${imageName} ."
            withCredentials(
                [usernamePassword(credentialsId: 'docker_hub', 
                passwordVariable: 'dockerHubPassword', 
                usernameVariable: 'dockerHubUser')]) {
              sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
              sh "docker push ${imageName}"
            }
          }
       }
 
       stage('Deploy') { 
          agent {label 'mgr1'}
          steps {
           sh "echo h4 testes"
           sh "echo Test Up load"
           sh "echo Test Up loads"
          }
       }
    }
}