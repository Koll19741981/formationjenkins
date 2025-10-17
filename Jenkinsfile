pipeline {
    agent any
    environment {
     URL_GIT = 'https://github.com/Koll19741981/formationjenkins.git'
     CREDENTIALS_ID = 'Koll19741981-to-use'
}
    stages {
        stage('build') {
            steps {
                echo 'cloner le repertoire' 
               // git branch: 'master', url: 'https://github.com/Koll19741981/read-files.git'
             checkout([
                $class: 'GitSCM',
                branches: [[name: '*/main']],
                userRemoteConfigs: [[
                    //url: 'https://github.com/Koll19741981/formationjenkins.git',
                    //credentialsId: 'Koll19741981-to-use'
                    url: "${URL_GIT}",
                    credentialsId: "${CREDENTIALS_ID}"
                    

                ]]
              ])
              echo  " Cloner le projet"
              sh "printenv"
            }
        }
        
        
         stage('test') {
            steps {
                sh 'ls -al'
              //  sh 'cat server.csv'
                //def path= Paths.get("server.csv")
               // script{

                    // def lines = readFile("server.csv").split("\n")
                   //  lines.eachWithIndex{ line, index -> echo " ${line}"
                   //  }
               // }
               
                
            }
        }
        
        
        stage('deploy') {
            steps {
                echo 'connect au serveur'
                echo 'dowload configuration'
                 echo 'deploy project'
            }
        }
    }
}