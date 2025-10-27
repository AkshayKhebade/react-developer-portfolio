pipeline {
    agent any

    tools {
        nodejs "Node16"
    }

    stages {
       stage('Clone Repository') {
          steps {
             git branch: 'main', url: 'https://github.com/AkshayKhebade/react-developer-portfolio.git'
          }
      }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build React App') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Deploy to Nginx') {
            steps {
                sh '''
                sudo rm -rf /var/www/html/*
                sudo cp -r build/* /var/www/html/
                sudo systemctl restart nginx
                '''
            }
        }
    }
}
