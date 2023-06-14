pipeline {
  agent {label 'linux'}

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub_id')
	}

  stages {
    stage('Checkout Code') {
      steps {
        git(url: 'https://github.com/theuzumaki1111/curriculum-app', branch: 'main')
      }
    }

    stage('Log') {
      steps {
        sh 'ls -la'
      }
    }

    stage('Build') {
      steps {
        sh 'docker build -f Dockerfile -t mychatgpt:latest .'
      }
    }

    stage('Log into Dockerhub') {
      steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
    }

    stage('Push') {
      steps {
        sh 'docker push mychatgpt:latest'
      }
    }

  }
}