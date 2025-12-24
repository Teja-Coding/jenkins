
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
    environment{
        COURSE = "jenkins"
    }
    stages {
        stage('Build') {
            steps {
               echo "start building"
               echo " $COURSE "
            }
        }
        stage('Test') {
            steps {
                script{
                    sh """ 
                        echo "testing from here"
                        echo "here is learing course $COURSE"
                        env
                    """
                }
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

// pipeline {
//     agent {
//         node {
//             label 'AGENT-1'
//         }
//     }

//     stages {
//         stage('Build') {
//             steps {
//                 // Scripted part (runtime logic)
//                 script {
//                     sh 'echo "building"'
//                 }
//             }
//         }

//         stage('Test') {
//             steps {
//                 echo "start testing"
//             }
//         }

//         stage('Deploy') {
//             steps {
//                 script {
//                     echo "start deploying"
//                 }
//             }
//         }
//     }

//     post {
//         always {
//             echo "I will always say hello again...to you"
//             cleanWs()
//         }
//         success {
//             echo "I will run if success"
//         }
//         failure {
//             echo "I will run if failure"
//         }
//     }
// }
