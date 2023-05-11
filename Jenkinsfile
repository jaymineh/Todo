pipeline {
    agent any

  stages {

     stage("Initial cleanup") {
          steps {
            dir("${WORKSPACE}") {
              deleteDir()
            }
          }
        }

    stage('Checkout SCM') {
      steps {
            git branch: 'main', url: 'https://github.com/jaymineh/todo.git'
      }
    }

    stage('Prepare Dependencies') {
      steps {
             sh 'cat .env.sample'
             sh 'mv .env.sample .env'
             sh 'composer install'
             sh 'php7.4 artisan migrate'
             sh 'php7.4 artisan db:seed'
             sh 'php7.4 artisan key:generate'
      }
    }
  }
}
