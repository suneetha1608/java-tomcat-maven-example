pipeline {
    agent any
    stages {
        stage ('Build Jenkins Servlet Project') {
            steps {
                //For windows machine 
               bat  'mvn clean package'

                //For Mac & Linux machine
               // sh  'mvn clean package'
            }
            post{
                success{
                    echo 'Now Archiving ....'

                    archiveArtifacts artifacts : '**/*.war'
                }
            }
        }
      stage ('Deploy Build in Staging Area'){
            steps{

                build job : 'Deploy Artifact on Server Pipeline'

            }
        }
    stage ('Deploy to Production'){
            steps{
                timeout (time: 5, unit:'DAYS'){
                    input message: 'Approve PRODUCTION Deployment?'
                }
                
                build job : 'Deploy To Production-Pipeline'
            }

            post{
                success{
                    echo 'Deployment on PRODUCTION is Successful'
                }

                failure{
                    echo 'Deployement Failure on PRODUCTION'
                }
            }
        }        
        
     }
  }      