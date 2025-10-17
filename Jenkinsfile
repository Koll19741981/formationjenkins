pipeline {
    agent any
    environment {
     URL_GIT = 'https://github.com/Koll19741981/formationjenkins.git'
     CREDENTIALS_ID = 'Koll19741981-to-use'
}
    parameters {
              string( name: "version", description:" Environement sur  lequel  je deploye"    )
              choice( name: "environnement",  choices: [ "test","prepord","prod"],description:" Environement "    )
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
        
        
        //stage('deploy') {
            //steps {
               // sh 'chmod +x mvnw'
               // sh './mvnw clean package spring-boot:repackage -Dmaven.test.skip=true'
               //echo "   Environnement ${params.environment}"
               

               
            //}

           stage('Déploiement sur serveur distant') {
            steps {
                echo "Environnement ${params.environment}"
                sshPublisher(
                    publishers: [
                        sshPublisherDesc(
                            configName: 'training-server',  // correspond au Nom de la configuration
                            transfers: [
                                sshTransfer(
                                    sourceFiles: 'target/*.jar',
                                    remoteDirectory: '/',
                                    execCommand: 'ls -al'
                                )
                            ]
                        )
                    ]
                )
            }
        }

        }
    
}