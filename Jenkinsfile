pipeline {
    agent { label 'docker' }
    triggers { pollSCM('* 23 * * 1-5') }
    stages {
        stage('VCS'){
            steps {
                git url: 'https://github.com/practicepurpouse/StudentCoursesRestAPI.git',
                    branch: 'sprint_1_release'
            }
        }
        stage('Build') {
            steps {
                sh 'docker image build -t sureshkola/spc:latest .'
            }
        }
        stage('Scan & Push') {
            steps {
                sh 'echo docker scan sureshkola/spc:latest'
                sh 'docker image push sureshkola/spc:latest'
            }
        }
    }
}