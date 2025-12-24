
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
    // there is fine 
    agent {
        node{
            label 'AGENT-1'
        }
    }
    environment{
        COURSE = "jenkins"
    }
    options{
        timeout(time: 10,unit: 'MINUTES')
        disableConcurrentBuilds()
    }
        parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'DEPLOY', defaultValue: false, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
    stages {
        //this is build event 
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
                        sleep 10
                        env
                    """
                }
            }
        }
        stage('Deploy') {
            // input {
            //     message "Should we continue?"
            //     ok "Yes, we should."
            //     submitter "alice,bob"
            //     parameters {
            //         string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
            //     }
            // }
            when{
                expression { "$params.DEPLOY" == "true" }
            }
            steps {
                echo "start deploying"
            }
        }
        stage('parameters') {
            steps {
                echo "Hello ${params.PERSON}"

                echo "Biography: ${params.BIOGRAPHY}"

                echo "Toggle: ${params.TOGGLE}"

                echo "Choice: ${params.CHOICE}"

                echo "Password: ${params.PASSWORD}"
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
        aborted{
            echo 'pipeline is aborte'
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
