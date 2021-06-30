pipeline {
    agent any
    parameters {
        choice(name: 'VERSION', choices: ['1.1.0', '1.2.0', '1.3.0'], description: '')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
    }
    environment {
        TEST_VAR = 'Test content'
    }
    stages {
        stage('Stage1') {
            agent any
            steps {
                echo "Stage 1"
                echo "${TEST_VAR}"
                echo "${JOB_URL}"
            }
        }
        stage('Stage2') {
            agent {
                label 'Agent1'
            }
            steps {
                echo "Stage 2"
            }
        }
        stage('Test') {
            when {
                expression {
                    params.executeTests
                }
            }
            steps {
                echo "Stage Test"
                echo "print version : ${params.VERSION}"
            }
        }
    }
}
