
// pipeline {
//     agent any
//     stages {
//         stage('Build') {
//             steps {
//                 echo "start building"
//             }
//         }
//         stage('Test') {
//             steps {
//                 echo "start testing"
//             }
//         }
//         stage('Deploy') {
//             steps {
//                 echo "start deploying"
//             }
//         }
//     }
// }

pipeline {
    agent {
        node{
            label 'AGENT-1'
        }
    }
    stages {
        stage('Build') {
            steps {
               echo "start building"
            }
        }
        stage('Test') {
            steps {
                echo "start testing"
            }
        }
        stage('Deploy') {
            steps {
                echo "start deploying"
            }
        }
    }
    post{
        always{
            echo "I will always say hello again...to you"
            cleanWs()
        }
        success{
            echo "I will run if success"
        }
        failure{
            echo "i will run if failure"
        }
    }
}

