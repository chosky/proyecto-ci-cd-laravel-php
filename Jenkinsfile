pipeline {
    agent any
    stages {
        stage("Build") {
            steps {

                sh 'php --version'
                sh 'composer install'
                sh 'composer --version'
                sh 'cp .env.example .env'
                sh 'echo DB_HOST=127.0.0.1 >> .env'
                sh 'echo DB_USERNAME=root >> .env'
                sh 'echo DB_DATABASE=laravel >> .env'
                sh 'echo DB_PASSWORD= >> .env'
                sh 'php artisan key:generate'
                sh 'cp .env .env.testing'
                //sh 'php artisan migrate'
            }
        }
        stage("Unit test") {
            steps {
                sh 'php artisan test'
            }
        }
        stage("Code coverage") {
            steps {
                sh "echo 'SonarQube'"
            }
        }
        stage("Static Analysis Security Testing") {
            steps {
                sh "echo 'SonarQube'"
            }
        }
        stage("Software Composition Analysis") {
            steps {
                sh "echo 'snyk'"
            }
        }
        stage("Dynamic Analysis Security Testing") {
            steps {
                sh "echo 'OwaspZAP'"
            }
        }
        stage("Docker build") {
            steps {
                sh "docker build --tag laravel8cd ."
            }
        }
        stage("Deploy to prod"){
            steps {
                sh "php artisan serve --host=0.0.0.0 --port=80"
            }
        }
   }
}
