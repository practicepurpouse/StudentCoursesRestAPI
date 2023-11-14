pipeline {
    agent { label 'docker' }
    triggers { pollSCM('* * * * *') }
    stages {
        stage('VCS'){
            steps {
                git url: 'https://github.com/practicepurpouse/StudentCoursesRestAPI.git',
                    branch: 'develop'
            }
        }
        stage('Build') {
            steps {
                sh 'docker image build -t sureshkola/spc:latest .'
            }
        }
        stage('Scan & Push') {
            steps {
                sh 'echo docker scan sureshkola/spc:latest',
                sh 'docker image push sureshkola/spc:latest'
            }
        }
    }
}