pipeline{
    agent any
    triggers{
        pollSCM ("* * * * *")
    }
    tools {
        maven "M2_HOME"
        }
        environment{
            registry = "310511/devops-code"
            registryCredential ="dockerUserId"
        }
    stages {
        stage("build"){
          steps{
              sh "mvn clean"
              sh "mvn install"
              sh "mvn package"
              sh "mvn test"
              sleep 10
          }

        }
        stage("test"){
          steps{
              echo "test step"
              sh "mvn test"
             
          }

        }
        stage("deploy"){
          steps{
              script {
                  docker.build registry + ":$BUILD_NUMBER"
              }
          }

        }

    }

}
