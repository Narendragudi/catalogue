pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }
    environment {
        packageVersion = ''
    }

    options {
        timeout(time: 1, unit: 'HOURS')
        disableConcurrentBuilds()
    }

    // parameters {
    //     string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

    //     text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

    //     booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

    //     choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

    //     password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    // }
      //build

    stages {
        stage('Get the version') {
            steps {
                script {
                    def packagejson = readJSON file: 'package.json'
                    packageVersion = packageJson.version
                    echo "application version: $packageversion"
                }
            }
        }

        stage('install dependances') {
            steps {
                sh """
                    npm install
                """
            }

        stage('Build') {
            steps {
                sh """
                   ls -la
                   zip -q -r catalogue.zip ./* -x ".git"*.zip"
                   ls -ltr
                """
            }
        }

        stage('Deploy') {
            steps {
                sh """
                  echo " here i wrote shell script"
                  #sleep 10
                """
            }
       }

       stage('check params') {
        steps{
            sh """
              echo "Hello ${params.PERSON}"

              echo "Biography: ${params.BIOGRAPHY}"

              echo "Toggle: ${params.TOGGLE}"

              echo "Choice: ${params.CHOICE}"

              echo "Password: ${params.PASSWORD}"
            """
        }
       }
   }
    // post-build
   post {
       always {
            echo 'I will always say Hello again'
            deleteDir()
       }
       failure {
            echo 'this runs when pipeline is failed,used generally to send some alrets'
       }
       success {
            echo 'i will say hello when pipe line is success'
       }
   }
}