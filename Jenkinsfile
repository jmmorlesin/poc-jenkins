pipeline {
    agent any
    stages {
        stage("Clean") {
            steps {
                sh 'echo "Clean Step 1"'
                sh 'echo "Clean Step 2"'
            }
        }
        stage('Build') {
            steps {
                sh 'echo "Hello World"'
                sh '''
                    echo "Multiline shell steps works too"
                    ls -lah
                '''
            }
        }
        stage('Parallel Block') {
            parallel {
                stage('Parallel 1') {
                    agent any
                    steps {
                        sh 'echo "Parallel Step 1"'
                        sh 'echo "Executor number: $EXECUTOR_NUMBER"'
                        sh 'sleep 20s'
                    }
                    post {
                        always {
                            sh 'echo "Ending Parallel Step 1"'
                        }
                    }
                }
                stage('Parallel 2') {
                    agent any
                    steps {
                        sh 'echo "Parallel Step 2"'
                        sh 'echo "Executor number: $EXECUTOR_NUMBER"'
                        sh 'sleep 20s'
                    }
                    post {
                        always {
                            sh 'echo "Ending Parallel Step 2"'
                        }
                    }
                }
            }
        }
        stage("Finish") {
            steps {
                sh 'echo "Finish"'
            }
        }
    }
}
/*
pipeline {
    agent { docker { image 'python:3.5.1' } }
    stages {
        stage('build') {
            steps {
                sh 'python --version'
            }
        }
    }
}
*/
