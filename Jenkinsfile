pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'build stage'
      }
    }

    stage('Test') {
      parallel {
        stage('smoke') {
          steps {
            echo 'smoke test'
          }
        }

        stage('Integration') {
          steps {
            echo 'Functionnal'
            sh 'mvn -Dtest="com.example.testingweb.integration.**" test'
          }
        }

        stage('Functional') {
          steps {
            echo 'test fonctionnel termine'
            sh 'mvn -Dtest="com.example.testingweb.functional.**" test'
          }
        }

      }
    }

    stage('Deploy') {
      steps {
        input 'Voulez-vous continuer?'
        echo 'deployement demarer'
        sh 'mvn -DskipTests install'
        echo 'deployement termine'
      }
    }

  }
}