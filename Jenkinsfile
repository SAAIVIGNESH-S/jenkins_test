// pipeline {
//     agent { 
//         node {
//             label 'docker-agent-python'
//             }
//       }
//     triggers {
//         pollSCM '* * * * *'
//     }
//     stages {
//         stage('Build') {
//             steps {
//                 echo "Building.."
//                 sh '''
//                 cd myapp
//                 pip install -r requirements.txt
//                 '''
//             }
//         }
//         stage('Test') {
//             steps {
//                 echo "Testing.."
//                 sh '''
//                 cd myapp
//                 python3 hello.py
//                 python3 hello.py --name=Brad
//                 '''
//             }
//         }
//         stage('Deliver') {
//             steps {
//                 echo 'Deliver....'
//                 sh '''
//                 echo "doing delivery stuff.."
//                 '''
//             }
//         }
//     }
// }


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

    stage('Build') {
      steps {
        script {
          // Add build commands here
          // e.g., npm run build
        }
      }
    }
  }

  post {
    always {
      // Cleanup steps, notifications, etc.
    }
  }
}