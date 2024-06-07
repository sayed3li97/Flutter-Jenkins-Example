pipeline {
    agent any

    environment {
        FLUTTER_HOME = "/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games:/home/alkamelsayedali/flutter/bin"
        PATH = "$FLUTTER_HOME/bin:$PATH"
        flutter = "/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games:/home/alkamelsayedali/flutter/bin"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/sayed3li97/Flutter-Jenkins-Example.git'
            }
        }

        stage('Setup Flutter') {
            steps {
                sh '{env.SOURCE}; flutter doctor'
            }
        }

        stage('Get Dependencies') {
            steps {
                sh 'flutter pub get'
            }
        }

        stage('Build') {
            steps {
                sh 'flutter build web'
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'build/web/**', allowEmptyArchive: true
            }
        }

//         stage('Deploy') {
//             steps {
//                 // Add your deployment steps here (e.g., copy to a server, deploy to Firebase, etc.)
//             }
//         }
    }

//     post {
//         always {
//             cleanWs()
//         }
//     }
}
