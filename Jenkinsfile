node('php'){
    stage('Clean'){
        deleteDir()
        sh 'ls -la'
    }
    
    stage('Fetch') {
        checkout scm
    }
    
    stage('Build App'){
        sh 'composer install --no-scripts --prefer-dist --no-dev --ignore-platform-reqs'
    }
    
    stage('Docker Build') {
        sh 'docker build -t diegolirio/laravel:$BUILD_NUMBER .'
    }
    
    stage('Docker Ship') {
        sh 'docker push diegolirio/laravel:$BUILD_NUMBER'
        sh 'docker rmi -f diegolirio/laravel:$BUILD_NUMBER'
    }
}
