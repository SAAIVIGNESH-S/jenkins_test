pipeline {
  agent any

  triggers {
    pollSCM '* * * * *'
  }

  stages {
    stage('Checkout') {
      steps {
        script {
          checkout scm
        }
      }
    }

    stage('Install Dependencies') {
      steps {
        script {
          // Use the package manager for your project (npm or yarn)
          sh 'npm install'
        }
      }
    }

    stage('Lint and Format') {
      steps {
        script {
          sh 'npm install -g eslint prettier'
          sh 'eslint .'
          sh 'prettier --check .'
        }
      }
    }

    // stage('Build') {
    //   steps {
    //     script {
    //       // Add build commands here
    //       // e.g., npm run build
    //     }
    //   }
    // }
  }

//   post {
//     always {
//       // Cleanup steps, notifications, etc.
//     }
//   }
}