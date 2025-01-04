pipeline {
    agent any
    stages {
        stage('Checkout two versions') {
            steps {
                script {
                    // Checkout the first version (e.g., main branch)
                    dir('x64') {
                        checkout([$class: 'GitSCM', branches: [[name: 'master']],
                                  userRemoteConfigs: [[url: 'https://github.com/kmikhailv/two_repos.git']]])
                    }

                    // Checkout the second version (e.g., specific tag)
                    dir('arm') {
                        checkout([$class: 'GitSCM', branches: [[name: 'master']],
                                  userRemoteConfigs: [[url: 'https://github.com/kmikhailv/two_repos.git']]])
                    }
                }
            }
        }
        stage('Build both versions') {
            steps {
                script {
                    dir('x64') {
                        sh 'pwd; touch x64.txt'
                    }
                    dir('arm') {
                        sh 'pwd; touch arm.txt'
                    }
                    sh 'ls -lR .'
                }
            }
        }
    }
}
