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
     }
  }      