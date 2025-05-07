pipeline{
    agent any
    stages{
        stage('checkout'){
            steps{
                git url: 'https://github.com/Aryangupta6612/nodejscicd.git', branch: 'master'
            }
        }
        stage('Build and Deploy'){
            sh '''
                docker compose down || true
                docker compose up -d --build
            '''
        }
    }
    post{
        always{
            sh 'docker container prune -f||true'
            sh 'docker image prunt -f||true'
        }
        success{
            echo "Build and Deploy successful"
        }
        fail{
            echo "Build and Deploy fail"
        }
    }
}